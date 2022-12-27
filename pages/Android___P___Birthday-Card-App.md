alias:: Mobi-Birthday Card App

- ## Learning Outcomes
	- What are user interface elements, such as `Views` and `ViewGroups`.
	- How to display text in a `TextView` in an app.
	- How to set attributes, such as text, font, and margin on a `TextView`.
	- How to add an image or photo to your Android app.
	- How to display an image in your app using an `ImageView`.
	- How to extract text into a string resource to make it easier to translate your app and to reuse strings.
	- How to make your app usable for the largest number of people
- ## Views
	- in `res/layouts/main.xml`
	- > The unit for margins and other distances in the UI is *density-independent pixels* (dp). It's like centimeters or inches, but for distances on a screen. Android translates this value to the appropriate number of real pixels for each device. As a baseline, 1dp is about 1/160th of an inch, but may be bigger or smaller for some devices.
	- > **sp** is a unit of measure for the font size. UI elements in Android apps use two different units of measurement, *density-independent pixels* (**dp**) which you used earlier for the layout, and *scalable pixels* (**sp**) which is used when setting the size of text. By default, sp is the same size as dp, but it resizes based on the user's preferred text size.
- ## Summary
	- The **Layout Editor** helps you create the UI for your Android app.
	- Almost everything you see on the screen of your app is a `View`.
	- A `TextView` is a UI element for displaying text in your app.
	- A `ConstraintLayout` is a container for other UI elements.
	- `Views` need to be constrained horizontally and vertically within a `ConstraintLayout`.
	- One way to position a `View` is with a margin.
	- A margin says how far a `View` is from an edge of the container it's in.
	- You can set attributes on a `TextView` like the font, text size, and color.
	- The **Resource Manager** in Android Studio helps you add and organize your images and other resources.
	- An `ImageView` is a UI element for displaying images in your app.
	- `ImageViews` should have a content description to help make your app more accessible.
	- Text that is shown to the user like the birthday greeting should be extracted into a string resource to make it easier to translate your app into other languages.