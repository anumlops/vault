# Vault - Shared Credential Manager

A single-file password vault application that runs directly in the browser with no build tools required.

## Features

- 🔐 AES password encryption
- 👥 Support for multiple persons (Me/Her)
- 📁 Category and subcategory organization
- 🔍 Live search across platforms and usernames
- 👁️ Show/hide passwords
- 📋 Copy username/password to clipboard
- 🔄 Real-time sync with Firestore
- 🤝 Partner sharing

## Quick Start

1. Open index.html in your browser (or use GitHub Pages)
2. Register a new account
3. Create categories and add credentials

## Firebase Setup

1. Create a project at https://console.firebase.google.com
2. Enable **Email/Password** authentication
3. Create a **Firestore Database** (production mode)
4. Deploy these security rules:

`
rules_version = '2';
service cloud.firestore {
  match /datachines/{database}/documents {
    match /vaults/{userId}/{document=**} {
      allow read, write: if request.auth.uid == userId;
    }
    match /users/{userId} {
      allow read: if request.auth != null;
      allow write: if request.auth.uid == userId;
    }
  }
}
`

## Tech Stack

- React 18 (via CDN)
- Firebase Auth + Firestore
- CryptoJS for AES encryption
- No build tools required

## License

MIT