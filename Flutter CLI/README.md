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
