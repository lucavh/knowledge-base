Stands for **General Responsibility Assignment Software Patterns** created by Craig Larman.

### Creator Principle
- Helps you decide which class is reponsible for creating obects. 
- Problem: Who creates objects `A`?
- Solution: In general, assign the responsibility to create a new object to a class that contains, aggregates, records, closely uses or has initializaing information of instances of the new object.

### Information Expert Principle
- Helps you decide where you should assign new responsibilities. 
- Problem: Where should you assign new responsibilities to objects?
- Solution: Assign responsibility to the class that has the most information needed to fulfill it. 

### Controller
- Problem: Who should be responsible for handling an input system event?  
- Solution: A _use case controller_ should be used to deal with _all_ system events of a use case, and may be used for more than one use case. For instance, for the use cases _Create User_ and _Delete User_, one can have a single class called _UserController_, instead of two separate use case controllers.

### Protected variations
- Helps you make sure that you introduce abstraction so that you can split up certain parts of your application.
- Problem: How to design objects, subsystems, and systems so that the variations or instability in these elements does not have an undesirable impact on other elements?
- Solution: Identify ponts of predicted variation or instabilityl assign responsibilities to create a stable interface around them.

### Indirection
- Problem: Where to assign responsibility, to avoid direct coupling between two (or more) things? How to de-couple objects so that low coupling is supported and reuse potential remains higher?
- Solution: Assign the responsibility of mediation between two elements to an intermediate object to support low coupling and increase reuse potential. 

### Low coupling
[[low-coupling-and-high-cohesion]]

### High cohesion
[[low-coupling-and-high-cohesion]]

### Polymorphism
- Helps you to use inheritence to swap out behavior. 
- Problem: How to handle alternatives based on type (e.g. different types of conversions)? 
- Solution: Decouple the action (what) from the flavours (how), e.g. decouple the conversion method from the different types of conversion.

### Pure fabrication
- Problem: You don't have a clear place to put something.
- Solution: A seperate class/module that is specially made up to achieve low coupling, high cohesion, and the reuse thereof.

[[design-patterns]]