- Scoping instance
- ```kotlin
  fun main() {
      val squareCabin = SquareCabin(6)
  
      println("\nSquare Cabin\n============")
      println("Capacity: ${squareCabin.capacity}")
      println("Material: ${squareCabin.buildingMaterial}")
      println("Has room? ${squareCabin.hasRoom()}")
      
      // the below code works the same
      
      with(squareCabin) {
      println("\nSquare Cabin\n============")
      println("Capacity: ${capacity}")
      println("Material: ${buildingMaterial}")
      println("Has room? ${hasRoom()}")
  }
  }
  
  
  ```