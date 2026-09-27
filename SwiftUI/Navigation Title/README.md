In SwiftUI, you set the navigation title using the `.navigationTitle(_:)` modifier. [1, 2] 
Crucially, the modifier must be attached to the view inside the `NavigationStack`, not to the container itself. This design allows the title to change dynamically as different views are pushed onto the navigation stack. [3] 
## Basic Implementation
```
import SwiftUI
struct ContentView: View {
    var body: some View {
        NavigationStack {
            VikitView()
                // Attach to the inner view, NOT NavigationStack
                .navigationTitle("Dashboard") 
        }
    }
}
struct VikitView: View {
    var body: some View {
        Text("Main Content Area")
    }
}
```
------------------------------
## Controlling the Display Mode
By default, iOS displays the title in a Large format that shrinks to a smaller Inline format as the user scrolls. You can force a specific layout style using the .navigationBarTitleDisplayMode(_:) modifier: [4, 5] 
```
Text("Content")
    .navigationTitle("Settings")
    .navigationBarTitleDisplayMode(.inline) // Options: .large, .inline, or .automatic
```
------------------------------
## Customizing the Title View (Advanced)
If you need to include images, subtitles, or specific typography, the standard .navigationTitle string is intentionally limited. Instead, you can pass a custom view to the .toolbar principal placement: [6, 7] 
```
NavigationStack {
    VStack {
        Text("Your content here")
    }
    .navigationBarTitleDisplayMode(.inline) // Fits custom view nicely
    .toolbar {
        ToolbarItem(placement: .principal) {
            HStack {
                Image(systemName: "star.fill")
                    .foregroundColor(.yellow)
                Text("Custom Title")
                    .font(.headline)
            }
        }
    }
}
```
## Common Pitfalls

* Wrong Container Placement: Placing .navigationTitle() directly on the NavigationStack { ... } instead of the view inside it will result in the title not appearing at all. [3] 
* Deprecation Notice: Older tutorials use .navigationBarTitle(). This has been deprecated; always prefer .navigationTitle() for modern iOS development. [3, 8] 

Would you like to know how to pass dynamic data to the title from a subview, or are you looking to change the background color of the navigation bar? [8] 

[1] [https://developer.apple.com](https://developer.apple.com/documentation/swiftui/view/navigationtitle%28_:%29-43srq)
[2] [https://www.kodeco.com](https://www.kodeco.com/books/swiftui-cookbook/v1.0/chapters/4-create-a-navigationtitle-in-swiftui)
[3] [https://stackoverflow.com](https://stackoverflow.com/questions/56658948/why-doesnt-the-navigation-title-show-up-using-swiftui)
[4] [https://www.hackingwithswift.com](https://www.hackingwithswift.com/books/ios-swiftui/adding-a-navigation-bar)
[5] [https://www.hackingwithswift.com](https://www.hackingwithswift.com/books/ios-swiftui/customizing-the-navigation-bar-appearance)
[6] [https://stackoverflow.com](https://stackoverflow.com/questions/79625695/customize-navigation-title-in-swiftui)
[7] [https://www.devtechie.com](https://www.devtechie.com/blog/customizing-swiftui-navigation-titles-with-toolbaritem)
[8] [https://stackoverflow.com](https://stackoverflow.com/questions/77664511/how-to-change-navigation-title-color-in-swiftui)
