Polymorphism is a [[*software-design]] principle that allows objects of different classes to be treated as instances of a common superclass. This principle enables a single interface to represent multiple related classes, promoting flexibility and extensibility in the codebase.

For example, in a geometry application, we have different shapes like Circle, Square, and Triangle, each represented by their respective classes. To apply polymorphism, we create a common Shape superclass with a method called "calculateArea." Each shape class (Circle, Square, Triangle) inherits from the Shape superclass and provides its implementation of "calculateArea" based on its specific formula. Now, we can store various shapes in a list of type "Shape" and call the "calculateArea" method on each shape without knowing the specific type. This flexibility allows us to easily add more shapes in the future without altering existing code.

Polymorphism belongs to the set of [[grasp-design-patterns]].

[[*software-design]]