# Dayline: get the Android APK

The app is already written (www/index.html). Pick ONE way to turn it into an APK.

## Way A: GitHub builds it for you (no Android Studio, no installs)

1. Make a free account at github.com, then create a new repository named dayline-app (Private is fine).
2. Unzip this folder. In your new repository choose Add file > Upload files. Drag in
   everything you can see inside the unzipped folder (the www folder, capacitor.config.json,
   package.json, build-apk.yml). Click Commit changes.
3. Still in the repository, choose Add file > Create new file. In the name box type exactly:
       .github/workflows/build-apk.yml
   (typing the slashes creates the folders). Open build-apk.yml from this folder in any text
   editor, copy everything, paste it into the big box, and click Commit changes.
4. Open the Actions tab. Click "Build Android APK" on the left, then Run workflow (green button).
   Wait 5 to 10 minutes until the run shows a green tick.
5. Click the finished run, scroll to Artifacts, and download Dayline-APK. Unzip it to get app-debug.apk.
6. Send app-debug.apk to your phone (Google Drive, email or USB). Open it, allow "install
   unknown apps" when asked, and tap Install. If Play Protect warns about the app, tap
   More details > Install anyway. It warns because the app is not from the Play Store.

If a run fails (red cross), open it, copy the error text from the failed step, and send it to Claude.

## Way B: Android Studio on your MacBook

1. Install Node.js (LTS) and Android Studio. Open Android Studio once so it installs the Android SDK.
2. In Terminal, inside this folder:
       npm install @capacitor/core@7 @capacitor/cli@7 @capacitor/android@7
       npx cap add android
       npx cap sync android
       npx cap open android
3. In Android Studio wait for Gradle to finish, then Build > Build Bundle(s) / APK(s) > Build APK(s).
4. Click "locate". The file is app-debug.apk. Install it as in step 6 above.

## Notes
- Data is saved inside the app on that phone only. It does not sync with your MacBook or the web link.
- To change the app later, edit www/index.html and build again.
- app-debug.apk is for your own use. Publishing on the Play Store needs a signed release build.
