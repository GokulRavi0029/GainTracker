# GainTrack V4

Dashboard-first nutrition and muscle-gain tracker with Firebase cloud sync.

## Current features
- Daily calories, protein, carbs, and fat tracking
- Micronutrient tracking
- USDA FoodData Central search
- Automatic local food caching
- Monthly calendar/history
- Weight tracking and 7-day averages
- Google Sign-In through Firebase Authentication
- Cloud Firestore synchronization
- Local/offline browser storage
- JSON backup and restore

## Firebase
This build is configured for the `gaintrack-62d22` Firebase project.

Required Firebase services:
- Authentication: Google provider enabled
- Cloud Firestore

Recommended Firestore rules:

```text
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## Login
Use **Continue with Google** in Settings. The same Google account on Mac and iPhone maps to the same Firebase UID and Firestore data.

## Hosting
The app is a static site and can be hosted with GitHub Pages or another HTTPS static host. Google/Firebase authentication should be used from the hosted URL rather than by opening `index.html` directly from disk.
