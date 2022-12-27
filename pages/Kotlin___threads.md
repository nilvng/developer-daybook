- ```kotlin
  override fun onCreate(savedInstanceState: Bundle?) { // Main Thread
      super.onCreate(savedInstanceState)
      val helloTextView: TextView = findViewById(R.id.hello_world)
      helloTextView.text = "Hello, debugging!"
      setContentView(R.layout.activity_main)
      division()
  }
  
  private fun division() {
     val numerator = 60
     var denominator = 4
     thread(start = true) { // fork new thread so won't block Main Thread
        repeat(4) {
           Thread.sleep(3000)
           runOnUiThread { // return to Main Thread
              findViewById<TextView>(R.id.division_textview).setText("${numerator / denominator}")
              denominator--
           }
        }
     }
  }
  ```