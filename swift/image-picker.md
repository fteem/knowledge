# Image picker

Picking an image from camera or the gallery is done using an instance of the
`UIImagePickerController` class. From the documentation:

> The UIImagePickerController class manages customizable, system-supplied user
> interfaces for taking pictures and movies on supported devices, and for
> choosing saved images and movies for use in your app. An image picker
> controller manages user interactions and delivers the results of those
> interactions to a delegate object.

## Using it

Using it resembles a `UIAlertController` - it needs to be instantiated,
configured and `present`ed:

```swift
let picker = UIImagePickerController()
```

### Editing

If you would like the image picker to allow image cropping, there's the
`allowsEditing` Bool that can be configured:

```swift
picker.allowsEditing = true/false
```

### Receiving events

To receive events, such as "the image has been selected", the `UIImagePickerController`
requires a `delegate` - a class that receives notifications when the user picks
an image or movie, or exits the picker interface.

This is done via:

```swift
picker.delegate = self
```

In this example, `self` can be a `ViewController`. The most important thing is
that the delegate object must implement the `UIImagePickerControllerDelegate`
protocol.

### Setting the source

There are three sources that the `UIImagePickerController` supports: camera,
photo library and saved photos album. The `enum` `UIImagePickerControllerSourceType`
contains all of these sources:
- `UIImagePickerControllerSourceType.camera`
- `UIImagePickerControllerSourceType.photoLibrary`
- `UIImagePickerControllerSourceType.savedPhotosAlbum`

Setting the source is done via:

```swift
picker.sourceType = UIImagePickerControllerSourceType.photoLibrary
```

Since simulators don't have cameras (or the user might not give out camera access
to the application), it's best to check if the source is available before
using it:

```swift
if UIImagePickerController.isSourceTypeAvailable(UIImagePickerControllerSourceType.camera) {
    picker.sourceType = UIImagePickerControllerSourceType.camera
} else {
    picker.sourceType = UIImagePickerControllerSourceType.photoLibrary
}
```

### Present

To present (show on screen) this controller:

```swift
present(picker, animated: true)
```

## Handling the chosen media

Since the controller which will hold the `UIImagePickerController` instance and
behaviour implements the `UIImagePickerControllerDelegate` protocol, it has to
implement a function that will handle the chosen file:

```swift
func imagePickerController(_ picker: UIImagePickerController, didFinishPickingMediaWithInfo info: [String : Any]) {
    // `info` is a Dictionary that contains the image and metadata
    guard let image = info[UIImagePickerControllerEditedImage] as? UIImage else { return }

    // Do something with the image...
    if let jpegData = UIImageJPEGRepresentation(image, 80) {
        try? jpegData.write(to: someImagePath)
    }

    // Dismiss the image picker controller
    dismiss(animated: true)
}
```
