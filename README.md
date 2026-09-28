# 夜市夾娃娃 3D — Android App

用 Capacitor 把 HTML/three.js 遊戲包成原生 Android App。遊戲本體在 `www/index.html`，three.js 已內建（`www/three.min.js`），離線可玩。

## 方法一：不裝 Android Studio，用 GitHub 雲端打包（推薦）

1. 在 GitHub 建一個新 repo，把這個資料夾整個推上去（`main` 分支）。
2. 推上去後 GitHub Actions 會自動執行 `Build Android APK`，約 5–8 分鐘。
3. 到 repo 的 **Actions** 頁 → 點最新一次執行 → 下方 **Artifacts** 下載 `claw-machine-debug-apk`。
4. 解壓得到 `app-debug.apk`，傳到手機安裝（需允許「安裝未知來源應用程式」）。

## 方法二：本機用 Android Studio 打包

```bash
npm install
npx cap sync android
npx cap open android      # 開啟 Android Studio
```
在 Android Studio 中 **Build → Build Bundle(s) / APK(s) → Build APK(s)**，或直接連接手機按 ▶ 執行。

## 改遊戲內容

改 `www/index.html` 後執行 `npx cap sync android` 再重新打包。

## 上架 Google Play

需要簽名版本：`cd android && ./gradlew bundleRelease`，並在 `android/app/build.gradle` 設定 signingConfig 與 keystore。另外請把 `capacitor.config.json` 裡的 `appId` 改成你自己的套件名稱（例如 `com.yourname.clawmachine`）。
