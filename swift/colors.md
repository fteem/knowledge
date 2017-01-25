# Colors

## Creating & using custom colors

Easy as:

```swift
let btnColor = UIColor(hue: 0.5861, saturation: 1, brightness: 1, alpha: 1.0)
```

Then, we can reuse the color in any function that takes `UIColor` as an argument.
For example:

```swift
someButton.setTitleColor(btnColor, for: .normal)
```
