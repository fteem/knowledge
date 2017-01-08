# Assets

How iOS handles different resolutions of screens and assets?

iOS assets come in the sizes 2x and 3x, which are two times and three times the
size of the layout you created in Interface Builder. This might seem strange,
but it’s a little bit of iOS magic that takes away a huge amount of work from
developers.

Early iOS devices had non-retina screens. This meant a screen resolution of
320x480 pixels, and you could place things exactly where you wanted them – you
asked for 10 pixels in from the left and 10 from the top, and that was what you
got.

With iPhone 4, Apple introduced retina screens that had double the number of
pixels as previous screens. Rather than make you design all your interfaces
twice, Apple automatically switched sizes from pixels to “points” – virtual
pixels. On non-retina devices, a width of 10 points became 10 pixels, but on
retina devices it became 20 pixels. This meant that everything looked the same
size and shape on both devices, with a single layout.

Of course, the whole point of retina screens was that the screen had more
pixels, so everything looked sharper – just resizing everything to be larger
wasn’t enough. So, Apple took things a step further: if you create `hello.png`
that was 200x100 in size, you could also include a file called `hello@2x.png`
that was 400x200 in size – exactly double – and iOS would load the correct one.
So, you write `hello.png` in your code, but iOS knows to look for and load
`hello@2x.png` on retina devices.

More recently, Apple introduced retina HD screens that have a 3x resolution.
These follow the same naming convention: `hello.png` is for non-retina devices,
`hello@2x.png` for retina devices, and `hello@3x` for retina HD devices. You
still just write `hello.png` in your code and user interfaces, and iOS does the rest.

You might think this sounds awfully heavy – why should a non-retina device have
to download apps that include @2x and @3x content that it can’t show? Fortunately,
the App Store uses a technology called **app thinning** that automatically
delivers only the content each device is capable of showing – it strips out the
other assets when the app is being downloaded, so there’s no space wasted.
