# Master Plan V2 — Firebase-Backed UPS Field App
## VSS × Zoho CRM × Firebase Sync

---

## 1. Updated Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                    FIELD EMPLOYEE (Mobile)                          │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                    FIELD APP (GitHub Pages)                         │
│                                                                  │
│  ┌─────────────────────────────────────────────────────────────┐ │
│  │  ON APP LOAD:                                               │ │
│  │  1. Instantly read from Firebase → show dealer list         │ │
│  │  2. Background: call Zoho CRM API → fetch all UPS records  │ │
│  │  3. Write Zoho data → Firebase (update existing records)    │ │
│  │  4. Next load is INSTANT (Firebase has all data)           │ │
│  └─────────────────────────────────────────────────────────────┘ │
│                                                                  │
│  Dealer List ──► Tap Card ──► Modal ──► "Open Form" button      │
└────────────────────────────┬────────────────────────────────────┘
                             │
         ┌───────────────────┴────────────────────┐
         │                                        │
         ▼                                        ▼
┌─────────────────────┐               ┌──────────────────────────┐
│ GOOGLE FORM         │               │ ZOHO CRM                 │
│ (pre-filled)        │               │ UPS Module               │
└──────────┬──────────┘               └──────────┬─────────────┘
           │                                     │
           │ n8n PATCH (on form submit)          │ Background sync
           │                                     │ (every app open)
           ▼                                     ▼
┌─────────────────────┐               ┌──────────────────────────┐
│ n8n Workflow        │               │ FIREBASE FIRESTORE        │
│                     │               │                          │
│ 1. Parse form data  │               │ Collection: ups_dealers   │
│ 2. PATCH Zoho CRM  │               │ Doc per dealer (Record ID │
│ 3. Update Firebase │◄─────────────│   is doc ID)             │
└─────────────────────┘               │ Fields: all CRM fields   │
                                      │ + last_sync timestamp    │
                                      └──────────────────────────┘
```

---

## 2. Data Flow — Detailed

### App Load Flow (Every Time):
```
1. User opens app
2. App immediately reads / ups_dealers from Firebase
3. Firebase data renders on screen (FAST — no loading spinner needed)
4. Background: App calls Zoho CRM API
5. For each Zoho record → Firebase setDoc (upsert)
6. Done. Next load = instant from Firebase.
```

### Form Submit Flow:
```
1. User taps "Update Dealer" → Google Form opens (pre-filled)
2. User fills form → submits
3. Form response → Google Sheet (or n8n direct)
4. n8n receives webhook
5. n8n PATCH Zoho CRM (Dealer_Meets subform entry)
6. n8n updates Firebase doc for that record
7. User returns to app → refreshes → sees updated data
```

### Background Sync Flow:
```
On every app open:
  For each Zoho UPS record:
    Firebase.setDoc(record.id, {
      ...zohoData,
      last_synced: timestamp
    })
```

---

## 3. Firebase Setup Steps (For You)

Follow these steps in order. I'll guide you through each screen.

### Step 1: Create Firebase Project
1. Go to [console.firebase.google.com](https://console.firebase.google.com)
2. Click **"Add project"**
3. Name it: `vss-ups-field-app`
4. Google Analytics: **Disable** (not needed)
5. Click **Create project** → wait → **Continue**

### Step 2: Enable Firestore (Database)
1. Left sidebar → **Build** → **Firestore Database**
2. Click **"Create database"**
3. Choose: **Start in test mode** (we'll add rules later)
4. Select a location closest to you (India: `asia-south1 — Mumbai`)
5. Click **Enable**

### Step 3: Enable Authentication (Anonymous)
1. Left sidebar → **Build** → **Authentication**
2. Click **"Get started"**
3. Go to **Sign-in method** tab
4. Click on **Anonymous**
5. Toggle **Enable** → **Save**

### Step 4: Register Web App
1. Left sidebar → ⚙️ (Settings) → **Project settings**
2. Scroll to **"Your apps"** section
3. Click **Web** icon `</>`
4. App nickname: `VSS UPS Field App`
5. **Don't** check "Firebase Hosting"
6. Click **Register app**

### Step 5: Copy Your Config
After registering, you'll see a `firebaseConfig` object like this:
```javascript
const firebaseConfig = {
  apiKey: "AIza...",
  authDomain: "vss-ups-field-app.firebaseapp.com",
  projectId: "vss-ups-field-app",
  storageBucket: "vss-ups-field-app.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```
**Copy this config and send it to me.** I'll put it in the app.

### Step 6: Firestore Rules (After Setup)
Once I give you the rules, paste these in:
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /ups_dealers/{recordId} {
      allow read: if request.auth != null;
      allow write: if request.auth != null;
    }
  }
}
```

---

## 4. Firestore Data Structure

```
Collection: ups_dealers
Doc ID: Zoho Record ID (e.g., "1171062000000994001")

