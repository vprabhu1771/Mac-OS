An Info.plist (Information Property List) is a structured XML text file that contains essential configuration metadata for Apple bundles, such as iOS and macOS apps. It uses a key-value dictionary layout to tell the operating system how to interpret, configure, and secure your app. [1, 2] 
------------------------------
## 1. Where is the Info.plist File?

* In Xcode 13 and newer: By default, new projects do not contain a physical Info.plist file in the file explorer. Instead, Xcode manages these properties behind the scenes. You can configure fields directly by clicking your project root → selecting your Target → navigating to the Info tab. [3, 4] 
* Generating a physical file: If you add a custom key or edit a property inside the Info tab, Xcode will automatically generate a localized Info.plist file in your project directory. [3, 5] 

## 2. Common Keys Used in Info.plist
Xcode presents user-friendly names by default, but the underlying system relies on explicit XML keys. [6] 

| User-Friendly Xcode Name | Underlying Raw XML Key | Purpose |
|---|---|---|
| Bundle display name | CFBundleDisplayName | The actual name displayed under the app icon on the home screen. |
| Bundle identifier | CFBundleIdentifier | The unique ID of your app (e.g., com.company.appname). |
| Bundle version string (short) | CFBundleShortVersionString | The release version shown to users (e.g., 1.0.0). |
| Bundle version | CFBundleVersion | The internal build number (e.g., 42). |
| Privacy - Camera Usage Description | NSCameraUsageDescription | Explains why the app requests permission to use the camera. |
| Privacy - Location When In Use... | NSLocationWhenInUseUsageDescription | Explains why the app requires location access. |

## 3. How to Read/Write Plist Values Programmatically
You can query the values inside your Info.plist file at runtime using Bundle.main.infoDictionary: [7] 
```
// Get the App Version (e.g., "1.0")if let appVersion = Bundle.main.object(forInfoDictionaryKey: "CFBundleShortVersionString") as? String {
    print("App Version is \(appVersion)")
}
// Get the Bundle Identifierif let bundleID = Bundle.main.bundleIdentifier {
    print("Bundle ID is \(bundleID)")
}
```

## 4. Viewing Raw XML Source Code
If Xcode displays the file in its default table format, you can view and edit the raw XML directly: [6] 

   1. Right-click the Info.plist file in the Xcode project navigator.
   2. Hover over Open As.
   3. Select Source Code. [6, 8] 

------------------------------
If you need help with a specific configuration, please let me know:

* Are you trying to add a specific permission (like Camera, Location, or Bluetooth)?
* Are you having trouble locating or generating the physical file?
* Do you need to set up different plist values for Debug vs. Release builds?


[1] [https://developer.apple.com](https://developer.apple.com/documentation/bundleresources/information-property-list)
[2] [https://developer.apple.com](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html)
[3] [https://stackoverflow.com](https://stackoverflow.com/questions/67896404/where-is-info-plist-in-xcode-13-missing-not-inside-project-navigator)
[4] [https://sarunw.com](https://sarunw.com/posts/what-is-info-plist/)
[5] [https://www.youtube.com](https://www.youtube.com/watch?v=_DgvawY5K_0&t=46)
[6] [https://medium.com](https://medium.com/@Dougly/the-info-plist-file-in-xcode-80fa79a1bd08)
[7] [https://www.youtube.com](https://www.youtube.com/watch?v=tTsm-i4iJYA&t=54)
[8] [https://www.youtube.com](https://www.youtube.com/watch?v=uDX6gsRtM14&t=17)
