# Pulse Backend - The Bio Rhythm

## 🔥 Firebase Backend Architecture

This repository contains the backend configuration and security rules for Pulse, a bio rhythm habit tracking application built with Firebase.

## 🏗️ Tech Stack

- **Firebase Authentication** - User authentication with email/password
- **Cloud Firestore** - NoSQL database for storing habits and user data
- **Firebase Hosting** - Configuration for potential static hosting

## 📊 Database Schema

### Collections

#### `habits`
```javascript
{
  id: string,              // Auto-generated document ID
  userId: string,          // Firebase Auth UID
  name: string,            // Habit name (e.g., "Drink 8 glasses of water")
  completedDates: array,   // Array of ISO date strings (e.g., ["2024-10-24"])
  streak: number,          // Current consecutive days streak
  createdAt: string        // ISO timestamp
}
```

## 🔐 Security Rules

The Firestore security rules ensure:
- Users can only read/write their own habits
- All operations require authentication
- Data is validated on the server side

See `firestore.rules` for the complete implementation.

## 📈 Indexes

Composite indexes are configured for efficient queries:
- `userId` (ascending) + `createdAt` (descending)

This allows for fast retrieval of a user's habits sorted by creation date.

## 🚀 Deployment

Firebase backend is automatically deployed and managed. No additional deployment steps required.

### Firebase Project Details
- **Project ID:** `mindtrack-bed82`
- **Auth Domain:** `mindtrack-bed82.firebaseapp.com`
- **Region:** Auto-selected based on configuration

## 🔑 Environment Variables

The frontend connects to Firebase using the following configuration (already set up):
```javascript
apiKey: "AIzaSyBQw_2tOukJIpcVBw17Ub1K7PbJWqoeOh0"
authDomain: "mindtrack-bed82.firebaseapp.com"
projectId: "mindtrack-bed82"
```

## 📝 API Operations

### Authentication
- `signup(email, password)` - Create new user account
- `login(email, password)` - Sign in existing user
- `logout()` - Sign out current user

### Habits CRUD
- `addDoc(collection(db, 'habits'), habitData)` - Create habit
- `getDocs(query(...))` - Read user's habits
- `updateDoc(doc(...), updates)` - Update habit (mark complete/incomplete)
- `deleteDoc(doc(...))` - Delete habit

## 🛡️ Security Features

- Row-level security: Users can only access their own data
- Authentication required for all operations
- Server-side validation of data structure
- Protection against injection attacks

## 🔗 Related Repositories

- [Frontend Repository](https://github.com/YOUR_USERNAME/mindtrack-frontend)

## 📧 Contact

For questions or issues, please open an issue in this repository.
