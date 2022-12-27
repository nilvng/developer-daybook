- ```kotlin
  enum class Color {
    RED, GREEN, BLUE
  }
  
  when (getColor()) {
      Color.RED -> println("red")
      Color.GREEN -> println("green")
      Color.BLUE -> println("blue")
      // 'else' is not required because all cases are covered
  }
  
  when (getColor()) {
    Color.RED -> println("red") // no branches for GREEN and BLUE
    else -> println("not red") // 'else' is required
  }
  ```