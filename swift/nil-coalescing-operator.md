# Nil-Coalescing Operator

The *nil-coalescing* operator (`a ?? b`) unwraps an optional `a` if it contains
a value, or returns a default value `b` if a is nil. The expression a is always
of an optional type. The expression `b` must match the type that is stored inside `a`.

The *nil-coalescing* operator is shorthand for the code below:

```swift
a != nil ? a! : b
```

The code above uses the ternary conditional operator and forced unwrapping (`a!`)
to access the value wrapped inside `a` when `a` is not `nil`, and to return `b`
otherwise. The *nil-coalescing* operator provides a more elegant way to
encapsulate this conditional checking and unwrapping in a concise and readable form.

```
NOTE

If the value of a is non-nil, the value of b is not evaluated. This is known as
short-circuit evaluation.
```

The example below uses the nil-coalescing operator to choose between a default color name and an optional user-defined color name:

```swift
let defaultColorName = "red"
var userDefinedColorName: String?   // defaults to nil
 
 var colorNameToUse = userDefinedColorName ?? defaultColorName
 // userDefinedColorName is nil, so colorNameToUse is set to the default of "red"
 ```

The `userDefinedColorName` variable is defined as an optional `String`, with a
default value of `nil`. Because `userDefinedColorName` is of an optional type,
you can use the *nil-coalescing* operator to consider its value. In the example
above, the operator is used to determine an initial value for a `String` variable
called `colorNameToUse`. Because `userDefinedColorName` is `nil`, the expression
`userDefinedColorName ?? defaultColorName` returns the value of `defaultColorName`,
or `red`.

If you assign a non-nil value to `userDefinedColorName` and perform the
nil-coalescing operator check again, the value wrapped inside `userDefinedColorName`
is used instead of the default:

```swift
userDefinedColorName = "green"
colorNameToUse = userDefinedColorName ?? defaultColorName
// userDefinedColorName is not nil, so colorNameToUse is set to "green"
```


Text taken from: [Apple's documentation on the nil-coalescing operator](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/BasicOperators.html#//apple_ref/doc/uid/TP40014097-CH6-ID72)
