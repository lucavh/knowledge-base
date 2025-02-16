Dependency inversion is part of a group of design principles that is called the [[solid-design-principles]]. D stands for dependency inverison. 

Dependency Inversion encourages high-level modules to depend on abstractions rather than concrete implementations. This means that the core components of a system should not rely directly on specific low-level details, but rather on abstract interfaces or classes. By doing so, the codebase becomes more flexible, maintainable, and easier to extend, as different implementations can be easily swapped without affecting the higher-level modules.

In practice, you want to apply an abstraction mechanism and types in your code. [[Python]] does not support this by default, but you can make use of the module called `ABC` (Abstract Base Class) and `type hinting`. 

For example, in an application with a logging feature, the high-level business logic should not directly depend on a specific logging library. Instead, it should rely on an abstract logging interface. The concrete implementation of the logging interface (e.g., writing logs to a file or sending them to a remote server) is decided and injected at runtime, enabling easy configuration and adaptability.

[[software-design]]
