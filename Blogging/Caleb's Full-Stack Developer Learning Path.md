
Disclaimer: this isn't meant to be an end all be all. I'm not saying if you don't know something on the list, you're a fraud. These are just things that I have found useful in my career so far, ranked from most fundamental to most specialized / complex. It's mainly a list of topics, and the research is for you to do. Doing my own research usually cements the ideas for longer.

# Level 0: Tools of the Trade

I consider these a bare minimum for anyone who wants to be any kind of software developer. You can probably learn them within a few months and they are language agnostic.
* Basic programming syntax and ideas like data types, structures, control flow, loops etc
* OOP - inheritance, encapsulation, polymorphism, etc
* Value types vs reference types
* Heap vs Stack
* Recursion
	* Benefits - recursion can elegantly decribe problems in a human readable way
	* Drawbacks - performance is generally worse than iterative approaches (for example using a while loop). Fun fact: it's been proven that ANYTHING you can write using recursion, you can write with loops. The reason recursion is slower is because it unnecessarily adds to the stack.
* Git - for some insane reason college does not teach you this until like year 4. At a minimum you should understand these commands and what they do:
	* `clone`
	* `fetch`
	* `checkout`
	* `pull`
	* `push`
	* `merge` - just a conceptual understanding is fine, since you only need this one when working with others
	* Other very helpful ones are `status` and `stash`
* You should be able to to basic things in the unix (mac and linux) command line like change folders (`cd`), list the files in the current folder (`ls`), create a folder (`mkdir`), make a file ( `touch`) and clear the terminal display `clear`. A lot of these work in windows too. Other useful commands are `ping`, `nano`, `pwd`, `find`, `rm`, `cat`
* Debugger - not learning to use the debugger is like trying to push a nail into wood with your bare hands when a hammer is within reach. It's not that hard and it will save you rediculous ammounts of time
	* Also play around with the "watch" feature of your debugger. You can type any expression into the watch and the expression will be evaluated. 

# Level 1: Learning the Ropes

These are things that I would aim to learn in the first year of either internships or junior development.

## High Level Concepts

**MVC** - Model View Controller is a very common architecture used when building backends (apis). I suggest reading a little on the conceptual side but also just dive in and learn a framework that uses MVC. There is Spring Boot for Java, ASP.NET for C#, and Django for Python. This is a good Spring Boot series: https://www.youtube.com/watch?v=9SGDpanrc8U
**SOLID** - 5 principles to make clean code
* Single Responsibility Principle - one function, one effect
* Open Closed Principle - implementation details should be private, but imformation useful to sub-classes should be available. In C# and TypeScript, this can be accomplished with the `protected` access modifier.
* Linskov Substitution - If classes B and C inherit from A and a function's parameter accepts classes of type A, passing in either a B or C should have the exact same behavior. In other words, subtypes should be substitutable if the consumer is only concerned with the supertype.
* Interface Segregation - keep interfaces as small and distinct as possible to maximize reusability
* Dependency Inversion - use abstractions instead of implementations when possible. This means work with interfaces, base classes, and abstract classes when possible instead of directly using a class. It makes things easier to test and refactor in the future.
**Composition over Inheritance** - Program to interfaces by default, only use inheritance when there is a clear advantage. This is a good example: https://www.baeldung.com/cs/program-to-interface
**Time Complexity / Algorithm Analysis** - If you went to college, you are probably set here. If not, make sure you understand big O notation
**Common Data Structures** - These data structures come up a lot and are good to have in your toolbelt. ESPECIALLY hashtables.
* Hashtable / Dictionary / Lookup (they are called different things depending on the language)
* Linked List
* Set
* Trees
**Functional Programming and Side Effects** - Good to know the ideas of pure functions and side effects. Don't need to go super deep but those terms are good to have in the vocabulary
**Testing** - Get familiar with automated tests. Unit tests and integration tests are the main ones to know about. There will certainly be libraries in your language of choice the help with both.
* Mocking is also an important idea to know of

## Important Tools To Know About

**Containers** - See Docker documentation. It's essentially a very lightweight virtual machine. Great for running programs in parallel that have conflicting dependencies and making sure everyone on the team can run the apps regardless of their system.
**Hashing Methods**
* SHA-256, 516 - very secure
* MD5 - not considered secure but faster
**GUIDs** - globally unique identifiers. A cryptographically random string of bits. Often used as an alternative to auto incrementing number primary keys. This allows things like offline syncing.

## Web Development

If you're a full-stack developer, you'll most likely work with front-end technologies. Before jumping into learning a framework like Angular or React, I would suggest building a site with "vanilla" javascript. It will help you understand the underlying mechanisms in those frameworks later. These are topics I would look into:
* Javascript - basic syntax, data types, and stuff that you learn for all languages
	* Arrow Functions
	* DOM Manipulation - This is just the term for making changes to the HTML on the page. The HTML is represented by a giant javascript object called the Document Object Model (DOM). https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Manipulating_documents
	* The "spread operator" - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax
	* Promises - this will also be a nice intro to asynchronous programming
