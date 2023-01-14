source:: [Android Basics - Navigation Components](https://developer.android.com/codelabs/basic-android-kotlin-training-fragments-navigation-component?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-kotlin-unit-3-pathway-2%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-training-fragments-navigation-component#6)

- ## Steps
	- Include the [Jetpack Navigation library](https://developer.android.com/jetpack/androidx/releases/navigation)
	- Add a `NavHost` to the activity
	- Create a navigation graph
	- Add fragment destinations to the navigation graph
- ## Navigation Graph
- ## Intent
- ## SafeArg
-
- ## Pieces
	- `NavHostFragment`: container for destinations
	- `NavController`: conducts navigation
		- ```kotlin
		  holder.view.findNavController().navigate(action)
		  ```
	- `NavigationView`: Menu for `DrawerLayout`
	- `NavigationUI`: Updates content outside `NavHostFragment`
		- `NavigationView`
		- `BottomNavBar`
	-
- ## Enable back button
	- ```kotlin
	  override fun onSupportNavigateUp(): Boolean {
	     return navController.navigateUp() || super.onSupportNavigateUp()
	  }
	  ```
- setting `defaultNavHost` to `true` in the XML
-