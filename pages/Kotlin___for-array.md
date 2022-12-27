- ```kotlin
  for (i in array.indices) {
      println(array[i])
  }
  
  for ((index, value) in array.withIndex()) {
      println("the element at $index is $value")
  }
  ```
-