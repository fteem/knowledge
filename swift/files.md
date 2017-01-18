# Files

## Bundle

Files are always part of the `Bundle` object, which is in fact an `NSBundle` object
under the hood. An NSBundle object helps you access the code and resources in a
bundle directory on disk. 

## File paths

Getting a filepath in the Bundle is done via:

```swift
Bundle.main.path(forResource: "filename", ofType: "type")
```

For example, finding a filepath in a Bundle for a file called `grades.csv`:

```swift
Bundle.main.path(forResource: "grades", ofType: "csv")
```

The signature of the `Bundle.main.path` function is:

```swift
func path(forResource name: String?, ofType ext: String?) -> String?
```

Since it returns an Optional String, using the filepath is usually done in an
if clause:

```swift
if let path = Bundle.main.path(forResource: "grades", ofType: "csv") {
  // use path...
}
```
