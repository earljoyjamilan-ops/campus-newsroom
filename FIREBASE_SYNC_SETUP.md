# Campus Newsroom: Firebase Sync Setup

This is the first production-sync upgrade. The app can still run locally, but when Firebase is connected it can share data across student, teacher, editor, and admin devices.

## What Firebase Will Sync

- Registered users
- Articles and revision history
- Notifications
- Lesson progress
- Practice attempts and assignments
- Certificates and certificate settings
- Press ID settings
- Coverage desk records and meeting minutes

## Create Firebase Project

1. Go to `https://console.firebase.google.com/`.
2. Create a project named `Campus Newsroom`.
3. Add a Web app.
4. Copy the Firebase configuration object.
5. Enable Firestore Database.

Firebase's official web setup guide says a web app receives a Firebase configuration object when you register it, and that object connects the app to the Firebase project resources.

## Temporary Firestore Rules for Pilot Testing

Use these only for a controlled pilot. Replace them with stricter role-based rules before school-wide production.

```txt
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /newsroomState/{docId} {
      allow read, write: if true;
    }
  }
}
```

## Connect Inside the App

1. Open Campus Newsroom.
2. Log in as the Publication Administrator.
3. Click the floating `Online Sync` button.
4. Paste the Firebase config JSON.
5. Click `Save Config`.
6. Click `Connect`.
7. Click `Push This Device Data` if your current device has the latest demo records.

After that, another device can open the same app, connect to the same Firebase project, and click `Pull Cloud Data`.

## Important Production Notes

- This first sync bridge stores the app state in one Firestore document for easy pilot testing.
- For full school-wide production, the next upgrade should split the data into secure collections: users, articles, comments, evaluations, badges, certificates, coverage, attendance, and files.
- Profile photos and article photos are currently stored as browser image data. For production, move those to Firebase Storage.
- Do not use open Firestore rules for a real school-wide launch.

