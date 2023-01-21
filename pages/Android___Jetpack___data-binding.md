summary:: binding code to view in layout.xml

- ```kotlin
  android:text="@{gameViewModel.currentScrambledWord}"
  ```
- ## Advantages to [[Android/Jetpack/view-binding]]
- lets you remove many UI framework calls in your activities, making them simpler and easier to maintain.
- This can also improve your app's performance and help prevent memory leaks and null pointer exceptions.
- ## Steps
	- In the `build.gradle(Module)`
		- ``` xml
		  buildFeatures {
		     dataBinding = true
		  }
		  ```
	- apply the `kotlin-kapt` plugin.
		- ``` xml
		  plugins {
		     id 'com.android.application'
		     id 'kotlin-android'
		     id 'kotlin-kapt'
		  }
		  ```
		- Above steps auto generates a binding class for every layout XML file in the app. If the layout file name is `activity_main.xml` then your autogen class will be called `ActivityMainBinding`.
	- Open `game_fragment.xml`, select **code** tab
		- Right-click the root element (`ScrollView`), select **Show Context Actions** > **Convert to data binding layout**
	- Replace this from [[Android/Jetpack/view-binding]]
		- ``` kotlin
		  binding = GameFragmentBinding.inflate(inflater, container, false)
		  ```
		- with:
		- ```kotlin
		  binding = DataBindingUtil.inflate(inflater, R.layout.game_fragment, container, false)
		  ```
	- ```kotlin
	  override fun onViewCreated(view: View, savedInstanceState: Bundle?) {
	   super.onViewCreated(view, savedInstanceState)
	  - binding.gameViewModel = viewModel
	  - binding.maxNoOfWords = MAX_NO_OF_WORDS
	  ...
	  }
	  ```
	- The `LiveData` is lifecycle-aware observable, so you have to pass the lifecycle owner to the layout. In the `GameFragment`, inside the `onViewCreated()`method, below the initialization of the binding variables, add the following code
		- ```kotlin
		  // Specify the fragment view as the lifecycle owner of the binding.
		     // This is used so that the binding can observe LiveData updates
		     binding.lifecycleOwner = viewLifecycleOwner
		  ```
	- ```xml
	  <TextView
	     android:id="@+id/word_count"
	     ...
	     android:text="@{@string/word_count(gameViewModel.currentWordCount, maxNoOfWords)}"
	     .../>
	  <TextView
	     android:id="@+id/score"
	     ...
	     android:text="@{@string/score(gameViewModel.score)}"
	     ... />
	  ```