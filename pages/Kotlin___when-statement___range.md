- ```kotlin
  when (x) {
      1,2 -> print("x is in the range")
      in validNumbers -> print("x is valid")
      !in 10..20 -> print("x is outside the range")
      else -> print("none of the above")
  }
  ```