* CSS - look into the various ways you can select elements, like by parent, class, element, or a combination of them
	* Look into flexbox, it will make your life easier
	* Check out SASS, it is a similar language that compiles down into CSS. It comes with nice features that make your life easier
	* Look into style libraries like Bootstrap or Tailwind
* HTML - HTML is pretty self explanatory but here are a few topics you may not be familiar with:
	* iframes
	* forms

Once you've got that (especially the DOM Manipulation part), you can pick a frontend framework to learn. React, Angular and Vue are popular ones. Svelte is also an option but I would recommend learning that after one of the others.

## List Manipulation

May seem oddly specific but working with lists is super common and comes up all over the place. I find myself using them constantly and they often come up in interviews. There are certain methods that most languages have to interact with lists. 
* Mapping function - `map` in javascript, `Select` in C#, and `stream().map` in Java, these methods map each item in a list using a lambda function. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map
* Aggregate function - `reduce` in Javascipt, `Aggregate` in C#, and `stream().reduce` in Java, these methods allow you to aggregate the items in a list into a single value using a lambda you define. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce
* Flattening map function - similar to `map`, but it "flattens" a list of lists by taking the items of the inner lists and putting them directly in the outer list. Called `flatMap` in javascript, `SelectMany` in C# and `stream().flatMap` in Java. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flatMap

## Security

