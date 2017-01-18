# Arrays

## Shuffling arrays

Easiest way to do is to use `GameplayKit`:

> GameplayKit is an object-oriented framework that provides foundational tools
> and technologies for building games.

`GameplayKit` has `GKRandomSource` which is the superclass for all basic
randomization classes. We can utilise this class to randomise, via:

```swift
GKRandomSource.sharedRandom().arrayByShufflingObjects(in: array) as! [Type]
```

`sharedRandom` is a function that returns a shared instance that shares a
system-wide random source. It returns `GKRandomSource`.

`arrayByShufflingObjects` takes an array as an argument and shuffles it. Since
the signature of the function is:

```swift
func arrayByShufflingObjects(in array: [Any]) -> [Any]
```

it returns AnyObject so the `[Any]` (array of Any object) has to be casted to
a `[String]` (array of Strings).

### Example/Usage

```swift
let names = ["Ilija", "John", "Jane"]

GKRandomSource.sharedRandom().arrayByShufflingObjects(in: names) as! [String]
// ["Jane", "Ilija", "John"]
```
