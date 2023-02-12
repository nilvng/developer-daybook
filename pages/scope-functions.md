page-type:: [[Kotlin]]
source:: https://kotlinlang.org/docs/scope-functions.html#functions

- view holder so that you can access views created from your layout file in code.
-
- you can take advantage of a Kotlin feature called *asynchronous flow* (often just called *flow*) that will allow the DAO to continuously emit data from the database. If an item is inserted, updated, or deleted, the result will be sent back to the fragment. Using a function called `collect(),` you can call `submitList()` using the new value emitted from the flow so that your `ListAdapter` can update the UI based on the new data.