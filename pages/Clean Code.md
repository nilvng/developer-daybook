page-type:: [[Book]]
author:: Robert C. Martin

- ## Principles, patterns, practices in writing code
	- ### Meaningful name
	- ### Functions
	  collapsed:: true
		- 1. Small
		- 2. Do One thing
		- 3. One level of abstraction
		- 4. switch -> polymorphism
		- 5. Arguments
			- Minimize the use
			- Consider the order in function name
		- 6. No Side effects
		- 7. Either your function should change the state of an object, or it should return some information about that object. Doing both often leads to confusion
		  8. Prefer throwing exception to separate the happy path with errors
	- ### Comments
		- #### Goods
			- Amplification
			- informative comments, always prioritize to do it with function names
			- explanation of intent
			- clarification
			- warning of consequences
		- #### Bads
			- mumblings: Any comment that forces you to look in another module for the meaning of that comment has failed to communicate
			- noise comments
			- journal comments
-
- ## Case Studies
-
- ## Heuristics and smells gathered through case studies
-