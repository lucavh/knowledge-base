The creator principle is a [[*software-design]] principle that promotes creating instances of objects through a separate class or method instead of allowing unrelated classes to create instances directly. 

For instance, in a drawing application, using a ShapeFactory class to create different shapes enhances flexibility and maintainability by reducing dependencies between classes. This enables easy modifications to the creation process without impacting client classes that use the shapes.

The creator principle belongs to the set of [[grasp-design-patterns]].

[[*software-design]]