# Tummy Tracker 🌸

A preppy, installable PWA to track tummy aches and find patterns in food, drink, stress, and activity.

## Features
- Log entries with food/drink meal table, pain level, stress & activity
- Interactive calendar with color-coded pain dots
- Patterns view to spot triggers
- Google sign-in with Firebase — syncs across all your devices
- Installable as a PWA (home screen icon, works offline)

## Setup

### 1. Clone this repo
```bash
git clone https://github.com/YOUR_USERNAME/tummy-tracker.git
cd tummy-tracker
```

### 2. Configure Firebase
Follow the full setup guide in **FIREBASE_SETUP.md**, then fill in your config in `firebase-config.js`.

### 3. Deploy to GitHub Pages
- Push to GitHub
- Go to repo **Settings → Pages**
- Set source to `main` branch → Save
- Add your `username.github.io` domain to Firebase authorized domains

### File structure
```
tummy-tracker/
├── index.html          ← The whole app
├── firebase-config.js  ← YOUR Firebase config goes here
├── manifest.json       ← PWA manifest
├── sw.js               ← Service worker (offline support)
├── icon-192.svg        ← Home screen icon (small)
├── icon-512.svg        ← Home screen icon (large)
├── FIREBASE_SETUP.md   ← Step-by-step Firebase guide
└── README.md           ← This file
```

## Data & Privacy
All data is stored in **your own Firebase Firestore** under your Google account.
Firestore security rules ensure only you can read/write your entries.
