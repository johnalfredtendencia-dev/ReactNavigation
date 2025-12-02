# Quick Reference Guide - React Native Navigation Lab

## Quick Start Commands

```bash
# Install dependencies
npm install

# Start development server
npm start

# Run on Android
npm run android

# Run on web
npm run web
```

---

## Git Workflow for Submission

### 1. Initial Setup
```bash
# Create GitHub repository first (on GitHub website)
# Then in your project directory:

git init
git add .
git commit -m "Initial commit: React Native navigation lab activity"
```

### 2. Connect to GitHub
```bash
# Replace YOUR_USERNAME and YOUR_REPO with your actual GitHub info
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git branch -M main
git push -u origin main
```

### 3. Making Changes
```bash
# After making changes
git add .
git commit -m "Descriptive message about changes"
git push
```

---

## Commit Message Templates

Use clear, descriptive commit messages:

```bash
# Initial setup
git commit -m "Initial commit: React Native navigation lab activity"

# Feature additions
git commit -m "Add: HomeScreen component with navigation button"
git commit -m "Add: DetailsScreen with back navigation"
git commit -m "Add: Stack navigator configuration"

# Bug fixes
git commit -m "Fix: Navigation parameter passing"
git commit -m "Fix: Android SDK path configuration"

# Updates
git commit -m "Update: README with student information"
git commit -m "Update: Styling for Home screen"

# Documentation
git commit -m "Docs: Add screenshots to README"
git commit -m "Docs: Update installation instructions"
```

---

## Navigation Code Snippets

### Basic Navigation
```javascript
// Navigate to a screen
navigation.navigate('ScreenName');

// Go back
navigation.goBack();

// Navigate with parameters
navigation.navigate('Details', { 
  itemId: 86, 
  userName: 'John' 
});
```

### Access Parameters
```javascript
// In the destination screen
function DetailsScreen({ route, navigation }) {
  const { itemId, userName } = route.params;
  return (
    <Text>{userName} - Item ID: {itemId}</Text>
  );
}
```

### Navigation Options
```javascript
<Stack.Screen 
  name="Home" 
  component={HomeScreen}
  options={{
    title: 'My Home',
    headerStyle: {
      backgroundColor: '#f4511e',
    },
    headerTintColor: '#fff',
  }}
/>
```

---

## Common Issues & Solutions

### Issue: "ANDROID_HOME not set"
```bash
# macOS/Linux
export ANDROID_HOME="$HOME/Library/Android/sdk"
export PATH="$PATH:$ANDROID_HOME/emulator:$ANDROID_HOME/platform-tools"

# Add to ~/.zprofile for persistence
echo 'export ANDROID_HOME="$HOME/Library/Android/sdk"' >> ~/.zprofile
echo 'export PATH="$PATH:$ANDROID_HOME/emulator:$ANDROID_HOME/platform-tools"' >> ~/.zprofile
source ~/.zprofile
```

### Issue: "Port 8081 already in use"
```bash
# Kill the process
npx kill-port 8081

# Or use a different port
npx expo start --port 8082
```

### Issue: "Unable to resolve module"
```bash
# Clear cache and reinstall
rm -rf node_modules
npm install
npx expo start --clear
```

### Issue: "adb not found"
```bash
# Verify adb is in PATH
which adb

# If not found, check ANDROID_HOME
echo $ANDROID_HOME

# Manually add to PATH
export PATH="$PATH:$ANDROID_HOME/platform-tools"
```

---

## README.md Checklist

Before submitting, ensure your README includes:

- [ ] Student name and ID
- [ ] Course name and date
- [ ] Project description
- [ ] Features list
- [ ] Technologies used
- [ ] Installation instructions
- [ ] Running instructions
- [ ] Project structure
- [ ] Screenshots (minimum 3)
- [ ] Challenges faced
- [ ] Learning outcomes
- [ ] References
- [ ] GitHub repository link

---

## Screenshot Guidelines

### Required Screenshots:

1. **Home Screen**
   - App running on Android emulator
   - Shows navigation button
   - Clear and readable

2. **Details Screen**
   - Navigation in action
   - Shows back button and navigation options
   - Clear and readable

3. **Navigation Flow**
   - Demonstrates transition between screens
   - Can be a GIF or multiple screenshots

### How to Take Screenshots:

**Android Emulator:**
- Click camera icon in emulator toolbar
- Or press `Ctrl + S` (Windows/Linux) / `Cmd + S` (macOS)
- Screenshots saved to: Desktop or Pictures folder

**From VS Code Terminal:**
- Use emulator's screenshot tool
- Save to `screenshots/` folder in project
- Add to Git: `git add screenshots/`

---

## Testing Checklist

Before submission, test all functionality:

### Navigation Tests:
- [ ] Click "Go to Details" from Home → navigates successfully
- [ ] Click "Go Back" from Details → returns to Home
- [ ] Click "Go to Home" from Details → navigates to Home
- [ ] Press hardware back button → goes back
- [ ] Press back on Home screen → exits app
- [ ] Header shows correct screen titles

### Code Quality:
- [ ] No console errors
- [ ] No warnings (except simctl - harmless)
- [ ] Code is properly formatted
- [ ] Components are properly named
- [ ] Styles are organized

### Documentation:
- [ ] README is complete
- [ ] All instructions are clear
- [ ] Screenshots are included
- [ ] Git history is clean

---

## Grading Self-Check

| Criteria | Status | Notes |
|----------|--------|-------|
| Environment Setup | ⬜ | Android SDK working |
| Project Structure | ⬜ | All files present |
| Navigation Works | ⬜ | All flows tested |
| Code Quality | ⬜ | Clean, commented |
| Git Repository | ⬜ | Proper commits |
| README Complete | ⬜ | All sections filled |
| Screenshots | ⬜ | 3+ included |
| Testing | ⬜ | All scenarios pass |

---

## Time Management

Suggested time allocation:

- **Environment Setup:** 30 minutes
- **Project Creation:** 20 minutes
- **Implementation:** 40 minutes
- **Testing:** 30 minutes
- **Documentation:** 30 minutes
- **Git/GitHub:** 20 minutes
- **Total:** ~2.5 hours

---

## Additional Resources

- **React Navigation Playground:** https://reactnavigation.org/docs/getting-started
- **Expo Snacks (Online Editor):** https://snack.expo.dev/
- **React Native Express:** http://www.reactnativeexpress.com/
- **GitHub Markdown Guide:** https://guides.github.com/features/mastering-markdown/

---

## Support Contacts

- **Instructor:** [Add instructor email]
- **Lab Hours:** [Add lab hours]
- **Discussion Forum:** [Add forum link]
- **Course Website:** [Add course website]

---

**Last Updated:** December 2, 2025
