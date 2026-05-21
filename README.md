# 🧠 IngatKu – Smart Reminder for Elderly & PWD

[![Hackathon Project](https://img.shields.io/badge/Hackathon-2026-blue)](https://github.com/your-repo)
[![Flutter](https://img.shields.io/badge/Frontend-Flutter-blue)](https://flutter.dev)
[![Firebase](https://img.shields.io/badge/Backend-Firebase-yellow)](https://firebase.google.com)
[![Gemini AI](https://img.shields.io/badge/AI-Gemini%202.5%20Flash-orange)](https://deepmind.google/gemini)

**IngatKu** (from Malay *Ingat* = Remember) is a mobile application designed to help elderly and people with disabilities (PWD) never miss hospital appointments or medication doses. The app **automatically captures** incoming notification alerts from hospital systems, clinic portals, or caregiver apps and instantly creates or updates reminders inside IngatKu – no manual entry needed.

> 🏆 Built for ElectroHack 2.0 – tackling accessibility & healthcare adherence.

---

## 📖 Table of Contents
- [Inspiration](#inspiration)
- [Features](#features)
- [How It Works](#how-it-works)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [UI/UX Design](#uiux-design)
- [AI Integration](#ai-integration)
- [Team](#team)
- [License](#license)

---

## 💡 Inspiration
Elderly users often struggle with:
- Forgetting to enter appointments into calendars.
- Overwhelming multiple apps and notifications.
- Low tech literacy for manual scheduling.

IngatKu solves this by **listening to existing notifications** (with user permission) and intelligently parsing them into clear, accessible reminders – all in one place.

---

## ✨ Features
- 🔔 **Automatic notification listener** – reads alerts from hospital, pharmacy, or clinic apps.
- 📅 **Appointment & medication reminders** – parsed directly into the in-app calendar.
- 🤖 **AI‑powered extraction** (Gemini 2.5 Flash) – converts raw notification text into structured events (date, time, medicine name, dosage).
- 🗣️ **Voice & large‑text accessible UI** – designed for low vision and fine motor difficulty.
- 📲 **Cross‑platform** – Flutter app for Android (iOS coming soon).
- ☁️ **Cloud sync** – reminders stored in Firebase, accessible by caregivers if needed.

---

## ⚙️ How It Works
1. User grants **Notification Read Permission** (Android `NotificationListenerService`).
2. When any new notification arrives (e.g., "Your appointment at Klinik Sehat is tomorrow 10 AM" or "Take Metformin 500mg with dinner"), IngatKu intercepts it.
3. The notification text is sent to a **Python backend** hosted on Firebase Cloud Functions (or similar).
4. **Gemini 2.5 Flash** extracts structured data: `{ type, datetime, medicine, dose, location, ... }`.
5. The parsed reminder is saved to **Firestore** and appears instantly in the user’s Flutter app.
6. Local and push notifications remind the user before each event.

---

## 🧰 Tech Stack
| Layer       | Technology                                      |
|-------------|-------------------------------------------------|
| Frontend    | Flutter (Dart)                                  |
| Backend     | Python (FastAPI / Flask) + Firebase Cloud Functions |
| Database    | Firebase Firestore + Firebase Authentication   |
| AI / NLP    | **Gemini 2.5 Flash** (via Vertex AI or Google AI Studio) |
| UI Design   | Penpot (design system & prototyping)            |
| Notifications (Android) | `NotificationListenerService` + WorkManager |

---
## Getting Started

### Prerequisites

Make sure you have the following installed:

- [Flutter SDK](https://docs.flutter.dev/get-started/install) `^3.11.4`
- [Dart SDK](https://dart.dev/get-dart) (included with Flutter)
- [Android Studio](https://developer.android.com/studio) or [VS Code](https://code.visualstudio.com/) with Flutter extension
- A Firebase project set up (see Firebase Setup below)

---

### Installation

1. **Clone the repository**
```bash
   git clone https://github.com/NazilHaziq1/IngatKu---ElectroHack-2.0.git
   cd IngatKu---ElectroHack-2.0
```

2. **Install dependencies**
```bash
   flutter pub get
```

3. **Firebase Setup**
   - Go to [Firebase Console](https://console.firebase.google.com/) and create a project
   - Enable **Authentication** (Email/Password or your chosen method)
   - Enable **Cloud Firestore**
   - Download `google-services.json` (Android) and/or `GoogleService-Info.plist` (iOS)
   - Place them in the appropriate directories:
     - Android: `android/app/google-services.json`
     - iOS: `ios/Runner/GoogleService-Info.plist`

4. **Run the app**
```bash
   flutter run
```

