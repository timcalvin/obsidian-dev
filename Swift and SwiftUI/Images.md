## Remote Images

To load images from a URL use **AsyncImage**.

```swift
AsyncImage(url: track.artworkURL)
```

To have more control and put a placeholder while loading try the following.

```swift
AsyncImage(url: track.artworkURL) { image in
	image.resizable()
} placeholder: {
	ProgressView()
}
.frame(width: 150, height: 150)
```