{
  id: "1171062000000994001",           // Zoho record ID
  name: "Gayatri Batteries",
  phone: "+919448043392",
  dealer_code: "1000036990",
  dealer_type: "Distributor",
  email: "",
  address: "Bangalore, Karnataka",
  city: "Bangalore",
  state: "Karnataka",
  total_lifetime_value: null,
  last_order_date: null,
  last_order_value: null,
  total_visits: 0,
  next_followup: null,
  owner_email: "vsustainsolarenergy@gmail.com",
  dealer_meets: [],                    // Array of visit objects
  last_synced: Timestamp,              // Firebase server timestamp
  source: "zoho_crm"
}
```

---

## 5. Web App Flow

### On Every Load:
```javascript
async function initApp() {
  // 1. Load from Firebase instantly (no spinner)
  const dealers = await firebaseReadAll();
  renderDealerList(dealers); // fast render

  // 2. In background: sync from Zoho CRM
  const zohoRecords = await fetchAllFromZoho();
  for (const record of zohoRecords) {
    await firebaseSetDoc(record.id, {
      ...record,
      last_synced: serverTimestamp()
    });
  }

  // 3. Re-render with fresh data
  const updatedDealers = await firebaseReadAll();
  renderDealerList(updatedDealers);
}
```

### On Form Submit (after n8n updates Zoho):
```javascript
// After n8n → Zoho is updated
// n8n also updates Firebase directly via HTTP request node
// OR app manually re-syncs on next open

async function reSyncDealer(recordId) {
  const record = await fetchFromZoho(recordId);
  await firebaseSetDoc(recordId, { ...record, last_synced: serverTimestamp() });
}
```

---

## 6. n8n Workflow Update

```
[Google Form Submit] ──► [n8n Webhook]
                              │
                              ▼
                    [Code: Parse form data]
                              │
                              ▼
                    [HTTP: PATCH Zoho CRM]
                     UPS/{record_id} - Dealer_Meets entry
                              │
                              ▼
                    [HTTP: Update Firebase Doc]
                     Firestore REST API
                     PATCH /ups_dealers/{record_id}
                     { ...updated fields }
                              │
                              ▼
                       [Success ✓]
```

---

## 7. What I Need From You

Before I can start building:

1. **Firebase config** — the `firebaseConfig` object from Step 5 above
2. **Google Form URL** + **entry IDs** — same as before
3. **n8n webhook URL** — your existing n8n cloud URL?

Once you give me the Firebase config, I'll:
- Set up the complete app repo
- Write all the Firebase sync logic
- Deploy it to GitHub Pages

---

## 8. Implementation Steps (In Order)

### Day 1 (You — Firebase Setup, 20 mins):
- [ ] Create Firebase project
- [ ] Enable Firestore
- [ ] Enable Anonymous Auth
- [ ] Register web app
- [ ] Send me `firebaseConfig`

### Day 1 (Me — Web App Build, 2 hours):
- [ ] Create repo `vss-ups-field-app`
- [ ] Set up Firebase SDK
- [ ] Build dealer list (reads from Firebase)
- [ ] Build Zoho → Firebase sync function
- [ ] Build modal (tap card → dealer details)
- [ ] Build form pre-fill URL builder
- [ ] Deploy to GitHub Pages

### Day 2 (You — Google Form):
- [ ] Create Google Form with fields
- [ ] Send form URL + entry IDs

### Day 3 (Me — n8n Workflow + Firebase Rules):
- [ ] Build n8n workflow (form → Zoho PATCH → Firebase update)
- [ ] Write Firestore security rules
- [ ] End-to-end test

---

*Status: Awaiting Firebase config + Form URL from user*
