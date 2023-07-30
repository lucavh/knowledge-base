Indirection is a [[software-design]] principle that involves introducing an intermediary or abstraction between components or modules to achieve decoupling and flexibility. By adding this extra layer of indirection, changes in one component are less likely to have a direct impact on others, making the system easier to maintain and modify. Indirection enables the software to adapt to changes without requiring extensive modifications to the entire codebase.

For example, consider a video game application where different characters interact with each other. Instead of having direct references to specific character classes in the game code, the application uses a CharacterController interface. Each character class implements this interface, providing its unique behavior. The game logic interacts with the characters through the CharacterController interface, not knowing the specific character types. This indirection allows for the addition of new character types in the future without altering the core game logic, promoting a more flexible and scalable design.

Indirection belongs to the set of [[grasp-design-patterns]].

[[software-design]]