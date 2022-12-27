summary:: subview of Activity

-
- ## Lifecycle
	- The lifecycle states and callback methods are quite similar to those used for **activities**. However, keep in mind the difference with the `onCreate()` method. With activities, you would use this method to inflate the layout and bind views.
	- However, in the fragment lifecycle, `onCreate()` is called before the view is created, so you can't inflate the layout here.
	- Instead, you do this in `onCreateView()`. Then, after the view has been created, the `onViewCreated()` method is called, where you can then bind properties to specific views.
	-
- ## Use Cases
	- Using the Navigation component, many apps can manage their entire layout within a single activity, with all navigation occurring between fragments.
	- Fragments make common layout patterns possible, such as master-detail layouts on tablets, or multiple tabs within the same activity.
-
-