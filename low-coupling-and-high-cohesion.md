Cohesion & coupling are [[software-design]] principles.

## Low coupling

- Coupling is a measure of how dependent two parts of your code are on eachother. Low coupling allows you to split up your code, having less dependencies and higher reuse potential.
- An example of high coupling is a function that accesses data that is deep in the structure of an object. Requires a lot of adjustments.
- An example of low coupling is minimal dependency and little changes required.

## High cohesion

- Cohesion is the degree to which elements of a certain class or function belong together. High cohesion allows you to minimize responsibilities of classes or modules in your code in order to keep them manageable and easy to understand.
- An example of low cohesion is a function does a lot of different things that do not belong together.
- An example of high cohesion is a function with a clear responsibility, only one task to execute.
- Recommendation: make classes/modules either data focused (representing data structure) or behavior focues (keep data associated realtively simple)

Low coupling and high cohesion belong to the set of [[grasp-design-patterns]].

[[software-design]]