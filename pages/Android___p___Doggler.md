summary:: collection view of puppies

- ## Tasks
	- DONE layout of vertical and horizontal
	- DONE button (provided)
	- DONE layout of grid
	- DONE implement the adapter
-
- ## Placeholder for preview
	- TextView: `tools:text=""`
	- ImageView: `tools:src="@drawable/name"`
- ## Spacing between views
	- `android:layout_marginVertical`
	- or `android:layout_margin` for all side
	- or `android:layout_marginEnd` for right side
- ## Text styles
	- `textAppearance`
- ## Adapter
	- ```kotlin
	  class DogCardAdapter(
	      private val context: Context?,
	      private val layout: Int
	  ): RecyclerView.Adapter<DogCardAdapter.DogCardViewHolder>() {}
	  ```
	- ### ViewHolder: holding all  reference to subviews
		- ```kotlin
		      class ItemViewHolder(
		          private val view: View // root view
		          ): RecyclerView.ViewHolder(view) {
		          val textView: TextView = view.findViewById(R.id.item_title)
		          val imageView: ImageView = view.findViewById(R.id.item_image)
		      }
		  ```
	- ### `onCreateViewHolder()`
		- ```kotlin
		  override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ItemViewHolder {
		          val layoutType = when (layout) {
		              Layout.GRID -> R.layout.grid_list_item
		              else -> R.layout.vertical_horizontal_list_item
		          }
		  
		          // TODO Inflate the layout
		          val adapterLayout = LayoutInflater.from(parent.context)
		              .inflate(layoutType,parent,false)
		   
		          return DogCardViewHolder(adapterLayout)
		  ```
	- ### `onBindViewHolder()` to set data in each of the recycler view cards
		- ```kotlin
		      override fun onBindViewHolder(holder: ItemViewHolder, position: Int) {
		          val item = dataset[position]
		          holder.textView.text = context.resources.getString(item.stringResourceId)
		          holder.imageView.setImageResource(item.imageResourceId)
		      }
		  ```
-
- ## Activity
	- ### Main Activity
	  collapsed:: true
		- bind event of buttons
			- ```kotlin
			  override fun onCreate(savedInstanceState: Bundle?) {
			    super.onCreate(savedInstanceState)
			    // Setup view binding
			    binding = ActivityMainBinding.inflate(layoutInflater)
			    setContentView(binding.root)
			    
			   // Launch the VerticalListActivity on verticalBtn click
			    binding.verticalBtn.setOnClickListener {launchVertical()}
			    
			    // Launch the HorizontalListActivity on horizontalBtn click
			    binding.horizontalBtn.setOnClickListener{ launchHorizontal() }
			  
			    // Launch the GridListActivity on gridBtn click
			    binding.gridBtn.setOnClickListener {launchGrid()}
			  }
			  ```
		- launch another activity
			- ```kotlin
			  private fun launchVertical() {
			    listIntent = Intent(this, VerticalListActivity::class.*java*)
			    startActivity(listIntent)
			  }
			  ```
	- ### Horizontal Activity
		- ```kotlin
		  
		  class HorizontalListActivity : AppCompatActivity() {
		  
		      private lateinit var binding: ActivityHorizontalListBinding
		  
		      override fun onCreate(savedInstanceState: Bundle?) {
		          super.onCreate(savedInstanceState)
		          binding = ActivityHorizontalListBinding.inflate(layoutInflater)
		          setContentView(binding.root)
		  
		          binding.horizontalRecyclerView.adapter = DogCardAdapter(
		              applicationContext,
		              Layout.HORIZONTAL
		          )
		  
		          // Specify fixed size to improve performance
		          binding.horizontalRecyclerView.setHasFixedSize(true)
		  
		          // Enable up button for backward navigation
		          supportActionBar?.setDisplayHomeAsUpEnabled(true)
		      }
		  }
		  ```