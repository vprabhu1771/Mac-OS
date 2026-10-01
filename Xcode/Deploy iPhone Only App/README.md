Yes. If your Flutter app is designed **only for iPhone**, you can submit it to the Apple App Store as **iPhone-only** and exclude iPad.

In App Store Connect, you can configure the supported device family so the app is available for **iPhone but not iPad**.

### For your Flutter app

In your iOS project, open:

`ios/Runner.xcodeproj` → **Runner** -> **TARGETS** -> **Runner** → **Build Settings** → **Deployment** -> 

Look for **Targeted Device Family**.

Set it to:

**iPhone** only

and make sure **iPad** is not selected.

You can also check `ios/Runner/Info.plist` / Xcode project settings to ensure the device family is not configured to include iPad.