**Secure Public Communication
* There are two kinds of encryption: symmetric and asymetric. 
	* In symmetric encryption, both parties hold a shared secret key. To generate the secret key, there is an algorithm called Diffie-Hellman (https://www.youtube.com/watch?v=NmM9HA2MQGI and https://www.youtube.com/watch?v=Yjrfm_oRO0w). The secret key is XORed with the messages to encrypt and decrypt. 
		* BONUS: In reality, this would only be secure if the message is sent once. The secret key could be inferred if it is used too often. This is solved by the use of "nonces" and "initialization values" if you want to look more into it.
	* In asymmetric encryption, each party publishes a public key and generates a secret key. The secret key is never shared with anyone. RSA is the algorithm used for this. The math is a little more difficult to understand but these videos give the general idea: https://www.youtube.com/watch?v=4zahvcJ9glg and https://www.youtube.com/watch?v=oOcTVTpUsPQ

## Databases

* Tables, Views, Indexed Views - views are essentially saved queries, indexed views actually store updated results of those queries
* Forgien Keys
* Primary Keys
	* Composite - allow multiple columns to act as a row's identifier
* Basic querying - `select`, `where`, `order by`, `distinct`
* Joins - https://www.w3schools.com/sql/sql_join.asp
* Group By - https://www.w3schools.com/sql/sql_groupby.asp
* NULL checking - depending on how the database is set up, NULL = NULL may or may not evaluate to true. It's a gotchya to keep in mind: https://www.red-gate.com/hub/product-learning/sql-prompt/the-null-mistake-and-other-sql-null-heresies

# Level 2: Becoming Well Rounded

At this point I would dive deeper into higher level concepts to prepare you for a more mid to senior level role. Getting familiar with roles around yours are also important, like Cloud Engineers, DevOps Engineers, Data Engineers, Data Scientists, Security Analysts, and Architects. Being a Full-Stack developer means having a well rounded picture of the technology that goes into building and maintaining software. As a kind of generalist, you could very well move into one of those roles in the future, too.

I also think it's important to be more intentional when you are developing. Before writing code, draw a sketch of the architecture you plan to implement. Think about things like, "will this be easy to write tests for?", "if I need to add to or change something about this later, will this architecture allow me to?", and "if I come back to this in 6 months, will I understand what I did?"

## Cloud

Everyone interacts with the cloud at this point, and it's good to have a general understanding of it's components. I would reccommend taking a beginner cloud certification prep like AZ-900 or AWS Cloud Practitioner. Very common services include:
* Storage - AWS S3 or Azure Blob Storage
* Virtual Machines
* Load Balancers
* Infrastructure As Code Tools - Azure ARM Templates or AWS Terraform
* Virtual Networks and Subnets
* Serverless Compute - AWS Lambda or Azure Functions
* Container Orchestration Tools - Kubernetes is usually what is used, it's an open source tool. AWS and Azure have their own wrapper services that make it easier to use
* CDNs (Content Delivery Networks)
* Firewalls
* Low Code Workflow Tools - Azure Logic Apps or Power Automate
* Message Queues - AWS SMS or Azure Service Bus

## Networking

At this point people may start to expect you to know certain things around networking, even if they aren't used directly in your day-to-day. Here are a few topics to look over:
* DNS Servers - they are the servers that map domain names to IP addresses
* Routing - routing is how one computer on a network finds another computer. This happens over the public internet too. It's very interesting: https://en.wikipedia.org/wiki/Routing

## Security

Here are some more security concepts to be aware of as a full-stack developer:
* DDOS Attacks - Denial of Service attacks are basically just overloading your servers to the point that they become useless to your customers. There are various solutions to mitigate this, especially on the cloud including AI powered firewalls
* SQL Injection Attacks - If user input isn't cleaned properly, attackers can use that to execute SQL on your database
* Timing Attacks - some bad actors can use timing to infer private information. For example, if you are comparing a password attempt to the actual password, it would take a little longer to reject if the first few characters were correct, giving the attacker information. This is just one example, there are other ways to use timing to get private info.
* Thread Isolation - if a computer is infected a virus may be able to actually listen to nearby threads and gather information. There is a setting on your computer that makes this more difficult, called thread isolation
* Cross Site Scripting - Various methods to execute javascript on someone else's computer if form fields aren't cleaned properly

## Architecture & Design

I would recommend going over the cloud section first before hitting this. First, watch this short video on architecture: https://www.youtube.com/watch?v=ElMnHDSFaCw&list=PLwLLcwQlnXBxeirFuVX9D24UMLSGU65Tw this guy's channel has a lot of other good stuff.
* Difference between a Monolith and Microservices - https://www.youtube.com/watch?v=GBTdnfD6s5Q
* Difference between Event Driven and RPC Style Microservices - Event driven architecture is when each service emits events for things related to that service, and other services react to those events in whatever way they choose. RPC (remote procedure call) style architecture is more tightly coupled and is where services explicitly call for actions to be made in other services. The benefits of event-driven is things are very loosely coupled, while the downside is there can be a lot of noise and unnesecary messages. The benefits of RPC is it's much more direct but at the same time, that tight coupling can be bad. https://www.youtube.com/watch?v=STKCRSUsyP0
* Domain Driven Design - A popular architectural style especially used in the Microsoft stack. Quick intro video: https://www.youtube.com/watch?v=8Z5IAkWcnIw More in depth explanation (which also goes over Event Sourcing and CQRS): https://www.youtube.com/watch?v=rolfJR9ERxo

## Methodology
* Test Driven Development - an important development methodology that forces you to write automated tests *before* you write the code itself. This forces you to structure your code in a testable way, clearly define success, and obviously creates great test coverage for long term stability. https://en.wikipedia.org/wiki/Test-driven_development and https://www.youtube.com/watch?v=Bq_oz7nCNUA are good intros. https://www.youtube.com/watch?v=EZ05e7EMOLM is a very interesting talk on the pros and cons of the method.

## Frontend

At this point you've been working with a frontend framework for a little while. I would look into these topics to 
* Typescript - if you aren't already using TypeScript, check it out! It's super powerful and helpful
* Redux pattern - redux is a design pattern meant to make managing state easier. There are various libraries that implement this pattern depending on the framework you use (Redux for React, NgRx for Angular, etc)
* Change Detection - this is the process that your framework of choice uses to determine which DOM changes need to be made after you do stuff to change the state. It's good to look into because there are some gotchyas around reference types like arrays and objects. The exception to this would be Svelte, because it doesn't do change detection. It has a fancy compiler that explicitly manipulates the DOM without having to detect changes.

## Meta Programming

* Compilers - look into compilers and the general idea of how they are built. Did you know that typescript is written entirely in typescript?
* Interpreters - should know the difference between a compiled language and an interpreted language. An example of an interpreted language is Python. 
* Decorators - this is a feature that a lot of languages have, including Python, Java and C#. It allows you to basically write code that writes code at compile time. Even if you don't make your own, it's good to know how they work because you have most likely been using them without knowing it

## Useful Algorithms

Certain algorithms are especially helpful to know. I find that graph algorithms can help in so many different places because of how flexible they are. These are nice ones to know about:
* Shortest Path Algorithms - there are various ones out there depending on the kind of graph and use case, Geeks for Geeks usually has nice explanations https://www.geeksforgeeks.org/dijkstras-shortest-path-algorithm-greedy-algo-7/
* Breadth First and Depth First Search - also on Geeks for Geeks
* Finding a Cycle in a Graph - also on Geeks for Geeks

## More On Databases

* If you did the cloud section, you probably heard of flat file databases like MongoDB. I suggest learning about that and understanding the pros and cons:
	* Pros - reads are incredibly fast
	* Cons - there is a lot of duplicated data, which makes writes harder and increases storage costs. Luckily, storage is dirt cheap on the cloud so that is not usually a concern
* Take a deeper dive into SQL. I highly recommend this course: https://www.linkedin.com/learning/advanced-sql-logical-query-processing-part-1/course-introduction?autoplay=true 
	* Set Operations
	* Query Processing Order - different parts of a query execute in a set order. Knowing this can make debugging queries much easier. Again, I recommend that LinkedIn Learning course listed above

# Level 3: Specialization

If you've mastered level 2, you have a well rounded understanding of full-stack development. You probably know a couple backend languages and frameworks as well as frontend technologies. From here you can really branch out or further hone to fullstack skills. Here are a few possible directions you might go and good starting points for each.

## Blockchain

## AI and ML

## Data Engineering

## Security

## Cloud

## Backend Specialist

## Frontend Specialist

## UI / UX Developer

# Appendix: My Favorite Resources