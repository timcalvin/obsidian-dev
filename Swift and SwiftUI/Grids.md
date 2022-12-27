Grids can be **LazyVGrid** or **LazyHGrid**.

To describe the structure of the grid one column or row at a time, us **GridItem**.

```swift
let gridItems: [GridItem] = [
	GridItem(.fixed(100)),
	GridItem(.fixed(100)),
	GridItem(.fixed(100))
]
```

You then use those in the grid like this:

```swift
LazyVGrid(columns: gridItems) {
	ForEach(1..<100) { i in
		Color.red
	}
}
```

To make the grid more flexible and scrollable, place it in a **ScrollView**.

```swift
ScrollView {
	LazyVGrid(columns: gridItems) {
		ForEach(1..<100) { i in
			Color.red
		}
	}
}
```

You can also choose the direction of scrolling and whether or not to show the scroll indicators.

```swift
ScrollView(.horizontal, .showsIndicators: false) {
	LazyVGrid(columns: gridItems) {
		ForEach(1..<100) { i in
			Color.red
		}
	}
}
```

In addition to *fixed*, **GridItem**s can also come in *flexible* and *adaptive*. With flexible you setup minimum and maximum sizes, and adaptive grid items fill their space automatically.