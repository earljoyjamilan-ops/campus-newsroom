# Firebase Auto-Connect Setup

Use this when Campus Newsroom is already uploaded to GitHub Pages and you want students to open the app without manually pasting Firebase config.

## What To Edit

Open `index.html` and find this line:

```js
const TLS_BUILT_IN_FIREBASE_CONFIG=null;
```

Replace `null` with your Firebase web config object:

```js
const TLS_BUILT_IN_FIREBASE_CONFIG={
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

## After Editing

1. Save `index.html`.
2. Upload the updated `index.html` to the GitHub repository root.
3. Wait for GitHub Pages to update.
4. Open the GitHub Pages link on another device.
5. The app should connect to Firebase automatically.

## Important

Use only one main admin device to push the first complete data set. Other devices should pull cloud data first.
