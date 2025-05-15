# 🛠 React Expo TypeScript Setup on macOS (with Homebrew)

This guide walks you through setting up a macOS environment to build React Native apps using **Expo with TypeScript**, leveraging **Homebrew** for package management.

---

## 1. 🍺 Install Node.js (via Homebrew)

```bash
brew install node
```

After installation, verify:

```bash
node -v
npm -v
```

---

## 2. 🧶 Install Yarn (via Homebrew)

```bash
brew install yarn
```

Verify:

```bash
yarn -v
```

---

### ⚠️ Important Reminder

Avoid using `sudo` with `npm` or `yarn`.

Running `sudo npm install` may create root-owned files that block your user from accessing npm's cache and cause permission errors. Stick with standard installs unless necessary.

---

## 3. 📦 Install Expo CLI

📌 **Recommended:** Use `npx` instead of a global install.

To start a project without installing globally:

```bash
npx expo start
```

If you prefer a global install:

```bash
npm install -g expo-cli
```

Learn more at: [https://docs.expo.dev/more/expo-cli/](https://docs.expo.dev/more/expo-cli/)

---

## 4. 🧑‍💻 Install Xcode

- Download Xcode from the Mac App Store
- Launch Xcode and accept the license
- Install command line tools:

```bash
xcode-select --install
```

---

## 5. 🤖 Install Android Studio

Download from: [https://developer.android.com/studio](https://developer.android.com/studio)

During setup, ensure the following are installed:

- Android SDK
- Android Emulator
- SDK Command-line Tools

Then:

- Open Android Studio → Preferences → Appearance & Behavior → System Settings → Android SDK
- Note your SDK Location (default: `~/Library/Android/sdk`)

---
### ⚠️ Important Reminder

The .zshrc file is a configuration file for the Z shell (Zsh)

A popular Unix shell that is often used as a more powerful alternative to Bash. 
PATH modifications to include directories for tools like Node.js, Android SDK, or Expo

## 6. 🛠 Configure `.zshrc` for Android SDK

a. Create `.zshrc` if it does not exist:

```bash
touch ~/.zshrc
```

b. Open it:

```bash
open -a TextEdit ~/.zshrc
```

c. Add:

```bash
# Android SDK Path
export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/platform-tools
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
```

d. Apply:

```bash
source ~/.zshrc
```

---

## 7. 📱 Set Up Android Emulator

- Open Android Studio → Device Manager → Create Device
- Select a phone (e.g., Pixel 6) and install a system image
- Launch the emulator

Check with:

```bash
adb devices
```

---

## 8. 🚀 Create and Run a Sample Expo App

```bash
npx create-expo-app myApp -t
cd myApp
npx expo start
```

Use:
- `i` for iOS simulator
- `a` for Android emulator

---

🎥 For the full tutorial walkthrough, subscribe to [MonteyCodes YouTube Channel](https://www.youtube.com/@sergiomontey)




## 🧩 Xcode Not Detected Fix (React Native iOS Build Error)

If you see an error like this when running `npx expo run:ios` or trying to open the iOS simulator:

> **"Command failed: xcrun xcodebuild -workspace... Xcode is not installed or not configured properly."**

### ✅ Step-by-Step Fix:

1. **Ensure Xcode is Fully Installed:**
   - Open the Mac App Store and search for **Xcode**
   - If it says **"Open"**, you're good. If it says **"Get"**, download and install it.

2. **Launch Xcode Once and Agree to Terms:**
   - Open Xcode from the Applications folder
   - Accept the license and install any required components

3. **Manually Set the Developer Path:**

```bash
sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
```

4. **Verify the Current Xcode Path:**

```bash
xcode-select -p
```

Expected output:

```
/Applications/Xcode.app/Contents/Developer
```

5. **Clear Expo Cache and Reinstall Dependencies (Optional):**

```bash
npx expo-cli cache:clear
npm install
# or
yarn install
```

6. **Restart the Metro Bundler and Try Again:**

```bash
npx expo start
npx expo run:ios
```

This should resolve Xcode detection issues for Expo or React Native builds on macOS.
