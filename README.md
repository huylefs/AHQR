# AHQR - Android QR Code Application

<p align="center">
  <strong>Android QR code scanner and generator application</strong>
</p>

---

## 📋 Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Screenshots](#screenshots)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [QR Code Types Supported](#qr-code-types-supported)
- [Team Members](#team-members)

---

## 🎯 Introduction <a name="introduction"></a>

**AHQR** is an end-term project developed at **Samsung R&D Vietnam Internship**. This Android application provides comprehensive QR code functionality, allowing users to both scan existing QR codes and generate new ones based on various data types including URLs, phone numbers, emails, SMS, contacts (meCard), locations, and plain text.

The app features a custom-built QR code generation engine implementing the QR Code standard with support for multiple error correction levels, making it a robust solution for QR code operations.

---

## ✨ Features <a name="features"></a>

### QR Code Scanning
- 📷 **Image-based scanning** - Pick QR code images from your device gallery
- 🔍 **Smart detection** - Automatically identifies QR code content type
- 📱 **Quick actions** - Perform actions directly (call, browse, send SMS/email)
- 📜 **Scan history** - All scanned QR codes are saved locally with timestamps
- 🗑️ **History management** - Delete or re-execute saved QR codes

### QR Code Generation
- 🌐 **Website URLs** - Generate QR codes for web links
- 📞 **Phone calls** - Create dial-ready QR codes
- 💬 **SMS messages** - Generate QR codes with phone number and pre-filled message
- 📧 **Emails** - Create email QR codes with recipient, subject, and body
- 📝 **Free text** - Encode any plain text
- 👤 **meCard contacts** - Generate contact cards with name, phone, email, address, URL, and nickname
- 📍 **Locations** - Create Google Maps location QR codes

### Additional Features
- 💾 **Save QR codes** - Save generated QR codes to your device gallery
- 📤 **Share QR codes** - Share generated QR codes via any app
- ⚙️ **Customization** - Configure error correction level (L, M, Q, H) and block size
- 🎨 **Modern UI** - Material Design with bottom navigation
- 🌙 **Dark mode support** - System theme integration

---



---

## 🛠️ Tech Stack <a name="tech-stack"></a>

| Category | Technology |
|----------|------------|
| **Language** | Java |
| **Min SDK** | 24 (Android 7.0 Nougat) |
| **Target SDK** | 34 (Android 14) |
| **Build System** | Gradle 8.4.1 |
| **UI Components** | Material Design 1.12.0 |
| **Navigation** | Jetpack Navigation 2.7.7 |
| **Database** | Room 2.6.1 |
| **Lifecycle** | ViewModel & LiveData 2.8.3 |
| **QR Processing** | ZXing 3.3.2 + ZXing Android Embedded 3.6.0 |
| **View Binding** | Enabled |

---

## 📁 Project Structure <a name="project-structure"></a>

```
app/src/main/java/com/app/src/ahqr/
├── data/
│   ├── model/
│   │   ├── MyQR.java              # Room Entity for QR history
│   │   └── MyQRDao.java           # Data Access Object
│   └── repository/
│       ├── MyQRDatabase.java      # Room Database singleton
│       └── MyQRRepository.java    # Repository pattern implementation
│
├── ui/
│   ├── adapter/
│   │   └── QRAdapter.java         # RecyclerView adapter for QR history
│   └── main/
│       ├── MainActivity.java      # Main activity with navigation
│       ├── SplashActivity.java    # Splash screen
│       └── fragment/
│           ├── GenerateFragment.java    # QR generation UI
│           ├── GenerateViewModel.java   # Generation business logic
│           ├── ScanFragment.java        # QR scanning UI
│           └── ScanViewModel.java       # Scanning business logic
│
└── utils/
    ├── Constant.java              # App constants
    ├── DateTimeConverters.java    # Room type converters
    └── generate/
        ├── QRCodeDataEncoding.java      # Data encoding implementation
        ├── QRCodeFacade.java            # Main QR generation facade
        ├── QRCodeModulePlacement.java   # Module placement algorithm
        ├── QRErrorCorrectionEncoding.java  # Reed-Solomon error correction
        └── QRVersion.java               # QR version and capacity tables
```

---

## 📥 Installation <a name="installation"></a>

### Prerequisites
- Android Studio Hedgehog (2023.1.1) or later
- JDK 8 or higher
- Android device/emulator with API 24+

### Build Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/AHQR.git
   cd AHQR
   ```

2. **Open in Android Studio**
   - Launch Android Studio
   - Select "Open an Existing Project"
   - Navigate to the cloned directory

3. **Sync Gradle**
   - Android Studio will automatically sync Gradle dependencies
   - If not, click "Sync Project with Gradle Files"

4. **Build and Run**
   ```bash
   ./gradlew assembleDebug
   ```
   Or use the Run button in Android Studio

---

## 📱 Usage <a name="usage"></a>

### Scanning QR Codes

1. Open the app and navigate to the **Scan** tab
2. Tap the floating action button (📷)
3. Grant media access permission when prompted
4. Select a QR code image from your gallery
5. The app will decode the QR code and:
   - Display a dialog with the detected action
   - Save the scan to history
   - Offer to perform the action (open URL, call, etc.)

### Generating QR Codes

1. Navigate to the **Generate** tab
2. Select the **QR Code Action** type from the dropdown:
   - Browse to a website
   - Make a phone call
   - Send an SMS
   - Send an E-mail
   - Free Formatted Text
   - meCard (contact)
   - Location
3. Fill in the required fields
4. Optionally configure:
   - **Error Correction Level**: L (7%), M (15%), Q (25%), H (30%)
   - **Block Size**: Controls the QR code module size
5. Tap **Generate** to create the QR code
6. Use **Save** to store in gallery or **Share** to send via other apps

---

## 📊 QR Code Types Supported <a name="qr-code-types-supported"></a>

| Type | Format | Example |
|------|--------|---------|
| **URL** | `http://` or `https://` | `https://example.com` |
| **Phone Call** | `tel:` | `tel:+1234567890` |
| **SMS** | `smsto:` | `smsto:+1234567890:Hello!` |
| **Email** | `mailto:` | `mailto:test@email.com?subject=Hi&body=Hello` |
| **Plain Text** | Raw text | `Hello World` |
| **meCard** | `MECARD:` | `MECARD:N:John Doe;TEL:123456;EMAIL:john@email.com;` |
| **Location** | Google Maps URL | `https://www.google.com/maps/search/?api=1&query=...` |

---

## 🔧 Error Correction Levels

The app supports all standard QR code error correction levels:

| Level | Recovery Capacity | Use Case |
|-------|-------------------|----------|
| **L** | ~7% | Maximum data capacity |
| **M** | ~15% | Standard use (default) |
| **Q** | ~25% | Higher reliability |
| **H** | ~30% | Maximum error recovery |

---

## 🔐 Permissions

The app requires the following permissions:

| Permission | Purpose |
|------------|---------|
| `CAMERA` | For potential future camera scanning |
| `READ_EXTERNAL_STORAGE` | Reading QR code images |
| `WRITE_EXTERNAL_STORAGE` | Saving generated QR codes |
| `READ_MEDIA_VISUAL_USER_SELECTED` | Android 13+ photo picker |

---

## 👥 Team Members <a name="team-members"></a>

| Name | Role |
|------|------|
| **Đinh Thế An** | Developer |
| **Lê Đình Huy** | Developer |

*Samsung R&D Vietnam Internship Project*

---
## 🙏 Acknowledgments

- [ZXing](https://github.com/zxing/zxing) - QR code processing library
- [Material Design Components](https://material.io/develop/android) - UI components
- [Android Jetpack](https://developer.android.com/jetpack) - Architecture components

---

