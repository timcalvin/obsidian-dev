Fetching data requires multiple steps.

The first step is creating a struct to model the data. Each of the property names must be typed exactly the same as their names appear in JSON, and each of their types must also match the JSON.

For types, Swift has a special data type for storing URLs called **URL**. Also the **Decodable** protocol is responsible for decoding JSON into Swift data. In the example below, all the data types already conform to Decodable. You can also convert Swift structs into JSON and other formats using **Encodable**. You can combine both protocols into one and use **Codable**.

```swift
struct Track: Identifiable, Decodable {
  var id: Int {trackId}
	let trackId: Int
	let artistName: String
	let trackName: String
	let previewUrl: URL
	let artworkUrl100: String
}

struct SearchResult: Decodable {
	let results: [Track]
}
```

Here is an example of how to use this to download data, which uses **async** to tell Swift it can run at the same time as the other UI functions that are running one at a time on the *main actor*. Essentially, Swift is telling the function in the background that it can start some work, and then go to sleep until the results of that work come back. When you call an async function, you must mark it with the **await** keyword, to show you're acknowledging it could go to sleep.

```swift
struct ContentView: View {

	@State private var tracks = [Track]()
	@AppStorage("searchText") var searchText = ""

	func performSearch() async throws {
	  guard let url = URL(string: "https://itunes.apple.com/search?term=\(searchText)&limit=100&entity=song") else { return }

    let (data, _) = try await URLSession.shared.data(from: url)

    let searchResult = try JSONDecoder().decode(SearchResult.self, from: data)

        tracks = searchResult.results
    }

	func startSearch() {
		Task {
			try await performSearch()
		}
	}
}
```

## macOS

Network requests aren't allowed out of the box in macOS. To fix this, select your app under the **TARGETS** list, then select the* **Signing & Capabilities** tab and check the **Outgoing Connections (Client)** checkbox.

## JSON Basics

- Dictionaries are started and ended using { }
- Inside, key strings are in " " followed by : then the *value*
- Arrays are separeted using commas
- The top level has two values, an integer called **resultCount** and an array called **results**

**TIP:** You can paste compressed JSON into a site like https://jsonformatter.curiousconcept.com to see it in a more readable format.