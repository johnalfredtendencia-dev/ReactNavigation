# Laboratory Activity: React Native Navigation

**Course:** Mobile Application Development  
**Topic:** React Native Navigation with Expo  
**Duration:** 2-3 hours  
**Difficulty:** Intermediate

---

## Objectives

By the end of this laboratory activity, students will be able to:

1. Set up a React Native development environment using Expo
2. Install and configure React Navigation library
3. Implement stack navigation between multiple screens
4. Handle navigation actions (navigate, goBack)
5. Configure Android SDK and emulator for testing
6. Use Git version control to manage and push code to a personal repository

---

## Prerequisites

- **Software Requirements:**
  - Node.js (v18 or later) - [Download](https://nodejs.org/)
  - Git - [Download](https://git-scm.com/)
  - Android Studio (for Android emulator) - [Download](https://developer.android.com/studio)
  - VS Code or any code editor
  
- **Knowledge Requirements:**
  - Basic JavaScript/ES6 syntax
  - React fundamentals (components, props, state)
  - Command line basics
  - Git basics (commit, push, pull)

- **Accounts:**
  - GitHub account for repository hosting

---

## Part 1: Environment Setup (30 minutes)

### 1.1 Install Node.js and npm
Verify installation:
```bash
node --version
npm --version
```

### 1.2 Install Git
Verify installation:
```bash
git --version
```

### 1.3 Configure Android Environment

#### Step 1: Install Android Studio
1. Download and install Android Studio from the official website
2. During installation, ensure "Android SDK" and "Android Virtual Device" are selected

#### Step 2: Install Android SDK Components
1. Open Android Studio
2. Go to **More Actions** → **SDK Manager**
3. Install the following:
   - **Android SDK Platform** (API Level 34 or latest)
   - **Android SDK Platform-Tools**
   - **Android SDK Command-line Tools**
4. Note the SDK location (typically: `/Users/YOUR_USERNAME/Library/Android/sdk` on macOS or `C:\Users\YOUR_USERNAME\AppData\Local\Android\Sdk` on Windows)

#### Step 3: Create Virtual Device (Emulator)
1. In Android Studio, go to **More Actions** → **Device Manager**
2. Click **Create Device**
3. Select a device (e.g., Pixel 4)
4. Select a system image (e.g., API 34)
5. Click **Finish**

#### Step 4: Set Environment Variables

**For macOS/Linux (zsh):**
```bash
# Add to ~/.zprofile or ~/.zshrc
export ANDROID_HOME="$HOME/Library/Android/sdk"
export PATH="$PATH:$ANDROID_HOME/emulator:$ANDROID_HOME/platform-tools"

# Apply changes
source ~/.zprofile
```

**For macOS/Linux (bash):**
```bash
# Add to ~/.bash_profile or ~/.bashrc
export ANDROID_HOME="$HOME/Library/Android/sdk"
export PATH="$PATH:$ANDROID_HOME/emulator:$ANDROID_HOME/platform-tools"

# Apply changes
source ~/.bash_profile
```

**For Windows (PowerShell):**
```powershell
# Set user environment variables
[System.Environment]::SetEnvironmentVariable('ANDROID_HOME', 'C:\Users\YOUR_USERNAME\AppData\Local\Android\Sdk', 'User')
[System.Environment]::SetEnvironmentVariable('Path', $env:Path + ';%ANDROID_HOME%\emulator;%ANDROID_HOME%\platform-tools', 'User')
```

#### Step 5: Verify adb Installation
```bash
adb --version
```

---

## Part 2: Project Setup (20 minutes)

### 2.1 Create Project Directory
```bash
# Create and navigate to project directory
mkdir ReactNativeNavigation
cd ReactNativeNavigation
```

### 2.2 Initialize Git Repository
```bash
git init
```

### 2.3 Create Project Structure

Create the following files and directories:

**File: `package.json`**
```json
{
  "name": "react-native-navigation-app",
  "version": "1.0.0",
  "main": "expo/AppEntry.js",
  "scripts": {
    "start": "expo start",
    "android": "expo start --android",
    "ios": "expo start --ios",
    "web": "expo start --web"
  },
  "dependencies": {
    "expo": "~52.0.0",
    "expo-status-bar": "~2.0.0",
    "react": "18.3.1",
    "react-native": "0.76.3",
    "@react-navigation/native": "^6.1.9",
    "@react-navigation/native-stack": "^6.9.17",
    "react-native-screens": "~4.2.0",
    "react-native-safe-area-context": "~4.12.0"
  },
  "devDependencies": {
    "@babel/core": "^7.25.2"
  },
  "private": true
}
```

**File: `app.json`**
```json
{
  "expo": {
    "name": "react-native-navigation-app",
    "slug": "react-native-navigation-app",
    "version": "1.0.0",
    "orientation": "portrait",
    "userInterfaceStyle": "light",
    "ios": {
      "supportsTablet": true
    },
    "android": {},
    "web": {}
  }
}
```

**File: `babel.config.js`**
```javascript
module.exports = function(api) {
  api.cache(true);
  return {
    presets: ['babel-preset-expo'],
  };
};
```

**File: `.gitignore`**
```
node_modules/
.expo/
.expo-shared/
dist/
npm-debug.*
*.jks
*.p8
*.p12
*.key
*.mobileprovision
*.orig.*
web-build/
.DS_Store
```

### 2.4 Install Dependencies
```bash
npm install
```

**Note:** If you encounter missing package errors, install them:
```bash
npm install expo-asset
npx expo install react-dom react-native-web @expo/metro-runtime
```

---

## Part 3: Implement Navigation (40 minutes)

### 3.1 Create Screens Directory
```bash
mkdir screens
```

### 3.2 Create Home Screen

**File: `screens/HomeScreen.js`**
```javascript
import React from 'react';
import { View, Text, Button, StyleSheet } from 'react-native';

export default function HomeScreen({ navigation }) {
  return (
    <View style={styles.container}>
      <Text style={styles.title}>Home Screen</Text>
      <Text style={styles.subtitle}>Welcome to React Native Navigation!</Text>
      <Button
        title="Go to Details"
        onPress={() => navigation.navigate('Details')}
      />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    alignItems: 'center',
    justifyContent: 'center',
    backgroundColor: '#fff',
    padding: 20,
  },
  title: {
    fontSize: 24,
    fontWeight: 'bold',
    marginBottom: 10,
  },
  subtitle: {
    fontSize: 16,
    color: '#666',
    marginBottom: 20,
    textAlign: 'center',
  },
});
```

### 3.3 Create Details Screen

**File: `screens/DetailsScreen.js`**
```javascript
import React from 'react';
import { View, Text, Button, StyleSheet } from 'react-native';

export default function DetailsScreen({ navigation }) {
  return (
    <View style={styles.container}>
      <Text style={styles.title}>Details Screen</Text>
      <Text style={styles.subtitle}>This is the details page.</Text>
      <Button
        title="Go to Home"
        onPress={() => navigation.navigate('Home')}
      />
      <View style={styles.spacer} />
      <Button
        title="Go Back"
        onPress={() => navigation.goBack()}
      />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    alignItems: 'center',
    justifyContent: 'center',
    backgroundColor: '#fff',
    padding: 20,
  },
  title: {
    fontSize: 24,
    fontWeight: 'bold',
    marginBottom: 10,
  },
  subtitle: {
    fontSize: 16,
    color: '#666',
    marginBottom: 20,
    textAlign: 'center',
  },
  spacer: {
    height: 10,
  },
});
```

### 3.4 Create Main App Component

**File: `App.js`**
```javascript
import * as React from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createNativeStackNavigator } from '@react-navigation/native-stack';
import HomeScreen from './screens/HomeScreen';
import DetailsScreen from './screens/DetailsScreen';

const Stack = createNativeStackNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator initialRouteName="Home">
        <Stack.Screen 
          name="Home" 
          component={HomeScreen}
          options={{ title: 'Home' }}
        />
        <Stack.Screen 
          name="Details" 
          component={DetailsScreen}
          options={{ title: 'Details' }}
        />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

---

## Part 4: Testing and Running (30 minutes)

### 4.1 Start Development Server
```bash
npm start
```

This will display a QR code and options to run on different platforms.

### 4.2 Run on Android Emulator

**Option A: Using Command**
```bash
npm run android
```

**Option B: Using Expo CLI**
1. Start the server: `npm start`
2. Press `a` in the terminal to launch Android emulator

**First-time Setup:**
- The emulator will take 30-60 seconds to boot
- Expo Go app will be installed automatically
- Your app will launch once the emulator is ready

### 4.3 Test Navigation

Test the following scenarios:
1. ✅ App launches and shows Home Screen
2. ✅ Tap "Go to Details" → navigates to Details Screen
3. ✅ Tap "Go Back" → returns to Home Screen
4. ✅ Tap "Go to Details" then "Go to Home" → navigates to Home Screen
5. ✅ Verify back button in navigation header works

### 4.4 Alternative Testing Methods

**Web Browser (for quick testing):**
```bash
npm run web
```

**Physical Android Device:**
1. Install Expo Go from Google Play Store
2. Run `npm start`
3. Scan QR code with Expo Go app
4. Ensure phone and computer are on same WiFi network

---

## Part 5: Version Control and Repository Push (20 minutes)

### 5.1 Create GitHub Repository

1. Go to [GitHub](https://github.com)
2. Click **New Repository**
3. Repository name: `react-native-navigation-lab`
4. Description: `Lab activity for React Native navigation`
5. Keep it **Public** or **Private** (as per your preference)
6. **Do NOT** initialize with README, .gitignore, or license
7. Click **Create Repository**

### 5.2 Create README.md

**File: `README.md`**
```markdown
# React Native Navigation Lab Activity

A React Native application demonstrating stack navigation using React Navigation and Expo.

## Student Information
- **Name:** [Your Full Name]
- **Student ID:** [Your ID]
- **Course:** Mobile Application Development
- **Date:** [Submission Date]

## Features
- Stack navigation between screens
- Home and Details screens
- Navigation buttons and gestures
- Android emulator support

## Technologies Used
- React Native 0.76.3
- Expo ~52.0.0
- React Navigation 6.x
- JavaScript/ES6

## Installation

\`\`\`bash
npm install
\`\`\`

## Running the App

\`\`\`bash
# Start development server
npm start

# Run on Android
npm run android

# Run on iOS
npm run ios

# Run on web
npm run web
\`\`\`

## Project Structure
\`\`\`
├── App.js                 # Main app with navigation
├── screens/
│   ├── HomeScreen.js     # Home screen
│   └── DetailsScreen.js  # Details screen
├── package.json          # Dependencies
├── app.json             # Expo configuration
└── README.md            # Documentation
\`\`\`

## Screenshots
[Add screenshots of your running app here]

## Challenges Faced
[Describe any challenges you encountered and how you resolved them]

## Learning Outcomes
[Describe what you learned from this lab activity]

## References
- [React Navigation Documentation](https://reactnavigation.org/)
- [Expo Documentation](https://docs.expo.dev/)
- [React Native Documentation](https://reactnative.dev/)
```

### 5.3 Stage and Commit Changes

```bash
# Check status
git status

# Add all files
git add .

# Commit with message
git commit -m "Initial commit: React Native navigation lab activity"
```

### 5.4 Link Local Repository to GitHub

Replace `YOUR_USERNAME` and `YOUR_REPO_NAME` with your actual GitHub username and repository name:

```bash
# Add remote origin
git remote add origin https://github.com/YOUR_USERNAME/react-native-navigation-lab.git

# Verify remote
git remote -v

# Push to GitHub
git branch -M main
git push -u origin main
```

### 5.5 Verify Upload

1. Refresh your GitHub repository page
2. Verify all files are uploaded
3. Check that README.md displays correctly

---

## Part 6: Enhancements (Optional - Extra Credit)

Implement one or more of the following enhancements:

### Enhancement 1: Add a Third Screen
- Create a `ProfileScreen.js` with navigation to/from other screens
- Add a button on Home screen to navigate to Profile

### Enhancement 2: Pass Parameters
- Modify navigation to pass data between screens
- Example: Pass a name from Home to Details and display it

```javascript
// In HomeScreen.js
navigation.navigate('Details', { itemId: 86, userName: 'John' });

// In DetailsScreen.js
const { itemId, userName } = route.params;
```

### Enhancement 3: Custom Styling
- Add custom header colors
- Implement custom header buttons
- Add icons to screens (install `@expo/vector-icons`)

### Enhancement 4: Tab Navigation
- Install tab navigator: `npm install @react-navigation/bottom-tabs`
- Implement bottom tab navigation with icons

---

## Submission Requirements

Submit the following:

1. **GitHub Repository Link**
   - Ensure repository is public or add instructor as collaborator
   - Include complete README.md with student information

2. **Screenshots** (minimum 3)
   - App running on Android emulator showing Home screen
   - Details screen
   - Navigation in action

3. **Lab Report** (PDF format)
   - Cover page with student information
   - Objectives and learning outcomes
   - Step-by-step process with screenshots
   - Challenges faced and solutions
   - Conclusion and reflection
   - References

4. **Screen Recording** (optional but recommended)
   - 1-2 minute video demonstrating navigation flow
   - Upload to YouTube/Google Drive and include link in README

---

## Grading Rubric

| Criteria | Points | Description |
|----------|--------|-------------|
| **Environment Setup** | 15 | Android SDK configured, emulator working |
| **Project Structure** | 15 | All files created correctly, proper organization |
| **Navigation Implementation** | 30 | Stack navigation working, proper navigation logic |
| **Code Quality** | 15 | Clean code, proper naming, comments |
| **Git/GitHub** | 15 | Proper commits, complete repository, README |
| **Testing** | 10 | App runs without errors, navigation tested |
| **Documentation** | 10 | Complete README, lab report submitted |
| **Extra Credit** | +10 | Enhancements implemented |
| **Total** | **100** | (+10 bonus) |

---

## Troubleshooting

### Issue: "expo: command not found"
**Solution:**
```bash
npm install -g expo-cli
```

### Issue: "Android SDK not found"
**Solution:**
- Verify ANDROID_HOME is set correctly
- Restart terminal after setting environment variables
- Check SDK path in Android Studio settings

### Issue: "Port 8081 already in use"
**Solution:**
```bash
# Kill process on port 8081
npx kill-port 8081

# Or use different port
expo start --port 8082
```

### Issue: "Unable to resolve module"
**Solution:**
```bash
# Clear cache and reinstall
rm -rf node_modules
npm install
npx expo start --clear
```

### Issue: Emulator won't start
**Solution:**
- Open Android Studio → Device Manager
- Manually start emulator by clicking play button
- Wait for emulator to fully boot, then run `npm run android`

---

## Additional Resources

- [React Native Documentation](https://reactnative.dev/)
- [React Navigation Docs](https://reactnavigation.org/docs/getting-started)
- [Expo Documentation](https://docs.expo.dev/)
- [Android Studio Setup](https://developer.android.com/studio)
- [Git Basics](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics)
- [Markdown Guide](https://www.markdownguide.org/)

---

## Support

For questions or issues:
- Check the troubleshooting section
- Review React Navigation documentation
- Ask instructor during lab hours
- Post in course discussion forum

---

## Academic Integrity

This is an individual assignment. You may discuss concepts with classmates, but all code must be your own work. Copying code from other students or online sources without proper attribution constitutes plagiarism.

---

**Good luck with your lab activity! 🚀**
