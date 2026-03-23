# Firebase Setup Guide for Tummy Tracker

## Step 1 — Create Firebase project
1. Go to https://console.firebase.google.com
2. Click "Add project" → name it `tummy-tracker`
3. Turn OFF Google Analytics → "Create project"

## Step 2 — Set up Firestore
1. Left sidebar → "Firestore Database" → "Create database"
2. Choose "Start in test mode" → Next
3. Pick a region close to you (e.g. us-central1) → "Enable"

## Step 3 — Register your web app
1. Project Overview → click "</>" (web icon)
2. Name it `tummy-tracker-web` → "Register app"
3. Copy the firebaseConfig object shown — you'll need it next

## Step 4 — Add your config to the app
1. Open `firebase-config.js`
2. Replace the placeholder values with your real config:

```js
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

## Step 5 — Enable Google Sign-in
1. Left sidebar → "Authentication" → "Get started"
2. Click "Google" → toggle ON → set support email → "Save"

## Step 6 — Set Firestore security rules
1. Firestore Database → "Rules" tab
2. Replace all content with:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId}/entries/{entryId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```
3. Click "Publish"

## Step 7 — Add your GitHub Pages domain to Firebase
1. Firebase console → Authentication → Settings → Authorized domains
2. Click "Add domain"
3. Add: `YOUR_GITHUB_USERNAME.github.io`

## Step 8 — Deploy to GitHub Pages
1. Push all files to a GitHub repo
2. Go to repo Settings → Pages
3. Set Source to "main" branch → Save
4. Your app will be live at: https://YOUR_USERNAME.github.io/REPO_NAME

---

## IMPORTANT: Never commit firebase-config.js with real keys to a public repo!
Use the placeholder version in the repo and fill in your real keys locally,
OR use GitHub Secrets + a build step if you want full automation.
For a simple personal app, keeping the config in the file is fine since
Firestore rules protect your data regardless.
