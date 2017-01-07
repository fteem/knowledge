# Constants and variables

The let keyword defines a constant:

```swift
let theAnswer = 42
```

The `theAnswer` cannot be changed afterwards. This is why anything optional or
weak can't be written using `let`. They need to change during runtime and must
be written using `var`.

The `var` defines an ordinary variable:

What is interesting:

> The value of a constant doesn’t need to be known at compile time, but you must assign it a value exactly once.

Another strange feature:

> You can use almost any character you like for constant and variable names, including Unicode characters:

```swift
let 🐶🐮 = "dogcow"
```
