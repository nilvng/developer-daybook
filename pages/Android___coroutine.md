summary::  Background thread
source:: [Android Developer - Coroutine](https://developer.android.com/kotlin/coroutines)

## Sending Network requests
collapsed:: true
	- ```kotlin
	  class LoginViewModel(
	    private val loginRepository: LoginRepository
	  ): ViewModel() {
	  - fun login(username: String, token: String) {
	        // Create a new coroutine to move the execution off the UI thread
	        viewModelScope.launch(Dispatchers.IO) {
	            val jsonBody = "{ username: \"$username\", token: \"$token\"}"
	            loginRepository.makeLoginRequest(jsonBody)
	        }
	    }
	  }
	  ```
		- `viewModelScope` is a predefined `CoroutineScope` that is included with the `ViewModel` KTX extensions. Note that all coroutines must run in a scope. A `CoroutineScope` manages one or more related coroutines.
		- `launch` is a function that creates a coroutine and dispatches the execution of its function body to the corresponding dispatcher.
		- `Dispatchers.IO` indicates that this coroutine should be executed on a thread reserved for I/O operations.
	- Since this coroutine is started with `viewModelScope`, it is executed in the scope of the `ViewModel`. If the `ViewModel` is destroyed because the user is navigating away from the screen, `viewModelScope` is automatically cancelled, and **all running coroutines are canceled** as well.
	- Better approach, make `makeLoginRequest` run in background
		- Once the `withContext` block finishes, the coroutine in `login()` resumes execution *on the main thread* with the result of the network request.
		- ```kotlin
		  wo.Eclass LoginRepository(...) {
		    ...
		    suspend fun makeLoginRequest(
		        jsonBody: String
		    ): Result<LoginResponse> {
		  - // Move the execution of the coroutine to the I/O dispatcher
		        return withContext(Dispatchers.IO) {
		            // Blocking network request code
		        }
		    }
		  }
		  class LoginViewModel(
		      private val loginRepository: LoginRepository
		  ): ViewModel() {
		  
		      fun login(username: String, token: String) {
		  
		          // Create a new coroutine on the UI thread
		          viewModelScope.launch {
		              val jsonBody = "{ username: \"$username\", token: \"$token\"}"
		  
		              // Make the network call and suspend execution until it finishes
		              val result = try {
		                loginRepository.makeLoginRequest(jsonBody)
		              } catch (e: Exception) {
		                Result.Error("Network request failed")
		              }
		  
		              // Display result of the network request to the user
		              when (result) {
		                  is Result.Success<LoginResponse> -> // Happy path
		                  else -> // Show error in UI
		              }
		          }
		      }
		  }
		  ```
- ## Basics
	- | Elements ----------------- | description |
	  |---|---|
	  | Job | A cancelable unit of work, such as one created with the `launch()` function. |
	  | CoroutineScope | Functions used to create new coroutines such as `launch()` and `async()` extend `CoroutineScope`. |
	  | Dispatcher | Determines the thread the coroutine will use. The `Main` dispatcher will always run coroutines on the main thread, while dispatchers like `Default`, `IO`, or `Unconfined` will use other threads. |
	- ## Launch()
	- collapsed:: true
	  ```kotlin
	  import kotlinx.coroutines.*
	  - fun main() {
	    repeat(3) {
	        GlobalScope.launch {
	            println("Hi from ${Thread.currentThread()}")
	        }
	    }
	  }
	  ```
		- Global Scope using the default Dispatcher aka Main Thread. The `GlobalScope` allows any coroutines in it to run as long as the app is running
	- `suspend` keyword. Suspend signals that a block of code or function can be paused or resumed.
		- the `suspend` keyword. The reason is that it calls `delay()`, which is also a `suspend` function. Whenever a function calls another `suspend` function, then it should also be a `suspend` function.
	- ## runBlocking()
		- starts a new coroutine and blocks the current thread until completion
	- ## Async, await
		- ```
		  fun main() {
		      runBlocking {
		          val num1 = async { getValue() }
		          val num2 = async { getValue() }
		          println("result of num1 + num2 is ${num1.await() + num2.await()}")
		      }
		  }
		  ```
	-
-
	-