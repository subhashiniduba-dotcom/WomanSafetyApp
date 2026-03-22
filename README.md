# WomanSafetyApp
[README.md](https://github.com/user-attachments/files/26165384/README.md)
# Women Safety App 🛡️

An Android safety application built with Kotlin featuring SOS alerts, live location sharing, fake call, and safe route navigation.

---

## Features

- **SOS Alert** — Hold 3 seconds to send your GPS location via SMS to all emergency contacts
- **Live Location Sharing** — Stream real-time location to trusted contacts via Firebase
- **Fake Call** — Simulate an incoming call to escape uncomfortable situations
- **Safe Route Navigation** — Google Maps navigation with route deviation alerts

---

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Kotlin |
| Architecture | MVVM + Repository |
| Database | Room (local contacts) |
| Backend | Firebase (Auth, Realtime DB, FCM) |
| Maps | Google Maps SDK + Directions API |
| Background | Foreground Services, WorkManager |

---

## Setup Instructions

### 1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/WomenSafetyApp.git
cd WomenSafetyApp
```

### 2. Set up Firebase
1. Go to [Firebase Console](https://console.firebase.google.com)
2. Create a new project
3. Add an Android app with package name: `com.womensafety.app`
4. Download `google-services.json`
5. Replace `app/google-services.json` with your downloaded file
6. Enable **Authentication**, **Realtime Database**, and **Cloud Messaging** in Firebase Console

### 3. Set up Google Maps API Key
1. Go to [Google Cloud Console](https://console.cloud.google.com)
2. Enable **Maps SDK for Android** and **Directions API**
3. Create an API key
4. Open `gradle.properties` and replace:
   ```
   MAPS_API_KEY=YOUR_MAPS_API_KEY_HERE
   ```
   with your actual key

### 4. Open in Android Studio
- Open Android Studio → **Open** → Select the `WomenSafetyApp` folder
- Wait for Gradle sync to complete
- Run on a device or emulator (API 26+)

---

## Project Structure

```
app/src/main/java/com/womensafety/app/
├── model/              # Data classes (Contact, LocationData)
├── repository/         # Room DB, DAO, ContactRepository
├── viewmodel/          # MainViewModel
├── service/            # SosService, LocationTrackingService, FCM
├── receiver/           # BootReceiver, VolumeButtonReceiver
├── utils/              # LocationHelper, PermissionHelper
└── ui/
    ├── home/           # MainActivity
    ├── contacts/       # ContactsActivity, ContactsAdapter
    ├── fakecall/       # FakeCallActivity
    └── navigation/     # NavigationActivity
```

---

## Permissions Required

| Permission | Purpose |
|---|---|
| `ACCESS_FINE_LOCATION` | Get GPS coordinates for SOS |
| `ACCESS_BACKGROUND_LOCATION` | Track location when app is closed |
| `SEND_SMS` | Send SOS alerts to contacts |
| `FOREGROUND_SERVICE` | Keep SOS and location services alive |
| `POST_NOTIFICATIONS` | Show SOS and tracking notifications |
| `RECEIVE_BOOT_COMPLETED` | Restart services after phone reboot |

---

## GitHub Actions CI

This project includes a CI pipeline (`.github/workflows/android.yml`) that:
- Runs unit tests on every push
- Builds a debug APK
- Uploads the APK as an artifact

To use it, add your `google-services.json` content as a GitHub secret named `GOOGLE_SERVICES_JSON`.

---

## Contributing

Pull requests are welcome! For major changes, please open an issue first.

---

## License

MIT License — feel free to use and modify.
