- ## Definition
- Object-like relational database
- similar to [[SQL]] but they have inheritance, function overloading
-
- ## Database Indexing
	- D-tree search
	- ```sql
	  explain analyze SELECT id FROM "user" WHERE name = 'Nil';
	  explain analyze SELECT id FROM "user" WHERE name like '%Nil%'; -- matching is slowest
	  ```
- ## Trigger Functions
- [PosgreSQL Docs](https://www.postgresql.org/docs/current/plpgsql-trigger.html)
-
- ## Database Partitioning