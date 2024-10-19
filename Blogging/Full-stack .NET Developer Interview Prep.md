(Roughly in order of importance to the interview)
* SOLID
	* Single responsibility
	* Open closed principle
	* Liskov Substitution Principle
	* Interface segregation principle
	* Dependency inversion
* Composition over inheritance
* Understand the broad differences between .NET framework and ASP.NET
* Basic interview problems
	* Should understand arrays, linked lists, sets, maps, and stacks. Should know their tradeoffs and when to use them
	* Should understand conceptually what a hash is and how sets / maps use them (not just a cryptographic hash like SHA256)
	* Recursion and it's most common uses, especially DFS and BFS
	* Example problems:
		* Is string palindrome (I got this on two separate interviews for some reason)
		* Find shortest between nodes in a graph
		* Find the missing backet problem
		* Find a cycle in a directed graph
* Essential SQL
	* You already know SQL from EF core, you just need to get comfortable with writing it raw instead of with the ORM
	* CASE ... WHEN statements
	* COALESCE
	* common aggregates like MIN, MAX, AVG, CONCAT
	* subqueries
* Event driven architecture and Microservices
	* Tradeoffs: 
		* cons: debugging across services is hard, complexity, must handle network issues, be fault-tolerant
		* pros: (theoretically) teams can work independently from each other and deploy without coordinating with the other teams. Individual services should also be smaller, making their maintenance easier
* AWS services:
	* AWS Lambda
		* Tradeoffs between serverless compute like functions vs standalone servers
	* DynamoDB
		* Tradeoffs between "flat file" dbs like dynamo / mongo vs traditional relational servers
	* Message Services like SNS & SQS (or just generally what a message queue is in cloud architectures)
		* Pub-sub (it's just the observer pattern if you think about it :P)
		* Related: event driven architecture
	* Nice plus: Kubernetes and Docker
* Garbage collection, how objects are held in memory in managed languages
* Frontend
	* Signals!!
		* Benefits over observables
		* When to use observables
		* Bonus: js WeakMap and how it allows signals to avoid creating memory leaks without unsubscribes
	* State management best practices (separation of business logic from view layer mainly)
	* Async pipe
* Domain driven design
	* Tradeoffs in complexity

![[image.png]]