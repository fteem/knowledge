# Alerts

Done by using `UIAlertController`. From the doc:

> A `UIAlertController`object displays an alert message to the user. This class
> replaces the `UIActionSheet` and `UIAlertView` classes for displaying alerts.
> After configuring the alert controller with the actions and style you want,
> present it using the `present(_:animated:completion:)`  method.

## Creating and presenting

Created using:

```swift
let alertControler = UIAlertController(
    title: "Some title",
    message: "This is the message, OK?",
    preferredStyle: {.alert, .actionSheet}
)
```

An an action to the `UIAlertController`:

```swift
alertController.addAction(
    UIAlertAction(
        title: "Action title",
        style: {.default, .cancel, .destructive},
        handler: handlerHere
    )
)
```

Presenting:

```swift
present(alertController, animated: true)
````
