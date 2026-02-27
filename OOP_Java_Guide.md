# Object-Oriented Programming in Java — Complete Conceptual Guide

> A clear, sufficient explanation of every OOP concept you need — no fluff, no code dumps, just understanding.

---

## Table of Contents

1. [What is OOP?](#what-is-oop)
2. [Classes and Objects](#classes-and-objects)
3. [The Four Pillars of OOP](#the-four-pillars-of-oop)
   - [Encapsulation](#1-encapsulation)
   - [Abstraction](#2-abstraction)
   - [Inheritance](#3-inheritance)
   - [Polymorphism](#4-polymorphism)
4. [Constructors](#constructors)
5. [The `this` Keyword](#the-this-keyword)
6. [The `static` Keyword](#the-static-keyword)
7. [The `final` Keyword](#the-final-keyword)
8. [Access Modifiers](#access-modifiers)
9. [Abstract Classes](#abstract-classes)
10. [Interfaces](#interfaces)
11. [Abstract Class vs Interface](#abstract-class-vs-interface)
12. [Composition vs Inheritance](#composition-vs-inheritance)
13. [Method Overloading vs Overriding](#method-overloading-vs-overriding)
14. [SOLID Principles](#solid-principles)
15. [Object Relationships](#object-relationships)
16. [Common OOP Design Patterns in Interviews](#common-oop-design-patterns-in-interviews)
17. [Enums](#enums)
18. [Wrapper Classes and Autoboxing](#wrapper-classes-and-autoboxing)
19. [The `Object` Class](#the-object-class)
20. [Garbage Collection Basics](#garbage-collection-basics)
21. [Common Mistakes in Java OOP](#common-mistakes-in-java-oop)
22. [Interview Thinking Framework for OOP Questions](#interview-thinking-framework-for-oop-questions)
23. [Quick Revision Cheat Sheet](#quick-revision-cheat-sheet)

---

## What is OOP?

Object-Oriented Programming is a way of organizing code around **objects** — things that bundle **data** (what they know) and **behavior** (what they can do) together.

Instead of writing a long list of instructions, you model your program as a collection of interacting objects, each responsible for a specific part of the system.

**Why OOP?**
- **Modularity:** Each object is a self-contained unit. You can work on one without breaking another.
- **Reusability:** Write once, reuse in many places through inheritance and composition.
- **Maintainability:** Changes in one class don't ripple through the entire codebase (if designed well).
- **Models the real world:** A `BankAccount` object with `deposit()` and `withdraw()` methods mirrors how we think about bank accounts.

---

## Classes and Objects

### Class
A class is a **blueprint** or **template**. It defines:
- What data an object will hold (fields/attributes)
- What actions an object can perform (methods)

Think of a class like an architectural plan for a house. The plan itself isn't a house — it describes how to build one.

### Object
An object is a **specific instance** of a class. It exists in memory and holds actual values.

If `Car` is a class, then "my red Toyota" is an object. "Your blue Honda" is another object of the same class, with different field values.

### Key Points
- A class can have **many objects** (instances)
- Each object has its **own copy** of instance fields
- All objects share the **same methods** defined in the class
- Creating an object is called **instantiation** (done using `new` in Java)

---

## The Four Pillars of OOP

### 1. Encapsulation

**What it is:** Wrapping data (fields) and the methods that operate on that data into a single unit (class), and **restricting direct access** to the internal data.

**How it works in Java:**
- Make fields `private`
- Provide `public` getter and setter methods to access/modify the fields
- The setter can include **validation logic** (e.g., reject negative age values)

**Why it matters:**
- **Protects data integrity:** You can't set an account balance to -500 if the setter prevents it
- **Hides implementation details:** You can change how data is stored internally without affecting code that uses the class
- **Controls access:** Read-only fields only have a getter, no setter

**Real-world analogy:**
A TV remote. You press buttons (public methods) to change the channel. You don't open the remote and rewire it (directly accessing private internals).

**The rule of thumb:** Fields should **always** be private unless there's a very strong reason to do otherwise.

---

### 2. Abstraction

**What it is:** Hiding the **complex implementation** and exposing only the **essential interface** to the user.

**How it works in Java:**
- Abstract classes and interfaces define WHAT an object can do without specifying HOW
- Users of a class interact with its public methods, not its internal logic

**Why it matters:**
- **Simplifies usage:** You call `list.sort()` without knowing if it uses merge sort, timsort, or quicksort internally
- **Reduces complexity:** Each class handles its own complexity; external code doesn't need to know
- **Enables swapping implementations:** If you depend on a `Database` interface, you can switch from MySQL to PostgreSQL without changing business logic

**Real-world analogy:**
Driving a car. You turn the steering wheel and press pedals (the interface). You don't need to understand the combustion engine, hydraulic systems, or electronics (the implementation).

**Encapsulation vs Abstraction:**
- **Encapsulation** = hiding the data (making fields private)
- **Abstraction** = hiding the complexity (showing only what's necessary)
- They overlap but are distinct. Encapsulation is the mechanism; abstraction is the design goal.

---

### 3. Inheritance

**What it is:** A class (child/subclass) **derives** properties and behavior from another class (parent/superclass).

**How it works in Java:**
- Use the `extends` keyword: `class Dog extends Animal`
- The child class **inherits** all non-private fields and methods from the parent
- The child class can **add** new fields and methods
- The child class can **override** inherited methods to change behavior

**Types of Inheritance in Java:**
| Type | Description | Supported? |
|------|------------|-----------|
| Single | One child, one parent | ✅ Yes |
| Multilevel | A → B → C (chain) | ✅ Yes |
| Hierarchical | One parent, many children | ✅ Yes |
| Multiple | One child, many parents | ❌ No (use interfaces instead) |

**Why Java doesn't support multiple inheritance of classes:**
The **Diamond Problem** — if two parent classes have the same method, the child doesn't know which one to use. Java avoids this ambiguity by allowing multiple inheritance only through interfaces (where the child MUST provide its own implementation).

**The `super` keyword:**
- `super()` calls the parent's constructor
- `super.method()` calls the parent's version of an overridden method
- `super` must be the **first statement** in a constructor if used

**When to use inheritance:**
- **"IS-A" relationship:** A Dog IS-A Animal. A SavingsAccount IS-A BankAccount.
- If you can say "X is a type of Y," inheritance makes sense.

**When NOT to use inheritance:**
- **"HAS-A" relationship:** A Car HAS-A Engine. Don't make Car extend Engine. Use composition instead.
- When the parent and child don't share a true hierarchical relationship.

---

### 4. Polymorphism

**What it is:** The ability of a single interface/method to work with different types. Literally means "many forms."

**Two types in Java:**

#### Compile-Time Polymorphism (Method Overloading)
- **Same method name, different parameter lists** within the same class
- Decided at compile time based on the method signature
- Example: `add(int, int)` and `add(double, double)` — same name, different parameter types
- Return type alone is NOT enough to distinguish overloaded methods

#### Runtime Polymorphism (Method Overriding)
- A child class provides its **own implementation** of a method already defined in the parent class
- Decided at runtime based on the **actual object type**, not the reference type
- This is the truly powerful form of polymorphism
- The parent reference can point to a child object, and the child's version of the method runs

**Why it matters:**
- **Flexible code:** Write code that works with the parent type, and it automatically works with ALL child types
- **Extensible:** Add new child classes without modifying existing code
- **Decoupling:** The caller doesn't need to know the specific type — just the interface

**Real-world analogy:**
A universal remote (parent type reference) can control any TV brand (child type objects). You press "power" and each TV handles it differently, but the remote doesn't need to know the details.

**Key rules for overriding:**
- Same method name and parameters
- Same or more accessible access modifier (can't reduce visibility)
- Same or covariant return type (child class return type is allowed)
- Cannot override `static`, `final`, or `private` methods

---

## Constructors

**What:** Special methods that run when an object is created. They initialize the object's state.

**Rules:**
- Same name as the class
- No return type (not even `void`)
- Called automatically when you use `new`
- If you don't write any constructor, Java provides a **default no-arg constructor**
- If you write ANY constructor, Java does **not** provide the default one — you must explicitly write a no-arg constructor if you still need one

**Types:**
| Type | Description |
|------|-------------|
| Default | No parameters. Java provides it if you write none. |
| Parameterized | Takes arguments to initialize fields with specific values. |
| Copy Constructor | Takes another object of the same class and copies its values. (Java doesn't have a built-in copy constructor like C++, but you can write one.) |

**Constructor Chaining:**
- `this()` calls another constructor in the same class
- `super()` calls a constructor in the parent class
- Must be the **first statement** in the constructor
- You cannot use both `this()` and `super()` in the same constructor

**Constructor vs Method:**
| Aspect | Constructor | Method |
|--------|------------|--------|
| Name | Same as class | Any name |
| Return type | None | Required |
| Called by | `new` keyword | Explicitly by name |
| Inherited? | No | Yes (non-private) |
| Purpose | Initialize object | Define behavior |

---

## The `this` Keyword

**What it refers to:** The **current object** — the instance on which the method/constructor was called.

**Uses:**
1. **Distinguish fields from parameters** when they have the same name: `this.name = name;`
2. **Call another constructor** in the same class: `this(param)` — must be first statement
3. **Pass the current object** as an argument to another method
4. **Return the current object** from a method (for method chaining like builder pattern)

**Common confusion:** `this` cannot be used in a `static` context because static methods don't belong to any specific object.

---

## The `static` Keyword

**What it means:** The member belongs to the **class itself**, not to any specific object.

### Static Fields
- **Shared** by all objects of the class (only one copy in memory)
- Useful for constants or counters: "How many Car objects have been created?"
- Accessed via `ClassName.field`

### Static Methods
- Can be called without creating an object: `Math.max(a, b)`
- **Cannot access** non-static fields or methods (because there's no specific object context)
- **Cannot use** `this` or `super`
- Utility/helper methods are often static

### Static Blocks
- Run **once** when the class is first loaded (before any constructor runs)
- Used for one-time static initialization

### When to use static:
- Utility methods that don't depend on object state (`Math.sqrt()`)
- Constants (`static final double PI = 3.14159`)
- Factory methods that create and return instances
- Counters shared across all instances

---

## The `final` Keyword

**Applied to different things, it means different things:**

| Applied to | Meaning |
|-----------|---------|
| **Variable** | Cannot be reassigned after initialization (constant) |
| **Method** | Cannot be overridden by child classes |
| **Class** | Cannot be extended (no subclasses allowed) |
| **Parameter** | Cannot be modified inside the method |

**`final` + `static` = Constant:**
`static final int MAX_SIZE = 100;` — a class-level constant that never changes.

**`final` reference vs `final` object:**
A `final` reference variable can't point to a different object, but the object itself CAN still be modified. `final List<String> list` means you can't do `list = new ArrayList<>()` but you CAN do `list.add("hello")`.

---

## Access Modifiers

| Modifier | Same Class | Same Package | Subclass (different package) | Everywhere |
|----------|-----------|-------------|------|-----------|
| `private` | ✅ | ❌ | ❌ | ❌ |
| (default/package-private) | ✅ | ✅ | ❌ | ❌ |
| `protected` | ✅ | ✅ | ✅ | ❌ |
| `public` | ✅ | ✅ | ✅ | ✅ |

**Rules of thumb:**
- Fields → almost always `private`
- Methods → `public` if part of the API, `private` for internal helpers
- Classes → usually `public` (one public class per file in Java)
- `protected` → use when you want subclasses in other packages to access, but not anyone else

**Default access (no keyword):** Often called package-private. Accessible within the same package only. This is NOT the same as `public`.

---

## Abstract Classes

**What:** A class that **cannot be instantiated** and may contain **abstract methods** (methods without a body).

**Key properties:**
- Declared with the `abstract` keyword
- Can have both abstract methods (no body) AND concrete methods (with body)
- Can have constructors (called by subclasses via `super()`)
- Can have fields (including private ones)
- A child class MUST implement all abstract methods, or it must also be declared abstract

**When to use:**
- When you have a base class that should never be instantiated on its own
- When you want to provide **partial implementation** (some methods defined, some left for subclasses)
- When there's a natural "IS-A" hierarchy with shared state

**Example thinking:** An `Animal` class. You never create a generic "animal" — you create a `Dog` or `Cat`. But all animals share common fields like `name` and `age`, and common concrete methods like `sleep()`. The `makeSound()` method is abstract because each animal sounds different.

---

## Interfaces

**What:** A **contract** that defines what a class must do, without saying how.

**Key properties:**
- All methods are `public abstract` by default (before Java 8)
- Since Java 8: can have `default` methods (with a body) and `static` methods
- Since Java 9: can have `private` methods (helper methods for default methods)
- Fields are `public static final` by default (constants only)
- No constructors (cannot be instantiated)
- A class can implement **multiple interfaces**

**When to use:**
- When unrelated classes need to share a behavior: both `Bird` and `Airplane` can `Flyable`
- When you want to define a capability/contract without forcing a class hierarchy
- When you need multiple inheritance of behavior

**Interface as a Type:**
You can use an interface as a reference type. A variable of type `Comparable` can hold any object whose class implements `Comparable`. This is the foundation of programming to interfaces.

---

## Abstract Class vs Interface

| Aspect | Abstract Class | Interface |
|--------|---------------|-----------|
| Methods | Abstract + concrete | Abstract + default (Java 8+) |
| Fields | Any type | Only `public static final` |
| Constructors | Yes | No |
| Inheritance | Single (`extends`) | Multiple (`implements`) |
| Access modifiers | Any | Public (methods), public static final (fields) |
| Use case | Shared base with partial implementation | Contract / capability across unrelated classes |
| "IS-A" vs "CAN-DO" | IS-A relationship | CAN-DO capability |

**Quick decision:**
- If classes share **state** (fields) and **base behavior**, use abstract class
- If classes share a **capability** but are otherwise unrelated, use interface
- If in doubt, **prefer interfaces** — they're more flexible (multiple implementation)

---

## Composition vs Inheritance

### Inheritance ("IS-A")
- `Dog extends Animal` → Dog IS-A Animal
- Tight coupling: changes in parent affect all children
- Rigid hierarchy: once set, hard to restructure

### Composition ("HAS-A")
- `Car` has an `Engine` field → Car HAS-A Engine
- Loose coupling: you can swap the Engine implementation
- Flexible: change behavior by changing the composed object

### The Golden Rule
> **"Favor composition over inheritance."**

**Why:**
- Inheritance locks you into a hierarchy that's hard to change later
- Composition lets you mix and match behaviors at runtime
- Many real-world relationships are HAS-A, not IS-A
- Inheritance should be used when there's a genuine type hierarchy, not just for code reuse

**Example:**
- ❌ `Stack extends ArrayList` — a Stack is NOT a type of ArrayList. It just uses list-like storage internally.
- ✅ `Stack` has an `ArrayList` field — a Stack HAS storage. The storage is an implementation detail.

---

## Method Overloading vs Overriding

| Aspect | Overloading | Overriding |
|--------|-------------|-----------|
| Where | Same class | Child class overrides parent method |
| Method name | Same | Same |
| Parameters | MUST differ | MUST be same |
| Return type | Can differ | Same or covariant (subtype) |
| Access modifier | Can differ | Same or more accessible |
| Binding | Compile-time (static) | Runtime (dynamic) |
| `static` methods | Can be overloaded | Cannot be overridden (hidden, not overridden) |
| Annotation | None needed | `@Override` recommended |

**Overloading resolves based on:** parameter types at compile time.
**Overriding resolves based on:** actual object type at runtime.

---

## SOLID Principles

### S — Single Responsibility Principle
> A class should have **only one reason to change.**

- Each class should do one thing and do it well
- A `UserValidator` validates users. A `UserRepository` stores users. Don't combine them.
- If you find yourself naming a class `UserManagerUtilHelper`, it probably does too much.

### O — Open/Closed Principle
> A class should be **open for extension, closed for modification.**

- Add new behavior by creating new classes (extending), not by modifying existing ones
- Use inheritance and polymorphism to extend behavior
- If adding a new feature requires editing existing, tested code — the design violates this principle

### L — Liskov Substitution Principle
> A child class should be **usable anywhere the parent class is expected**, without breaking behavior.

- If `Bird` has a `fly()` method, then `Penguin extends Bird` violates LSP because penguins can't fly
- Every subclass must honor the parent's contract
- The child can do MORE than the parent, but never LESS

### I — Interface Segregation Principle
> Don't force a class to implement **methods it doesn't use.**

- Prefer many small, focused interfaces over one large, bloated interface
- If `Robot implements Worker` and Worker has `eat()`, that's a problem — robots don't eat
- Split: `Workable` (has `work()`) and `Eatable` (has `eat()`). Robot only implements `Workable`.

### D — Dependency Inversion Principle
> Depend on **abstractions** (interfaces), not **concretions** (specific classes).

- A `NotificationService` should depend on a `MessageSender` interface, not directly on `EmailSender`
- This allows you to swap `EmailSender` for `SMSSender` without changing NotificationService
- High-level modules (business logic) should not depend on low-level modules (implementation details)

---

## Object Relationships

### Association
- A general relationship: "Object A uses/knows about Object B"
- A `Teacher` teaches `Students`. They exist independently.

### Aggregation (Weak "HAS-A")
- A special form of association where one object *contains* others, but the contained objects can **exist independently**
- A `Department` has `Employees`. If the department is deleted, the employees still exist.

### Composition (Strong "HAS-A")
- The contained object **cannot exist** without the container
- A `House` has `Rooms`. If the house is destroyed, the rooms are gone too.
- The lifecycle of the contained object is tied to the container.

### Dependency
- A temporary, weaker relationship: "Object A temporarily uses Object B"
- A `Printer` uses a `Document` to print. The Printer doesn't own or store the Document.

### Summary:
| Relationship | Strength | Lifecycle Dependency | Example |
|-------------|----------|---------------------|---------|
| Dependency | Weakest | None | Printer uses Document |
| Association | Weak | None | Teacher knows Student |
| Aggregation | Medium | Independent | Department has Employees |
| Composition | Strong | Dependent | House has Rooms |
| Inheritance | Strongest | Type relationship | Dog is Animal |

---

## Common OOP Design Patterns in Interviews

### 1. Builder Pattern
- **Problem:** Creating objects with many optional parameters
- **Solution:** A separate Builder class with methods for each parameter, chained together, finished with `build()`
- **Benefit:** Readable object construction without telescoping constructors

### 2. Singleton Pattern
- **Problem:** Ensuring only ONE instance of a class exists system-wide
- **Solution:** Private constructor + static method that returns the single instance
- **Use case:** Database connection pool, logger, configuration manager
- **Watch out:** Thread safety — lazy initialization needs synchronization

### 3. Factory Pattern
- **Problem:** Creating objects without exposing the creation logic
- **Solution:** A factory method that returns the appropriate subclass based on input
- **Benefit:** Client code doesn't need to know which specific class to instantiate

### 4. Observer Pattern
- **Problem:** When one object changes state, others need to be notified
- **Solution:** Subject maintains a list of observers, notifies them on state change
- **Use case:** Event systems, UI listeners, notification systems

### 5. Strategy Pattern
- **Problem:** You need to switch between different algorithms at runtime
- **Solution:** Define a family of algorithms as separate classes implementing a common interface. Pass the desired strategy to the context.
- **Benefit:** Adding a new algorithm = adding a new class, no existing code changes

---

## Enums

**What:** A special class that represents a **fixed set of constants.**

**Key properties:**
- Enums are implicitly `final` (can't be extended) and `static`
- Each constant is an instance of the enum type
- Can have fields, constructors, and methods (constructors are always private)
- Type-safe: compiler prevents invalid values
- Can be used in `switch` statements

**When to use:**
- Days of the week, months, directions, card suits, states in a state machine
- Anywhere you have a fixed, known set of values
- Prefer enums over `int` constants or `String` constants — they're safer and more expressive

**Enums can implement interfaces,** which makes them powerful for strategy-like patterns.

---

## Wrapper Classes and Autoboxing

**What:** Java has 8 primitive types (`int`, `double`, `boolean`, etc.) that are NOT objects. Wrapper classes (`Integer`, `Double`, `Boolean`, etc.) wrap these primitives as objects.

**Why they exist:**
- Collections (like `ArrayList`, `HashMap`) can only store objects, not primitives
- `ArrayList<int>` is illegal; `ArrayList<Integer>` is valid
- Wrapper classes provide utility methods: `Integer.parseInt()`, `Integer.MAX_VALUE`

**Autoboxing / Unboxing:**
- **Autoboxing:** Java automatically converts a primitive to its wrapper: `Integer x = 5;` (5 is auto-wrapped)
- **Unboxing:** Java automatically converts a wrapper to its primitive: `int y = x;` (x is auto-unwrapped)

**Gotchas:**
- `==` on wrapper objects compares **references**, not values (except for cached values -128 to 127 for Integer)
- Always use `.equals()` to compare wrapper objects
- Unboxing a `null` wrapper throws `NullPointerException`

---

## The `Object` Class

**Every class in Java implicitly extends `Object`.** It's the root of the class hierarchy.

**Important methods you should know:**

| Method | Purpose | When to Override |
|--------|---------|-----------------|
| `toString()` | Returns a string representation of the object | Almost always — default is `ClassName@hashcode` which is useless |
| `equals(Object o)` | Checks logical equality | When you need to compare objects by value, not by reference |
| `hashCode()` | Returns an integer hash for hash-based collections | **Always** override alongside `equals()` — they have a contract |
| `getClass()` | Returns the runtime class of the object | Rarely overridden |
| `clone()` | Creates a shallow copy | Use carefully; prefer copy constructors |

**The equals-hashCode contract:**
- If `a.equals(b)` is true, then `a.hashCode() == b.hashCode()` MUST be true
- If hashCodes differ, `equals()` MUST return false
- If hashCodes are equal, `equals()` MAY still return false (hash collisions)
- **Breaking this contract** causes bugs with `HashMap`, `HashSet`, etc. — objects get "lost" in hash-based collections

---

## Garbage Collection Basics

**What:** Java automatically deallocates memory for objects that are no longer referenced.

**How it works (simplified):**
1. Objects are created on the **heap**
2. When no variable references an object, it becomes **eligible** for garbage collection
3. The garbage collector (GC) periodically identifies and removes unreachable objects
4. You can suggest GC with `System.gc()` but **cannot force it**

**Making objects eligible for GC:**
- Set the reference to `null`
- Let the reference go out of scope
- Reassign the reference to another object

**Why it matters for OOP:**
- You don't manually free memory (unlike C/C++)
- But you should be aware of **memory leaks** — objects that are still referenced but no longer needed (e.g., objects in a growing list that's never cleared)
- In linked list problems, setting unused `next` pointers to `null` helps GC and is good practice

---

## Common Mistakes in Java OOP

### 1. Confusing `==` with `.equals()`
- `==` compares **references** (are these the same object in memory?)
- `.equals()` compares **values** (are these logically equivalent?)
- For strings: `"hello" == "hello"` may work due to string pooling, but `new String("hello") == new String("hello")` is `false`
- **Always use `.equals()` for object comparison**

### 2. Overriding `equals()` Without `hashCode()`
- If two objects are equal, they MUST have the same hash code
- Forgetting this breaks `HashMap` and `HashSet`

### 3. Making Everything Public
- Violates encapsulation
- Makes it impossible to enforce invariants
- Default instinct should be: make it `private`, promote accessibility only when needed

### 4. Deep Inheritance Hierarchies
- More than 2-3 levels deep becomes hard to understand and maintain
- Prefer shallow hierarchies + composition

### 5. God Classes
- A single class that does everything
- Violates Single Responsibility Principle
- If your class has 20+ methods or 500+ lines, it's probably doing too much

### 6. Forgetting `super()` in Constructors
- If the parent has no no-arg constructor, the child MUST explicitly call `super(args)` in its constructor
- Failing to do so = compilation error

### 7. Attempting to Override Static Methods
- Static methods are **hidden**, not overridden. The method called depends on the reference type, not the object type.
- This is NOT polymorphism.

### 8. Modifying a `final` Reference Object
- `final` prevents reassignment of the reference, NOT mutation of the object
- `final List<String> list = new ArrayList<>();` → you CAN `list.add("x")` but CANNOT `list = new ArrayList<>()`

### 9. Using Inheritance for Code Reuse Only
- Inheritance should represent a genuine IS-A relationship
- If you just want to reuse some methods, use composition (HAS-A) or a utility class

### 10. Not Using `@Override` Annotation
- Without it, a typo in the method name creates a NEW method instead of overriding
- `@Override` makes the compiler verify that you're actually overriding something

---

## Interview Thinking Framework for OOP Questions

When given an OOP design question (like "Design a Bank System" or "Design Twitter"), follow this framework:

### Step 1: Identify the Entities
- Read the problem statement carefully
- **Every significant noun** is a potential class: User, Account, Tweet, URL
- Ask: "What are the THINGS in this system?"

### Step 2: Identify the Actions
- **Every significant verb** is a potential method: deposit, withdraw, post, follow, encode
- Ask: "What can these things DO?"

### Step 3: Identify the Relationships
- Which entity owns which? (Composition)
- Which entity uses which? (Association / Dependency)
- Is there a hierarchy? (Inheritance)
- Ask: "How do these things RELATE to each other?"

### Step 4: Identify the Data
- What does each entity need to remember? (Fields)
- What is the right data structure for storing this? (HashMap, List, Array, Set)
- Ask: "What STATE does each object maintain?"

### Step 5: Define the API
- What methods should each class expose publicly?
- What are the parameters and return types?
- Ask: "How will external code INTERACT with these objects?"

### Step 6: Handle Edge Cases
- What happens with invalid input? (Negative amounts, non-existent IDs)
- What are the boundary conditions? (Empty list, single element)
- Validation should be the FIRST thing in every public method

### Step 7: Apply Design Principles
- Are fields `private`? (Encapsulation)
- Is each class focused on one responsibility? (SRP)
- Can new types be added without changing existing code? (OCP)
- Am I depending on interfaces or concrete classes? (DIP)

---

## Quick Revision Cheat Sheet

### The Four Pillars — One Line Each
| Pillar | One-Line Summary |
|--------|-----------------|
| **Encapsulation** | Hide data behind private fields; expose behavior through public methods |
| **Abstraction** | Show only what's necessary; hide the how |
| **Inheritance** | Child class gets parent's properties and behavior; enables IS-A hierarchies |
| **Polymorphism** | One interface, many implementations; method behavior depends on the actual object |

### SOLID — One Line Each
| Principle | One-Line Summary |
|-----------|-----------------|
| **S** | One class, one job |
| **O** | Extend behavior, don't modify existing code |
| **L** | Subtypes must be substitutable for their parent types |
| **I** | Small, focused interfaces over large, bloated ones |
| **D** | Depend on abstractions (interfaces), not concretions (specific classes) |

### Keywords — Quick Reference
| Keyword | On Variable | On Method | On Class |
|---------|-----------|-----------|---------|
| `static` | Shared across all instances | Callable without an object | (static nested class) |
| `final` | Can't reassign | Can't override | Can't extend |
| `abstract` | — | No body, must be implemented | Can't instantiate |

### Relationship Types
| See... | Think... |
|--------|----------|
| IS-A | Inheritance (`extends`) |
| CAN-DO | Interface (`implements`) |
| HAS-A (strong) | Composition (field, lifecycle tied) |
| HAS-A (weak) | Aggregation (field, independent lifecycle) |
| USES | Dependency (parameter/local variable) |

### Method Resolution
| Scenario | Resolved At | Based On |
|----------|-----------|----------|
| Overloaded methods | Compile time | Parameter types in the call |
| Overridden methods | Runtime | Actual object type (not reference type) |

---

> *"Good OOP design is not about using every feature Java offers. It's about using the right features to create code that is easy to understand, extend, and maintain."*

---

*End of OOP Guide*
