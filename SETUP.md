# Setting Up LUMIO Locally

This guide walks you through running LUMIO on your own computer for development or testing. Read every step before starting.

---

## What You Need Before Starting

- A computer running Windows, Mac, or Linux
- Internet connection for the initial setup
- About 2–3 hours for first-time setup
- No prior coding experience required — just follow each step

---

## Step 1 — Install Flutter

Flutter is the tool that builds LUMIO for both Android and iOS.

1. Go to **flutter.dev/docs/get-started/install**
2. Select your operating system (Windows / Mac / Linux)
3. Follow their official instructions exactly
4. When finished, open your terminal and type:

```
flutter doctor
```

This checks if everything installed correctly. All items should show a green checkmark. If something shows a red X, Google the exact error message — Flutter has excellent documentation.

---

## Step 2 — Install Git

Git is how you download and manage the project code.

**Windows:**
Go to **git-scm.com** → Download → Install with default settings

**Mac:**
Open Terminal and type:
```
git --version
```
If Git is not installed, Mac will prompt you to install it automatically.

**Linux:**
```
sudo apt install git
```

---

## Step 3 — Clone the Repository

This downloads the LUMIO code to your computer.

Open your terminal and type:

```
git clone https://github.com/henaswarnali-tech/Lumio.git
```

Then navigate into the folder:

```
cd Lumio
```

---

## Step 4 — Install Dependencies

This installs everything LUMIO needs to run:

```
flutter pub get
```

Wait for it to finish. This may take a few minutes.

---

## Step 5 — Set Up Firebase

LUMIO uses Firebase for user data, offline sync, and authentication.

1. Go to **console.firebase.google.com**
2. Create a free account if you do not have one
3. Tap **"Add project"** → name it `lumio-dev`
4. Follow Firebase setup instructions for Flutter at **firebase.google.com/docs/flutter/setup**
5. Download the config file and place it in the correct folder as instructed

---

## Step 6 — Run the App

Connect an Android device or start an emulator, then type:

```
flutter run
```

The app will build and launch. First build takes 3–5 minutes. After that it is much faster.

---

## Running on Android Device

1. On your Android phone go to **Settings → About Phone**
2. Tap **Build Number** seven times — this enables Developer Mode
3. Go to **Settings → Developer Options** → turn on **USB Debugging**
4. Connect your phone to your computer with a USB cable
5. Run `flutter devices` to confirm your phone is detected
6. Run `flutter run` to launch LUMIO on your phone

---

## Common Problems

**flutter doctor shows errors:**
Google the exact error message. Flutter's documentation covers almost every issue.

**firebase not connecting:**
Double check the config file is in the correct folder exactly as Firebase instructed.

**App builds but crashes immediately:**
Open an Issue on GitHub with the exact error message from your terminal.

---

## Project Folder Structure

```
lumio/
├── lib/                    # All Flutter app code
│   ├── main.dart           # App entry point
│   ├── screens/            # Individual app screens
│   ├── widgets/            # Reusable UI components
│   ├── models/             # Data structures
│   └── services/           # Firebase and other services
├── assets/
│   ├── animations/         # Lottie and Rive files
│   ├── images/             # Illustrations and icons
│   └── audio/              # Lesson audio files
├── curriculum/             # Lesson content in markdown
├── translations/           # Language files
├── CONTRIBUTING.md         # How to contribute
├── SETUP.md                # This file
└── README.md               # Project overview
```

---

## Need Help?

Open an Issue on GitHub describing exactly:
- What step you are on
- What you typed
- What error message appeared

We will help you from there.

---

*Thank you for setting up LUMIO. Every developer who runs this locally brings the project one step closer to the children it was built for.*
