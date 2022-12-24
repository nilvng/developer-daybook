icon:: 
alias:: Kotlin

-
- ## First class function
	- ```kotlin
	  fun double(x: Int) = x * 2
	  ```
- ## Extension function
	- ```kotlin
	  fun Humanoid.walk() {
	    println("walk")
	  }
	  ```
- ## Anonymous lambda
	- ```kotlin
	  val lambda: (Int) -> Int = {num -> double(num)}
	  ```
- ## Data class
	- ```kotlin
	  data class User(val name: String, val age: Int)
	  ```