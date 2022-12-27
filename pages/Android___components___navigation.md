- ## Navigation Graph
- ## Intent
- ## SafeArg
-
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
-