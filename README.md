# TabView-horizontal-sliding
Horizontal sliding through TabView
# The first part
![IMG_0127](https://github.com/S-way520/TabView-horizontal-sliding/assets/95877651/1a787770-e694-4ed3-a888-92c0f79c8fe6)
# The second part
Code file 1
```swift
import SwiftUI
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```
Code file 2
```swift
import SwiftUI
private let Count = ["One", "Two", "Three", "Four", "Five"]
struct ContentView: View {
    @State private var selected = 0
    var body: some View {
        VStack{
            Text("Tutorial")
                .font(.title2).bold().padding(.leading, 30)
                .padding(.top, 50)
            VStack(alignment: .leading, spacing: 0){
                HStack(spacing: 0){
                    ForEach(0..<Count.count, id: \.self){ index in
                        Text(Count[index])
                            .fontWeight(self.selected == index ? .bold : nil)
                            .font(.subheadline)
                            .foregroundColor(self.selected == index ? .blue : nil)
                            .frame(width: 50, height: 30)
                            .onTapGesture {
                                self.selected = index
                            }
                    }
                }
                HStack{
                    Capsule()
                        .fill(Color.blue)
                        .frame(width: 20, height: 2)
                }
                .frame(width: 50)
                .offset(x: CGFloat(selected * 50))
                .animation(.default, value: selected)
            }
            Spacer()
        }
        Selected
    }
}
extension ContentView {
    private var Selected : some View {
        TabView(selection: $selected) {
            Text("1").tag(0)
            Text("2").tag(1)
            Text("3").tag(2)
            Text("4").tag(3)
            Text("5").tag(4)
        }
        .frame(height: 500)
        .background(.blue)
        .tabViewStyle(.page(indexDisplayMode: .never))
        .padding(.bottom, 30)
    }
}
```
