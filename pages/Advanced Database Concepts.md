- tags: #backend
- ## Parameterised Select
-
- ## Indexing Tables
	- Types:
	  collapsed:: true
		- Hashing
		- B-tree
		- Bitmap
		- specialised index
	- ### Balanced Tree
		- Binary tree
		- Complexity: logn, n is depth of tree
		- High number of values in a column (high cardinality)
		- re-balance as needed
	- ### Hash
		- Map data to hash value
		- no order preserved
		- Only used for '='
		- smaller size and as fast as B-tree
	- ### Covering index
	- ### Bitmap
- ## Bulk loading and indexing
-
- ## Object-Relational Mapping
-
- ## Scalability - Partitioning
- ### Range partitioning
	- ```sql
	  CREATE TABLE menu_data
	        (order_id int not null,
	         order_date date not null,
	         order_item text not null,
	         order_type varchar)
	  PARTITION BY RANGE(order_date);
	  
	  CREATE TABLE order_date_w1 PARTITION OF menu_data
	  FOR VALUE FROM ('2020-01-01') TO ('2020-01-08');
	  
	  CREATE TABLE order_date_w2 PARTITION OF menu_data
	  FOR VALUE FROM ('2020-01-08') TO ('2020-01-15');
	  ```
- ### list partitioning
	- ```sql
	  CREATE TABLE menu_data
	        (order_id int not null,
	         order_date date not null,
	         order_item text not null,
	         order_type varchar)
	  PARTITION BY LIST(order_type);
	  
	  CREATE TABLE order_appetizer PARTITION OF menu_data
	  FOR VALUE IN ('vegetarian', 'vegan', 'meat');
	  
	  CREATE TABLE order_entree PARTITION OF menu_data
	  FOR VALUE IN ('with_rice', 'with_beans', 'with_fries');
	  ```
- ### hash partitioning
	- ```sql
	  CREATE TABLE menu_data
	        (order_id int not null,
	         order_date date not null,
	         order_item text not null,
	         order_type varchar)
	  PARTITION BY HASH(order_id);
	  
	  CREATE TABLE ordered_item_1 PARTITION OF menu_data
	  FOR VALUE WITH (MODULUS 5, REMAINDER 0);
	  
	  CREATE TABLE ordered_item_2 PARTITION OF menu_data
	  FOR VALUE WITH (MODULUS 5, REMAINDER 1);
	  ```
- ## Reliability
	- interface & database error
		- connection already closed
		- connection exception
		- connection doesn't exist
		- triggered action exception
		- invalid role specification
	- data & operational
		- numeric value out of range
		- invalid date
		- division by zero
		- invalid SQL statement
	- integrity and internal
		- not null violation
		- foreign key violation
		- modify data not permitted
	-
	-
- ## Maintainability
-