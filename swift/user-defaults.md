# User Defaults

User defaults is a tiny database that stores key-value pairs. The keys are strings
and the values can be `Bool`, `Float`, `Double`, `Int`, `String`, or `URL`, but
you can also write more complex types such as arrays, dictionaries and `Date` –
and even Data values.

From the documentation:

> The NSUserDefaults class provides a programmatic interface for interacting
> with the defaults system. The defaults system allows an application to
> customize its behavior to match a user’s preferences. For example, you can
> allow users to determine what units of measurement your application displays
> or how often documents are automatically saved. Applications record such
> preferences by assigning values to a set of parameters in a user’s defaults
> database. The parameters are referred to as defaults since they’re commonly
> used to determine an application’s default state at startup or the way it acts
> by default.

## Writing to `UserDefaults`

Writing can be done in the following way:

```swift
let defaults = UserDefaults.standard
defaults.set(25, forKey: "Age")
defaults.set(true, forKey: "UseTouchID")
defaults.set(CGFloat.pi, forKey: "Pi")
```

### Rules about writing

The rules are very simple:

1. All your data types must be one of the following: `boolean`, `integer`, 
   `float`, `double`, `string`, `array`, `dictionary`, `Date`, or a class that fits rule 2.
2. If your data type is a class, it must conform to the `NSCoding` protocol,
   which is used for archiving object graphs.
3. If your data type is an array or dictionary, all the keys and values must
   match rule 1 or rule 2.

This basically means that any class whose objects should be saved in `UserDefaults`
should implement the `NSCoding` protocol. `Struct`s implement it by default.

## Reading from `UserDefaults`

When you're reading values from `UserDefaults` you need to check the return type
carefully to ensure you know what you're getting. Here's what you need to know:

- `integer(forKey:)` returns an integer if the key existed, or 0 if not.
- `bool(forKey:)` returns a boolean if the key existed, or false if not.
- `float(forKey:)` returns a float if the key existed, or 0.0 if not.
- `double(forKey:)` returns a double if the key existed, or 0.0 if not.
- `object(forKey:)` returns `Any?` so you need to conditionally typecast it to your data type.

Reading is done:

```swift
let array = defaults.object(forKey: "SavedArray") as? [String] ?? [String]()
```

## Encoding objects/structs before writing

All objects or structs have to be encoded before they are written. This is done
via the `NSKeyedArchiver` class, using it's `archivedData(withRootObject:)` static
function:

```swift
// The data do be saved
var names = ['Ilija', 'John', 'Jane']
// Encoding...
let savedData = NSKeyedArchiver.archivedData(withRootObject: names)
// Saving
let defaults = UserDefaults.standard
defaults.set(savedData, forKey: "names")
```

## Decoding object/structs

All data that needs to be retrieved from the `UserDefaults` needs to be
decoded (unarchived) using `NSKeyedUnarchiver.unarchiveObject(with:)` function:

```swift
var names = [String]()
let defaults = UserDefaults.standard

if let savedNames = defaults.object(forKey: "names") as? Data {
    names = NSKeyedUnarchiver.unarchiveObject(with: savedNames) as! [String]
}
```
