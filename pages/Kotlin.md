icon:: 
tags:: #coding-language

- ## First class function
  collapsed:: true
	- ```kotlin
	  fun double(x: Int) = x * 2
	  ```
- ## Extension function
  collapsed:: true
	- ```kotlin
	  fun Humanoid.walk() {
	    println("walk")
	  }
	  ```
- ## Anonymous lambda
  collapsed:: true
	- ```kotlin
	  val lambda: (Int) -> Int = {num -> double(num)}
	  ```
- ## Data class
  collapsed:: true
	- ```kotlin
	  data class User(val name: String, val age: Int)
	  ```
- ## Singleton
	- ```kotlin
	  object DataProviderManager {
	    
	  }
	  ```