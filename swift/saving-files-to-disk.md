# Saving files to disk

Getting the file path to the location where you should store a file is done
easily with this function:

```swift
private func getDocumentsDirectory() -> URL {
    let paths = FileManager.default.urls(for: .documentDirectory, in: .userDomainMask)
    let documentsDirectory = paths[0]
    return documentsDirectory
}
```
