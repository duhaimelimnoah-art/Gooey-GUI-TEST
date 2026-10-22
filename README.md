# Gooey Playground — Android-ready React app

A small, touch-friendly playground with six interactive demos using the real `liquid-gooey` React library.

## Run it locally

Requirements: Node.js 20+ and npm.

```bash
npm install
npm run dev
```

Vite prints a local URL to open in your browser.

## Build for Android

This project uses Capacitor to package the React app as an Android application.

1. Install Node.js and Android Studio on a computer.
2. In this folder, run:

```bash
npm install
npm run build
npx cap add android
npx cap sync android
npx cap open android
```

3. Wait for Android Studio to finish syncing, then choose **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
4. Android Studio will show the APK location when the build finishes. Transfer the APK to your phone and open it to install. Android may ask you to approve installs from that file manager.

For later changes, run `npm run android:sync` before rebuilding.

## Installable web app

The project also includes a web manifest and a small service worker. After deploying the built `dist` folder to an HTTPS host, open the site in Chrome on Android and choose **Install app** or **Add to Home screen**. Browser install prompts depend on the browser and hosting setup.

## About the effect controls

The app uses `Liquid` and `Liquid.Item` from `liquid-gooey`. Blur and contrast control the silhouette filter; color and shadow are live controls. Effect tabs are included as playground controls. The public package's current API focuses primarily on Morph and Move; the tabs are an experimental UI selector, not a guarantee that every named mode is available in every installed version.

Package docs: https://libraries.dev/gooey.html


## Build the APK using only your phone (GitHub cloud build)

This repository includes `.github/workflows/build-android.yml`. You can trigger it on GitHub's cloud computers from a mobile browser—no local computer is required.

1. Sign in to GitHub in your phone browser and create a new repository.
2. Upload the contents of this project ZIP to the repository (extract it first if needed; include the `.github` folder).
3. Open the repository's **Actions** tab and enable Actions if prompted.
4. Select **Build Gooey Playground APK** → **Run workflow**.
5. Wait for the workflow to finish, open the completed run, and download the artifact named `gooey-playground-debug-apk`.
6. Extract the downloaded artifact ZIP on your phone and tap `app-debug.apk` to install it.

This produces a debug APK for testing, not a Play Store release. Cloud builds can fail if a dependency or Android toolchain changes; check the workflow log if that happens.
