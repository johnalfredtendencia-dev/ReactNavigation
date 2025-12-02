# React Native Navigation Project Setup

## Current Status
- [x] Verify that the copilot-instructions.md file in the .github directory is created.
- [x] Clarify Project Requirements
- [x] Scaffold the Project
- [x] Customize the Project
- [x] Install Required Extensions
- [x] Compile the Project
- [x] Create and Run Task
- [x] Launch the Project
- [x] Ensure Documentation is Complete
- [x] Create Lab Activity Instructions

## Project Type
React Native Expo project with React Navigation - CS Lab Activity

## Purpose
This is a laboratory activity for Computer Science students learning mobile application development with React Native. The project demonstrates stack navigation and includes comprehensive documentation for institutional use.

## Setup Instructions
Simple navigation example following React Native documentation, configured for Android development.

## Project Structure
- `App.js` - Main app with NavigationContainer and Stack Navigator
- `screens/HomeScreen.js` - Home screen with navigation to Details
- `screens/DetailsScreen.js` - Details screen with back navigation
- `package.json` - Dependencies including React Navigation
- `README.md` - Student-focused documentation with submission guidelines
- `LAB_ACTIVITY_INSTRUCTIONS.md` - Complete lab instructions for instructors and students
- `QUICK_REFERENCE.md` - Quick reference guide for common tasks

## How to Run
```bash
npm start        # Start Expo development server
npm run ios      # Run on iOS simulator
npm run android  # Run on Android emulator
npm run web      # Run in web browser
```

## Environment Configuration
Android SDK configured with ANDROID_HOME and PATH variables set in ~/.zprofile for persistent use.

## Lab Activity Features
- Step-by-step instructions for students
- Environment setup guide (Android Studio, SDK, emulator)
- Git workflow and GitHub repository setup
- Grading rubric (100 points + 10 bonus)
- Troubleshooting guide
- Code snippets and examples
- Testing checklist
- Screenshot guidelines
- Submission requirements

## Student Deliverables
1. Working React Native app with navigation
2. GitHub repository with all code
3. README.md with student information and documentation
4. Screenshots (minimum 3)
5. Lab report (PDF)
6. Optional: Screen recording demonstration

## Quick Commands for Students
```bash
# Install dependencies
npm install

# Run on Android emulator
npm run android

# Git workflow
git init
git add .
git commit -m "Initial commit: React Native navigation lab activity"
git remote add origin <GITHUB_URL>
git branch -M main
git push -u origin main
```

## Resources
- Full lab instructions: `LAB_ACTIVITY_INSTRUCTIONS.md`
- Quick reference: `QUICK_REFERENCE.md`
- Student README template: `README.md`
