Here are the essential Flutter CLI commands for creating a project, running it, and launching the iOS simulator.

### 1. Create a New Flutter Project
To create a new project, use the `flutter create` command followed by your project name. The name should be in lowercase with underscores .
```bash
flutter create my_app
```
You can also use the `--empty` flag to create a project with a minimal `main.dart` file .

### 2. Launch the iOS Simulator
Before running your app, open the iOS Simulator from the command line using:
```bash
open -a Simulator
```
This is the recommended way to start, as it's simpler than setting up a physical device .

### 3. Run Your Flutter App
Navigate into your project's directory and use the `flutter run` command to start the app. The tool will detect the running simulator and install your app on it .
```bash
cd my_app
flutter run
```
If you have multiple devices connected, the `flutter run` command will prompt you to select which one to use.

----
To restrict a new or existing Flutter project to Android and iOS only, use the --platforms flag during creation or use the flutter config command. [1, 2] 
## Option 1: Create a new project with only mobile platforms
When creating a brand-new project, explicitly specify only the android and ios platforms using the --platforms option: [1, 3] 
```bash
flutter create --platforms=android,ios my_app_name
```
(Replace my_app_name with your preferred project name).
## Option 2: Clean up an existing project
If you already created a project that generated folders for other platforms (like web, windows, macos, or linux), you can safely limit it back to mobile: [3] 

   1. Open your project directory and delete the platform folders you do not want (e.g., delete the web, windows, macos, and linux folders manually).
   2. Re-initialize the project using the platforms flag to ensure everything is configured correctly:
   ```bash
   flutter create --platforms=android,ios .
   ```
   
## Option 3: Permanently disable desktop/web globally
If you want all future standard flutter create commands to default strictly to mobile apps without typing the flag every time, disable the other platforms in your global Flutter configuration: [2] 
```bash
flutter config --no-enable-web
flutter config --no-enable-linux-desktop
flutter config --no-enable-macos-desktop
flutter config --no-enable-windows-desktop
```
(If you ever need them back, change --no-enable to --enable). [2] 
------------------------------
Would you like to know how to adjust your configuration to choose Kotlin/Swift over Java/Objective-C for these folders? [3, 4] 

[1] [https://stackoverflow.com](https://stackoverflow.com/questions/52199136/create-a-new-app-for-either-ios-or-android-using-flutter)
[2] [https://stackoverflow.com](https://stackoverflow.com/questions/63119667/how-to-create-flutter-project-only-for-only-android-and-ios-even-if-web-support)
[3] [https://docs.flutter.dev](https://docs.flutter.dev/packages-and-plugins/developing-packages)
[4] [https://stackoverflow.com](https://stackoverflow.com/questions/53294148/recreate-flutters-ios-and-android-folder-with-swift-and-kotlin)
