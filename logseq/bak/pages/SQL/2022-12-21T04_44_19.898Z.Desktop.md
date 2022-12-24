alias:: SQL-cheatsheet

- {{renderer :tocgen}}
- ## ACID Transaction
	- [YT-explained](https://www.youtube.com/watch?v=pomxJOFVcQs&list=PLQnljOFTspQXjD0HOzN7P2tgzu7scWpl2)
	-
- ## Create table
	- ```sql
	  create table "user"(
	  	id SERIAL PRIMARY KEY,
	    	name VARCHAR(50),
	    	age INT,
	    	pwd TEXT,
	    	preference CHAR VARYING(100)
	  )
	  
	  create table post (
	  	id SERIAL PRIMARY KEY,
	    	content VARCHAR(50),
	    	user_id INT, -- comments
	    	CONSTRAINT fk_user 
	    		FOREIGN KEY(user_id)
	    			REFERENCES "user"(id)
	  )
	  
	  INSERT INTO "user"(name, age) 
	  	VALUES ("Nil Nguyen", 21);
	  ```
- ## Queries
	- ```sql
	  UPDATE post SET content = "see ya"
	  	WHERE id = 1;
	  
	  DELETE FROM "user"
	  	WHERE id = 1;
	  
	  SELECT name FROM "user";
	  
	  
	  ```
- ## Joins
-
- ## Filter
-
- ## Trigger function
-
-