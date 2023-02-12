source:: [Background work with WorkManager - Kotlin  |  Android Developers](https://developer.android.com/codelabs/android-workmanager?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-kotlin-unit-6-pathway-1%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fandroid-workmanager#0)

-
- ## Introduction
- WorkManager is part of [Android Jetpack](http://d.android.com/jetpack) and an [Architecture Component](http://d.android.com/arch) for background work that needs a combination of opportunistic and guaranteed execution. Opportunistic execution means that WorkManager will do your background work as soon as it can. Guaranteed execution means that WorkManager will take care of the logic to start your work under a variety of situations, even if you navigate away from your app.
- [**`Worker`**](https://developer.android.com/reference/androidx/work/Worker.html): This is where you put the code for the actual work you want to perform in the background. You'll extend this class and override the [`doWork()`](https://developer.android.com/reference/androidx/work/Worker.html#doWork()) method.
- [**`WorkRequest`**](https://developer.android.com/reference/androidx/work/WorkRequest.html)**:** This represents a request to do some work. You'll pass in your `Worker` as part of creating your `WorkRequest`. When making the `WorkRequest` you can also specify things like [`Constraints`](https://developer.android.com/reference/androidx/work/Constraints.html) on when the `Worker` should run.
- [**`WorkManager`**](https://developer.android.com/reference/androidx/work/WorkManager.html)**:** This class actually schedules your `WorkRequest` and makes it run. It schedules `WorkRequest`s in a way that spreads out the load on system resources, while honoring the constraints you specify.
- ## Components
- ### Manager
-
- ### WorkRequest
-
- ### Chain of works