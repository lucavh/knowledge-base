Pure fabrication is a [[software-design]] principle that involves creating new classes or components solely to enhance modularity and reduce code dependencies. By isolating non-existent responsibilities into separate entities, developers achieve a more maintainable and flexible design. 

For example, suppose we have a Library class that is responsible for handling all aspects of the library, including managing books, issuing and returning books, and handling user accounts. Introducing an EmailService class solely responsible for sending notifications to users allows the main Library class to focus on managing books and user accounts, resulting in a cleaner and more manageable codebase.

Pure fabrication belongs to the set of [[grasp-design-patterns]].

[[software-design]]