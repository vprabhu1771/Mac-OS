Here are more advanced ways to work with the navigation title in SwiftUI, focusing on dynamic titles, styling, and structural patterns.
## 1. Dynamic Titles (Binding)
You can bind the navigation title directly to a string variable or state. This is highly useful when the title depends on user input or API data.
```
struct DynamicTitleView: View {
    @State private var username: String = "Guest User"

    var body: some View {
        NavigationStack {
            VStack(spacing: 20) {
                TextField("Edit profile name", text: $username)
                    .textFieldStyle(.roundedBorder)
                    .padding()
            }
            // Passing a Binding allows the title to update instantly as you type
            .navigationTitle($username) 
        }
    }
}
```
------------------------------
## 2. Customizing Fonts & Colors
SwiftUI does not provide a direct modifier like `.navigationTitleColor()`. Instead, you configure the appearance using the global `UIKit` fallback (`UINavigationBarAppearance`) inside an `init()` method or a `.onAppear` block.
```
struct StyledTitleView: View {
    init() {
        let appearance = UINavigationBarAppearance()
        appearance.configureWithOpaqueBackground()
        
        // Large Title Styling
        appearance.largeTitleTextAttributes = [
            .foregroundColor: UIColor.systemBlue,
            .font: UIFont.boldSystemFont(ofSize: 34)
        ]
        
        // Inline (Scrolled) Title Styling
        appearance.titleTextAttributes = [
            .foregroundColor: UIColor.systemBlue
        ]

        // Apply globally to this navigation stack
        UINavigationBar.appearance().standardAppearance = appearance
        UINavigationBar.appearance().scrollEdgeAppearance = appearance
    }

    var body: some View {
        NavigationStack {
            Text("Scroll down to see the title change")
                .navigationTitle("Styled Title")
        }
    }
}
```
------------------------------
## 3. Hiding the Navigation Title / Bar
If you want to use a completely custom top bar layout, you can hide the system navigation bar altogether while keeping the back button logic intact.
```
Text("Custom View")
    .navigationTitle("Hidden Title")
    .navigationBarHidden(true) // Hides the title space completely
```
------------------------------
## Summary Checklist for Title Visibility

| Property | Mode | Best Used For |
|---|---|---|
| .navigationBarTitleDisplayMode(.large) | Large bold font | Main landing screens, dashboards, settings roots. |
| .navigationBarTitleDisplayMode(.inline) | Small centered font | Deeply nested subviews, detail screens, edit menus. |
| .toolbar { ToolbarItem(placement: .principal) } | Any custom view | Logos, profile pictures, or dual-lined subtitles. |

Would you like to see how to implement search bars inside the navigation title using .searchable(), or do you need help hiding the back button on specific views?

