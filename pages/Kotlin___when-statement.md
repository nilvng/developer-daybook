- `when` defines a conditional expression with multiple branches. It is similar to the `switch`statement in C-like languages
- ## Basic
- ```
  fun main() {
      cases("Hello")
      cases(1)
      cases(0L)
      cases(MyClass())
      cases("hello")
  }
  
  fun cases(obj: Any) {                                
      when (obj) {                                     // 1   
          1 -> println("One")                          // 2
          "Hello" -> println("Greeting")               // 3
          is Long -> println("Long")                   // 4
          !is String -> println("Not a string")        // 5
          else -> println("Unknown")                   // 6
      }   
  }
  ```
- ## When expression
- ```kotlin
  fun main() {
      println(whenAssign("Hello"))
      println(whenAssign(3.4))
      println(whenAssign(1))
      println(whenAssign(MyClass()))
  }
  
  fun whenAssign(obj: Any): Any {
      val result = when (obj) {                   // 1
          1 -> "one"                              // 2
          "Hello" -> 1                            // 3
          is Long -> false                        // 4
          else -> 42                              // 5
      }
      return result
  }
  ```