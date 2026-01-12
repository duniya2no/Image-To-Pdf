# Build Commands for Photo to PDF App

## Prerequisites

1. **Install EAS CLI globally** (if not already installed):
   ```bash
   npm install -g eas-cli
   ```

2. **Login to Expo account**:
   ```bash
   eas login
   ```

3. **Configure project** (first time only):
   ```bash
   eas build:configure
   ```

## Build Commands

### Development Build (for testing)
```bash
# Android
npm run build:android
# or
eas build --platform android --profile development

# iOS
npm run build:ios
# or
eas build --platform ios --profile development
```

### Preview Build (APK for Android, IPA for iOS - for testing)
```bash
# Android APK (can install directly)
npm run build:android:preview
# or
eas build --platform android --profile preview

# iOS (requires Apple Developer account)
npm run build:ios:preview
# or
eas build --platform ios --profile preview
```

### Production Build (for app stores)
```bash
# Android (AAB for Play Store)
npm run build:android:production
# or
eas build --platform android --profile production

# iOS (for App Store)
npm run build:ios:production
# or
eas build --platform ios --profile production

# Both platforms at once
npm run build:all
# or
eas build --platform all --profile production
```

## Alternative: Local Build (Requires Android Studio / Xcode)

### For Android (requires Android Studio):
```bash
# Generate Android project
npx expo prebuild --platform android

# Build APK locally
cd android
./gradlew assembleRelease
# APK will be in: android/app/build/outputs/apk/release/app-release.apk

# Build AAB for Play Store
./gradlew bundleRelease
# AAB will be in: android/app/build/outputs/bundle/release/app-release.aab
```

### For iOS (requires Xcode and macOS):
```bash
# Generate iOS project
npx expo prebuild --platform ios

# Open in Xcode and build
open ios/PhotoToPDF.xcworkspace
# Then build from Xcode (Product > Archive)
```

## Quick Start Commands

```bash
# 1. Navigate to project directory
cd img

# 2. Install dependencies (if not done)
npm install

# 3. Start development server
npm start

# 4. For building, use one of the commands above
```

## Important Notes

- **EAS Build** (recommended): Builds in the cloud, no local setup needed
- **Local Build**: Requires Android Studio (for Android) or Xcode (for iOS)
- **Production builds** require proper app signing certificates
- **Android**: Production builds generate AAB files for Google Play Store
- **iOS**: Production builds require Apple Developer account ($99/year)

## Troubleshooting

If you encounter issues:
1. Make sure you're logged in: `eas whoami`
2. Clear cache: `eas build --clear-cache`
3. Check Expo status: `expo-doctor`
4. Update EAS CLI: `npm install -g eas-cli@latest`
