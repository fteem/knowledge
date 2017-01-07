# Type inference

This means that Swift figures out what data type a variable or constant should be
based on what you put into it. This means:
* you need to put the right thing into your variables otherwise they'll 
  have a different type from what you expect
* you can't change your mind later and try to put an integer into an array
* you only have to give something an explicit type if Swift's inference is wrong

To get you started, here are some example type inferences:

```swift
var score = 0 //This makes an Int (integer), so it holds whole numbers.
var score = 0.0 // This makes a Double, which is one of several ways of holding decimal numbers, e.g. 3.14159.
var score = "hello" // This makes a String, so it holds text.
var score = "" // Even though there's no text in the quote marks, this still makes a String.
var score = ["hello"] // This makes a [String] with one item, so it's an array where every item is a String.
var score = ["hello", "world"] // This makes a [String] with two items, so it's an array where every item is a String.
```

It's preferable to let Swift's type inference do its work whenever possible.
However, if you want to be explicit, you can be:

```swift
var score: Double = 0 
```
Swift sees the 0 so thinks you want an Int, but we're explicitly forcing it to be a Double anyway.

```swift
var score: Float = 0.0
```
Swift sees the 0.0 and thinks you want a Double, but we're explicitly forcing it
to be a Float. I said that Double is one of several ways of holding decimal
numbers, and Float is another. Put simply, Double is a high-precision form of
Float, which means it holds much larger numbers, or alternatively much more
precise numbers.
