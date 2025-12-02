# React Native Navigation Lab Activity

A React Native application demonstrating stack navigation using React Navigation and Expo.

## Student Information
- **Name:** [Your Full Name]
- **Student ID:** [Your Student ID]
- **Course:** Mobile Application Development
- **Date:** [Submission Date]

## Features
- Stack navigation between screens
- Home and Details screens
- Navigation buttons and gestures
- Android emulator support
- Clean and modern UI design

## Technologies Used
- React Native 0.76.3
- Expo ~52.0.0
- React Navigation 6.x
- JavaScript/ES6

## Project Structure

```
.
├── App.js                           # Main app with navigation setup
├── screens/
│   ├── HomeScreen.js               # Home screen component
│   └── DetailsScreen.js            # Details screen component
├── package.json                     # Project dependencies
├── app.json                        # Expo configuration
├── babel.config.js                 # Babel configuration
├── README.md                       # This file
└── LAB_ACTIVITY_INSTRUCTIONS.md    # Complete lab instructions
```

## Installation

Install all dependencies:

```bash
npm install
```

If you encounter missing package errors:
```bash
npm install expo-asset
npx expo install react-dom react-native-web @expo/metro-runtime
```

## Running the App

### Start Development Server
```bash
npm start
```

### Run on Android Emulator
```bash
npm run android
```

### Run on iOS Simulator (macOS only)
```bash
npm run ios
```

### Run on Web Browser
```bash
npm run web
```

### Using Expo Go (Physical Device)
1. Install Expo Go from App Store/Play Store
2. Run `npm start`
3. Scan QR code with Expo Go app
4. Ensure device and computer are on same WiFi

## Navigation Structure

The app implements a **Stack Navigator** with two screens:

### Home Screen
- Welcome message
- Button to navigate to Details screen
- Uses `navigation.navigate('Details')` method

### Details Screen
- Details information
- "Go to Home" button using `navigation.navigate('Home')`
- "Go Back" button using `navigation.goBack()`
- Hardware back button support

## Android Setup

### Environment Variables (macOS/Linux)
```bash
export ANDROID_HOME="$HOME/Library/Android/sdk"
export PATH="$PATH:$ANDROID_HOME/emulator:$ANDROID_HOME/platform-tools"
```

Add these to `~/.zprofile` or `~/.bashrc` for persistence.

### Environment Variables (Windows)
```powershell
setx ANDROID_HOME "C:\Users\YOUR_USERNAME\AppData\Local\Android\Sdk"
setx PATH "%PATH%;%ANDROID_HOME%\emulator;%ANDROID_HOME%\platform-tools"
```

## Testing Checklist

- [ ] App launches successfully
- [ ] Home screen displays correctly
- [ ] "Go to Details" button navigates to Details screen
- [ ] "Go Back" button returns to Home screen
- [ ] "Go to Home" button navigates to Home screen
- [ ] Hardware back button works
- [ ] Navigation header displays correct titles
- [ ] No console errors or warnings

## Screenshots

[Add screenshots of your running app here]

Example:
- Screenshot 1: Home Screen on Android Emulator
- Screenshot 2: Details Screen on Android Emulator
- Screenshot 3: Navigation in action

## Challenges Faced

[Document any challenges you encountered during the lab and how you resolved them]

Example:
- **Challenge:** Android SDK not found
- **Solution:** Set ANDROID_HOME environment variable and added to PATH

## Learning Outcomes

[Describe what you learned from this lab activity]

Example learning outcomes:
- Understanding of React Navigation stack navigator
- Setting up Android development environment
- Implementing screen-to-screen navigation
- Using navigation props and methods
- Version control with Git and GitHub

## Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| expo | ~52.0.0 | Development framework |
| react-native | 0.76.3 | Mobile app framework |
| @react-navigation/native | ^6.1.9 | Navigation core |
| @react-navigation/native-stack | ^6.9.17 | Stack navigator |
| react-native-screens | ~4.2.0 | Native screen components |
| react-native-safe-area-context | ~4.12.0 | Safe area handling |

## Git Commands Used

```bash
# Initialize repository
git init

# Stage changes
git add .

# Commit changes
git commit -m "Initial commit: React Native navigation lab"

# Add remote
git remote add origin https://github.com/YOUR_USERNAME/REPO_NAME.git

# Push to GitHub
git branch -M main
git push -u origin main
```

## Troubleshooting

### Port Already in Use
```bash
npx kill-port 8081
```

### Clear Cache
```bash
npx expo start --clear
```

### Reinstall Dependencies
```bash
rm -rf node_modules
npm install
```

## References

- [React Native Documentation](https://reactnative.dev/)
- [React Navigation Documentation](https://reactnavigation.org/)
- [Expo Documentation](https://docs.expo.dev/)
- [Android Studio Setup Guide](https://developer.android.com/studio)
- [Git Documentation](https://git-scm.com/doc)

## Submission

This project is submitted as part of the Mobile Application Development course lab activity.

**Repository Link:** [Add your GitHub repository link here]

---

**Completed by:** [Your Name]  
**Submission Date:** [Date]
