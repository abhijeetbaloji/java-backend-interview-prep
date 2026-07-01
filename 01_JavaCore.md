# Q1. `==` vs `.equals()`, and why `hashCode()`/`equals()` must be overridden together

## What?

In Java, `==` compares **primitive values** directly, but for objects it compares **references**, i.e., whether two variables point to the same object in memory.

The `.equals()` method is used to compare the **logical/content equality** of objects. By default, `Object.equals()` behaves exactly like `==`, but classes such as `String`, wrapper classes, and many collection-related classes override it to compare object data instead of memory addresses.

Whenever a custom class represents a business entity (such as `Employee`, `User`, or `Product`), overriding `equals()` allows objects with the same business data to be treated as equal. If `equals()` is overridden, `hashCode()` must also be overridden to satisfy Java's contract.

## Why?

Java separates **object identity** from **object equality** because many applications compare business data rather than memory locations.

Hash-based collections such as `HashMap`, `HashSet`, and `ConcurrentHashMap` first use `hashCode()` to locate a bucket and then use `equals()` to identify the correct object. If two equal objects return different hash codes, these collections may fail to retrieve stored objects correctly.

For immutable value objects, Java Records (Java 17+) are the preferred production approach because they automatically generate consistent `equals()` and `hashCode()` implementations.

## Key Points

- `==` compares references for objects and values for primitives.
- `.equals()` compares logical/content equality.
- Default `Object.equals()` behaves like `==`.
- Equal objects **must** return the same hash code.
- Unequal objects may still have the same hash code (collision).
- `HashMap` uses `hashCode()` first and `equals()` only if needed.
- Override both methods together.
- Use `Objects.equals(a, b)` for null-safe comparisons.
- Java Records automatically generate `equals()` and `hashCode()`.
- Common mistake: overriding only `equals()`.

## Example

```java
import java.util.*;

class Employee {
    private final int id;

    Employee(int id) {
        this.id = id;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (!(obj instanceof Employee other)) return false;
        return id == other.id;
    }

    @Override
    public int hashCode() {
        return Objects.hash(id);
    }
}

public class Demo {
    public static void main(String[] args) {
        Set<Employee> employees = new HashSet<>();

        employees.add(new Employee(101));

        System.out.println(employees.contains(new Employee(101)));
    }
}
```

## Interview Tip

"`==` compares references for objects, whereas `equals()` compares logical equality. Whenever I override `equals()`, I also override `hashCode()` because hash-based collections like `HashMap` and `HashSet` rely on both methods. Equal objects must always produce the same hash code; otherwise lookups can fail."

## Quick Revision

- `==` → reference comparison
- `.equals()` → content comparison
- Default `equals()` behaves like `==`
- Override `equals()` and `hashCode()` together
- Used heavily by `HashMap` and `HashSet`
- Equal objects → same hash code
- Records generate both methods automatically
- Memory Trick: **Equal Objects = Equal Hashes**

---

# Q2. String immutability and the String pool — why is `String` immutable?

## What?

A `String` is an immutable object, meaning its value cannot be changed after it is created. Operations such as `concat()`, `replace()`, or `toUpperCase()` return a **new String** instead of modifying the existing one.

Java maintains a **String Pool**, a special area in the heap where string literals are stored. When identical literals are encountered, the JVM reuses the existing object instead of creating another one, reducing memory consumption.

Using `new String("Java")` always creates a new object, whereas `"Java"` uses the pooled instance.

## Why?

Immutability enables safe object sharing across multiple parts of an application. Since a String never changes, multiple references can safely point to the same object without synchronization.

It also improves security, thread safety, caching, and performance. The JVM can cache the hash code of immutable strings, making lookups in hash-based collections faster.

For frequent string modifications, `StringBuilder` is recommended because repeated concatenation creates unnecessary temporary objects.

## Key Points

- Strings are immutable.
- String literals are stored in the String Pool.
- Duplicate literals reuse existing objects.
- `new String()` creates a separate object.
- `intern()` moves a string into the pool.
- Cached hash codes improve performance.
- Immutable objects are thread-safe.
- Use `StringBuilder` for repeated modifications.
- String Pool reduces memory usage.
- Common mistake: comparing strings using `==`.

## Example

```java
String s1 = "Java";
String s2 = "Java";
String s3 = new String("Java");

System.out.println(s1 == s2);       // true
System.out.println(s1 == s3);       // false
System.out.println(s1.equals(s3));  // true

StringBuilder builder = new StringBuilder("Java");
builder.append(" 17");
System.out.println(builder);
```

## Interview Tip

"String is immutable because it improves security, thread safety, caching, and enables the String Pool. Since strings never change, the JVM can safely reuse objects and cache hash codes. Whenever frequent modifications are needed, I prefer `StringBuilder`."

## Quick Revision

- Immutable object
- String Pool stores literals
- Duplicate literals reuse memory
- `new String()` creates a new object
- `intern()` adds to pool
- Cached hash code
- Use `StringBuilder` for modifications
- Memory Trick: **Immutable → Pool → Safe → Fast**

---

# Q3. Abstract class vs Interface — when to use which

## What?

An **abstract class** provides a partially implemented base class that can contain constructors, instance variables, concrete methods, and abstract methods. It is suitable when related classes share common implementation.

An **interface** defines a contract that implementing classes must follow. Since Java 8, interfaces support default and static methods, while Java 9 introduced private helper methods.

A class can extend only one abstract class but can implement multiple interfaces.

## Why?

Use an abstract class when several related classes share common state or implementation. It promotes code reuse while allowing subclasses to customize behavior.

Use an interface when defining capabilities or APIs that multiple unrelated classes should implement. Spring Boot applications commonly inject dependencies through interfaces because they encourage loose coupling and make testing easier.

## Key Points

- Abstract class supports constructors.
- Abstract class can have instance variables.
- Interface defines behavior.
- Multiple interfaces can be implemented.
- Only one abstract class can be extended.
- Interfaces support default and static methods.
- Abstract classes improve code reuse.
- Interfaces improve loose coupling.
- Spring commonly injects interface implementations.
- Common mistake: using inheritance where composition is better.

## Example

```java
interface PaymentService {
    void pay(double amount);
}

abstract class BasePaymentService {

    protected void log(String message) {
        System.out.println(message);
    }
}

class CreditCardPayment extends BasePaymentService
        implements PaymentService {

    @Override
    public void pay(double amount) {
        log("Processing payment");
        System.out.println("Paid " + amount);
    }
}
```

## Interview Tip

"I use interfaces to define contracts and enable loose coupling, especially in Spring Boot dependency injection. I use abstract classes when related classes share state or implementation. If I only need common behavior, I choose an interface; if I need shared fields and implementation, I choose an abstract class."

## Quick Revision

- Interface = Contract
- Abstract class = Shared implementation
- Multiple interfaces allowed
- Single inheritance only
- Abstract class supports constructors
- Interface supports default methods
- Spring prefers interfaces
- Memory Trick: **Interface = What, Abstract = How**

---

# Q4. Method overloading vs overriding (including covariant return types and static methods)

## What?

Method **overloading** means multiple methods share the same name but have different parameter lists. The compiler determines which method to invoke, so overloading is compile-time polymorphism.

Method **overriding** occurs when a subclass provides its own implementation of a superclass method using the same signature. The JVM decides which implementation to execute at runtime, enabling runtime polymorphism.

Java also supports **covariant return types**, allowing an overridden method to return a subclass of the original return type.

## Why?

Overloading improves API usability by allowing the same operation to accept different inputs.

Overriding enables polymorphism, allowing applications to substitute subclass implementations without changing client code. This principle is heavily used in Spring Boot, dependency injection, proxies, and framework design.

## Key Points

- Overloading → compile-time polymorphism.
- Overriding → runtime polymorphism.
- Parameter list must differ for overloading.
- Signature must match for overriding.
- Covariant return types are allowed.
- Static methods are hidden, not overridden.
- Private methods cannot be overridden.
- Final methods cannot be overridden.
- Use `@Override` annotation.
- Common mistake: changing only the return type does not overload a method.

## Example

```java
class Animal {

    Animal get() {
        return this;
    }

    static void print() {
        System.out.println("Animal");
    }
}

class Dog extends Animal {

    @Override
    Dog get() {
        return this;
    }

    static void print() {
        System.out.println("Dog");
    }
}
```

## Interview Tip

"Method overloading is resolved at compile time based on parameters, while overriding is resolved at runtime through dynamic dispatch. Java also allows covariant return types during overriding. Static methods are hidden rather than overridden."

## Quick Revision

- Overloading = Compile time
- Overriding = Runtime
- Different parameters for overloading
- Same signature for overriding
- Covariant returns allowed
- Static methods are hidden
- Final methods cannot be overridden
- Memory Trick: **Overload = Compile, Override = Runtime**

---

# Q5. Checked vs unchecked exceptions; when to create a custom exception

## What?

Checked exceptions extend `Exception` (excluding `RuntimeException`) and must either be handled using `try-catch` or declared using `throws`. They generally represent recoverable situations such as file access failures or database connectivity issues.

Unchecked exceptions extend `RuntimeException` and represent programming mistakes such as invalid arguments, null references, or illegal application state. They are not enforced by the compiler.

Custom exceptions represent business-specific failures and improve readability by expressing application intent clearly.

## Why?

Checked exceptions force developers to acknowledge recoverable failures, improving API correctness.

Unchecked exceptions keep application code cleaner by avoiding unnecessary exception handling for programming errors. In Spring Boot, business validation failures are commonly implemented as custom runtime exceptions and handled centrally using `@RestControllerAdvice`.

## Key Points

- Checked exceptions extend `Exception`.
- Unchecked exceptions extend `RuntimeException`.
- Checked exceptions require handling or declaration.
- Runtime exceptions are optional to catch.
- Create custom exceptions for business rules.
- Prefer meaningful exception names.
- Use global exception handling in Spring Boot.
- Avoid catching generic `Exception`.
- Don't use exceptions for normal control flow.
- Include meaningful error messages.

## Example

```java
public class InsufficientBalanceException extends RuntimeException {

    public InsufficientBalanceException(String message) {
        super(message);
    }
}

public class AccountService {

    private double balance = 1000;

    public void withdraw(double amount) {

        if (amount > balance) {
            throw new InsufficientBalanceException("Insufficient balance");
        }

        balance -= amount;
    }
}
```

## Interview Tip

"Checked exceptions represent recoverable conditions and must be handled or declared, whereas unchecked exceptions represent programming errors and extend `RuntimeException`. For business-specific validation, I create custom runtime exceptions and handle them globally using Spring Boot's exception handling mechanism."

## Quick Revision

- Checked → compiler enforced
- Unchecked → runtime only
- Recoverable → checked
- Programming errors → unchecked
- Custom exceptions improve readability
- Prefer `RuntimeException` for business validation
- Handle centrally using `@RestControllerAdvice`
- Memory Trick: **Checked = Compiler Checks, Runtime = Programmer Checks**


# Q5. Checked vs Unchecked Exceptions; When to Create a Custom Exception

## What?

Java categorizes exceptions into **checked** and **unchecked** exceptions. Checked exceptions extend `Exception` (excluding `RuntimeException`) and must be either handled using `try-catch` or declared using the `throws` keyword. They typically represent recoverable situations such as file access failures, database connectivity issues, or network errors.

Unchecked exceptions extend `RuntimeException` and represent programming errors or invalid application states. Examples include `NullPointerException`, `IllegalArgumentException`, and `IndexOutOfBoundsException`. The compiler does not force developers to handle them.

Custom exceptions are user-defined exceptions that represent domain-specific business errors. In modern Spring Boot applications, custom exceptions usually extend `RuntimeException` and are handled centrally using `@RestControllerAdvice`.

## Why?

Checked exceptions ensure that callers explicitly acknowledge recoverable failures, making APIs safer when external resources are involved.

Unchecked exceptions keep business code clean by avoiding excessive `try-catch` blocks for programming mistakes. Custom exceptions improve readability by expressing business intent clearly instead of throwing generic exceptions.

## Key Points

- Checked exceptions extend `Exception`.
- Unchecked exceptions extend `RuntimeException`.
- Checked exceptions must be handled or declared.
- Runtime exceptions are optional to catch.
- Create custom exceptions for business-specific validation.
- Prefer meaningful exception names.
- Handle custom exceptions globally using `@RestControllerAdvice`.
- Avoid catching generic `Exception`.
- Never use exceptions for normal program flow.
- Include meaningful exception messages.

## Example

```java
public class InsufficientBalanceException extends RuntimeException {

    public InsufficientBalanceException(String message) {
        super(message);
    }
}

public class AccountService {

    public void withdraw(double amount, double balance) {
        if (amount > balance) {
            throw new InsufficientBalanceException("Insufficient balance");
        }
    }
}
```

## Interview Tip

"Checked exceptions represent recoverable conditions and must be handled or declared. Unchecked exceptions represent programming errors and extend `RuntimeException`. For business validation failures such as invalid orders or insufficient balance, I create custom runtime exceptions and handle them globally using Spring Boot's exception handling."

## Quick Revision

- Checked → Compiler enforced
- Unchecked → Runtime only
- Recoverable → Checked
- Programming errors → Unchecked
- Custom exceptions improve readability
- Prefer `RuntimeException` for business validation
- Use global exception handling
- Memory Trick: **Checked = Compiler Checks**

---

# Q6. Java's Pass-by-Value Semantics (Especially for Objects)

## What?

Java is **always pass-by-value**. Whether the method parameter is a primitive or an object reference, Java passes a **copy of the value**.

For primitive types, the actual value is copied. Changing the parameter inside the method does not affect the original variable.

For objects, the value being copied is the **reference**, not the object itself. Both the original reference and the copied reference point to the same object, so modifying the object's state is visible outside the method. However, reassigning the parameter to a new object does not affect the caller's reference.

## Why?

Pass-by-value makes parameter passing simple and predictable. Since methods receive copies, they cannot accidentally replace variables owned by the caller.

Understanding this behavior prevents common interview mistakes, especially when discussing mutable objects, collections, and method parameters.

## Key Points

- Java is always pass-by-value.
- Primitive values are copied.
- Object references are copied.
- Both references point to the same object.
- Modifying object fields affects the original object.
- Reassigning the parameter does not affect the caller.
- Java is **not** pass-by-reference.
- Strings appear unchanged because they are immutable.
- Collections behave similarly since they are mutable.
- Common mistake: saying Java passes objects by reference.

## Example

```java
class Employee {
    String name;

    Employee(String name) {
        this.name = name;
    }
}

public class Demo {

    static void update(Employee emp) {
        emp.name = "Bob";
    }

    static void replace(Employee emp) {
        emp = new Employee("Charlie");
    }

    public static void main(String[] args) {

        Employee e = new Employee("Alice");

        update(e);
        System.out.println(e.name);      // Bob

        replace(e);
        System.out.println(e.name);      // Bob
    }
}
```

## Interview Tip

"Java is always pass-by-value. For objects, the copied value is the reference, not the object itself. Therefore, modifying the object's fields is reflected outside the method, but assigning the parameter to a new object only changes the local copy of the reference."

## Quick Revision

- Java is always pass-by-value
- Primitive → value copied
- Object → reference copied
- Same object, different references
- Object state can change
- Reference cannot be replaced externally
- Java is never pass-by-reference
- Memory Trick: **Copy the Reference, Not the Object**

---

# Q7. Functional Interfaces: Runnable, Callable, Supplier, Function

## What?

A functional interface contains exactly one abstract method and can be implemented using a lambda expression or method reference. Java provides several built-in functional interfaces in `java.util.function` and `java.util.concurrent`.

`Runnable` represents a task that takes no input and returns no result.

`Callable<T>` represents a task that returns a value and can throw checked exceptions.

`Supplier<T>` supplies an object without taking any input.

`Function<T, R>` accepts one input and produces one output.

## Why?

Functional interfaces simplify code by enabling lambda expressions, improving readability and reducing boilerplate.

They are widely used in Streams, CompletableFuture, Spring Boot, asynchronous programming, and dependency injection.

## Key Points

- Functional interface has one abstract method.
- Annotate with `@FunctionalInterface`.
- `Runnable` → no return value.
- `Callable` → returns value and throws exceptions.
- `Supplier` → produces data.
- `Function` → transforms data.
- Lambdas require functional interfaces.
- Streams heavily use `Function`.
- Executors use `Runnable` and `Callable`.
- Common mistake: confusing `Runnable` with `Callable`.

## Example

```java
Supplier<String> supplier = () -> "Java";

Function<String, Integer> length = String::length;

Runnable task = () -> System.out.println("Running");

Callable<Integer> callable = () -> 100;

System.out.println(supplier.get());
System.out.println(length.apply("Spring"));
```

## Interview Tip

"`Runnable` performs work without returning anything. `Callable` performs work and returns a result while allowing checked exceptions. `Supplier` produces values, whereas `Function` transforms one object into another. These interfaces are heavily used with lambdas, Streams, and asynchronous programming."

## Quick Revision

- One abstract method
- Lambda compatible
- Runnable → Task
- Callable → Task + Result
- Supplier → Produce
- Function → Transform
- Streams use Function
- Memory Trick: **Run, Call, Supply, Transform**

---

# Q8. `final` vs `finally` vs `finalize()`

## What?

Although their names are similar, `final`, `finally`, and `finalize()` serve completely different purposes.

`final` is a keyword used to make variables constant, prevent method overriding, or prevent class inheritance.

`finally` is a block associated with exception handling that executes regardless of whether an exception occurs, making it suitable for resource cleanup.

`finalize()` was a method of `Object` that the garbage collector could invoke before reclaiming memory. It has been deprecated for removal and should never be used in modern Java.

## Why?

These features address different problems: `final` improves immutability and design safety, `finally` ensures cleanup, and `finalize()` was originally intended for cleanup but proved unreliable.

Modern Java uses **try-with-resources** instead of relying on `finally` for closing resources whenever possible.

## Key Points

- `final` is a keyword.
- `finally` belongs to exception handling.
- `finalize()` is deprecated.
- Final variables cannot be reassigned.
- Final methods cannot be overridden.
- Final classes cannot be inherited.
- `finally` usually executes even if an exception occurs.
- Prefer try-with-resources over `finally`.
- Never depend on `finalize()`.
- Common mistake: confusing `final` with `finally`.

## Example

```java
final class Utility {

    public static void process() {

        try {
            System.out.println("Processing...");
        } finally {
            System.out.println("Cleanup");
        }
    }
}
```

## Interview Tip

"`final` is used for constants and preventing inheritance or overriding. `finally` guarantees cleanup code execution after a try-catch block. `finalize()` is deprecated and should not be used; modern Java recommends try-with-resources for resource management."

## Quick Revision

- final → Restrict
- finally → Cleanup
- finalize() → Deprecated
- Final variable = constant
- Final method = cannot override
- Final class = cannot extend
- Prefer try-with-resources
- Memory Trick: **Final = Restrict, Finally = Cleanup**

---

# Q9. Primitives vs Wrapper Classes, and Autoboxing Pitfalls

## What?

Java provides eight primitive data types (`int`, `double`, `boolean`, etc.) that store values directly and are highly efficient.

Wrapper classes (`Integer`, `Double`, `Boolean`, etc.) are object representations of primitives. They allow primitive values to be used with collections, generics, and APIs requiring objects.

Autoboxing automatically converts primitives to wrappers, while unboxing converts wrappers back to primitives.

## Why?

Collections such as `List` and `Map` work only with objects, making wrapper classes essential.

Although autoboxing simplifies code, excessive boxing/unboxing can create unnecessary objects and even cause `NullPointerException` during unboxing.

## Key Points

- Primitives store values directly.
- Wrappers are objects.
- Generics require wrapper classes.
- Autoboxing is automatic conversion.
- Unboxing can throw `NullPointerException`.
- Wrappers consume more memory.
- Primitives are generally faster.
- Integer values (-128 to 127) are cached.
- Use primitives unless null is required.
- Common mistake: comparing wrappers using `==`.

## Example

```java
Integer number = 10;      // Autoboxing

int value = number;       // Unboxing

Integer a = 100;
Integer b = 100;

System.out.println(a == b);       // true (cached)

Integer x = 200;
Integer y = 200;

System.out.println(x == y);       // false
System.out.println(x.equals(y));  // true
```

## Interview Tip

"Primitives store values directly and are faster. Wrapper classes are objects required by collections and generics. Java automatically performs autoboxing and unboxing, but careless unboxing may lead to `NullPointerException`, and wrapper comparisons should use `equals()` instead of `==`."

## Quick Revision

- Primitive = Value
- Wrapper = Object
- Collections need wrappers
- Autoboxing = Primitive → Wrapper
- Unboxing = Wrapper → Primitive
- Integer cache (-128 to 127)
- Prefer primitives for performance
- Memory Trick: **Primitive = Fast, Wrapper = Flexible**

---

# Q10. Composition vs Inheritance — When Do You Prefer Composition?

## What?

Inheritance models an **is-a** relationship, where a subclass extends a superclass and inherits its behavior.

Composition models a **has-a** relationship by building classes from other objects. Instead of inheriting implementation, one object delegates work to another.

Modern object-oriented design generally prefers composition because it reduces coupling and improves flexibility.

## Why?

Inheritance tightly couples subclasses to parent implementations. Changes in the superclass can unintentionally affect all subclasses.

Composition promotes modular design, easier testing, better encapsulation, and greater flexibility. Frameworks like Spring Boot heavily rely on composition through dependency injection instead of inheritance.

## Key Points

- Inheritance → is-a relationship.
- Composition → has-a relationship.
- Composition provides loose coupling.
- Easier unit testing.
- Better encapsulation.
- Supports dependency injection.
- Avoid deep inheritance hierarchies.
- Prefer interfaces with composition.
- Spring heavily uses composition.
- Common mistake: using inheritance just for code reuse.

## Example

```java
interface Engine {
    void start();
}

class PetrolEngine implements Engine {

    @Override
    public void start() {
        System.out.println("Engine started");
    }
}

class Car {

    private final Engine engine;

    Car(Engine engine) {
        this.engine = engine;
    }

    public void start() {
        engine.start();
    }
}
```

## Interview Tip

"I prefer composition over inheritance because it creates loosely coupled and easily testable code. Inheritance is suitable only when there is a genuine 'is-a' relationship, whereas composition works better for assembling reusable components. Spring Boot's dependency injection is a practical example of composition."

## Quick Revision

- Inheritance = Is-A
- Composition = Has-A
- Composition reduces coupling
- Easier testing
- Better flexibility
- Preferred in Spring Boot
- Avoid deep inheritance
- Memory Trick: **Favor Has-A over Is-A**


# Q11. Static vs Instance Methods/Variables, and Static Initialization Order

## What?

In Java, **static members** belong to the class itself, whereas **instance members** belong to individual objects. Static variables have a single shared copy across all objects, while instance variables are unique to each object.

Static methods can access only static members directly because they execute without requiring an object. Instance methods can access both instance and static members since they are invoked on an object.

Java initializes static members when the class is first loaded into memory. This process follows a well-defined initialization order, ensuring static variables and blocks are initialized before any object is created.

## Why?

Static members are useful for data or behavior common to all objects, such as utility methods (`Math.max()`), constants, counters, or singleton instances.

Instance members represent object-specific state and behavior. Choosing between static and instance members improves code organization, memory usage, and object-oriented design.

## Key Points

- Static members belong to the class.
- Instance members belong to objects.
- Static variables have only one shared copy.
- Instance variables are unique per object.
- Static methods cannot directly access instance variables.
- Instance methods can access both static and instance members.
- Static initialization occurs once when the class is loaded.
- Static methods cannot use `this` or `super`.
- Prefer static methods for utility functionality.
- Common mistake: accessing instance members directly from static methods.

## Example

```java
class Employee {

    static int employeeCount = 0;
    String name;

    static {
        System.out.println("Static block executed");
    }

    Employee(String name) {
        this.name = name;
        employeeCount++;
    }

    static void printCount() {
        System.out.println(employeeCount);
    }

    void printName() {
        System.out.println(name);
    }
}
```

### Static Initialization Order

```text
1. Static variables (in declaration order)
2. Static initialization blocks
3. main() starts
4. Object creation
5. Instance variables
6. Instance initialization blocks
7. Constructor
```

## Interview Tip

"Static members belong to the class and are loaded once when the class is initialized. Instance members belong to individual objects. Static methods can access only static members directly, whereas instance methods can access both. Java initializes static variables and static blocks before any object is created."

## Quick Revision

- Static → Class level
- Instance → Object level
- Static variable → One copy
- Instance variable → One per object
- Static methods cannot use `this`
- Static initialization happens once
- Utility methods are usually static
- Memory Trick: **Static = Shared, Instance = Separate**

---

# Q12. The Diamond Problem — How Does Java Resolve It with Default Methods?

## What?

The **diamond problem** occurs when a class inherits the same method implementation from multiple parent types, creating ambiguity about which implementation should be used.

Java avoids this problem for classes because it does not support multiple inheritance of classes. However, since Java 8 introduced **default methods** in interfaces, ambiguity can occur when multiple interfaces define the same default method.

Java resolves this by requiring the implementing class to explicitly override the conflicting method.

## Why?

Default methods allow interfaces to evolve without breaking existing implementations. The explicit override rule prevents ambiguity and ensures developers choose the desired implementation.

This approach provides many benefits of multiple inheritance without the complexity found in languages that support multiple class inheritance.

## Key Points

- Java does not support multiple inheritance of classes.
- Diamond problem occurs with multiple default methods.
- Compiler forces explicit override.
- Interface methods can be called using `InterfaceName.super.method()`.
- Class methods always take precedence over interface default methods.
- More specific interfaces take precedence over parent interfaces.
- Default methods improve backward compatibility.
- Common mistake: assuming Java allows multiple class inheritance.
- Interface conflicts are resolved at compile time.
- Frequently asked after default methods.

## Example

```java
interface A {

    default void show() {
        System.out.println("A");
    }
}

interface B {

    default void show() {
        System.out.println("B");
    }
}

class Demo implements A, B {

    @Override
    public void show() {
        A.super.show();
    }
}
```

## Interview Tip

"Java doesn't support multiple inheritance of classes, so the classic diamond problem doesn't exist there. With interface default methods, if two interfaces provide the same default implementation, the implementing class must override the method and explicitly choose which implementation to use."

## Quick Revision

- No multiple inheritance of classes
- Default methods can conflict
- Override resolves ambiguity
- Use `Interface.super.method()`
- Class methods have higher priority
- Compiler detects conflicts
- Default methods improve compatibility
- Memory Trick: **Two Defaults → Override Required**

---

# Q13. Designing an Immutable Class in Java

## What?

An immutable class is one whose state cannot change after object creation. Once an object is constructed, its fields remain constant throughout its lifetime.

Examples include `String`, wrapper classes, and Java Records. Immutable objects are naturally thread-safe because no synchronization is required after construction.

To create an immutable class, prevent external modification of its internal state and expose data safely.

## Why?

Immutable objects eliminate many concurrency problems, simplify debugging, and make objects safe to cache or share across threads.

They are widely used for value objects, configuration classes, DTOs, money objects, and cache keys.

## Key Points

- Declare the class as `final`.
- Make all fields `private final`.
- Initialize fields through the constructor.
- Do not provide setters.
- Return defensive copies of mutable objects.
- Perform defensive copying in constructors.
- Prefer immutable field types.
- Records are preferred for immutable data carriers.
- Thread-safe by design.
- Common mistake: exposing mutable collections directly.

## Example

```java
import java.util.List;

public final class Employee {

    private final int id;
    private final String name;
    private final List<String> skills;

    public Employee(int id, String name, List<String> skills) {
        this.id = id;
        this.name = name;
        this.skills = List.copyOf(skills);
    }

    public int getId() {
        return id;
    }

    public List<String> getSkills() {
        return List.copyOf(skills);
    }
}
```

## Interview Tip

"To design an immutable class, I make the class final, declare all fields private and final, initialize them through the constructor, avoid setters, and defensively copy mutable fields. Immutable objects are thread-safe and work well as cache keys and value objects."

## Quick Revision

- Final class
- Private final fields
- Constructor initialization
- No setters
- Defensive copies
- Thread-safe
- Prefer Records when appropriate
- Memory Trick: **Final + Private + No Setter = Immutable**

---

# Q14. Shallow Copy vs Deep Copy, and Implementing `clone()` Correctly

## What?

A **shallow copy** copies the object itself but shares references to nested mutable objects. Changes to shared objects affect both copies.

A **deep copy** creates completely independent copies of both the object and all nested mutable objects.

Java provides the `clone()` method through the `Cloneable` interface, but it performs only a shallow copy by default.

## Why?

Deep copies prevent unintended side effects when objects contain mutable state.

Modern Java generally avoids `clone()` because it has design limitations. Production code usually prefers copy constructors, factory methods, or builder patterns.

## Key Points

- Shallow copy shares referenced objects.
- Deep copy duplicates referenced objects.
- `Object.clone()` performs shallow copy.
- Implement `Cloneable` to enable cloning.
- Override `clone()` carefully.
- Deep copy nested mutable fields manually.
- Copy constructors are preferred.
- Immutable objects do not require deep copying.
- Builder pattern is often cleaner.
- Common mistake: assuming `clone()` performs deep copy.

## Example

```java
class Address {

    String city;

    Address(String city) {
        this.city = city;
    }
}

class Employee {

    String name;
    Address address;

    Employee(String name, Address address) {
        this.name = name;
        this.address = new Address(address.city);
    }

    Employee(Employee other) {
        this(other.name, other.address);
    }
}
```

## Interview Tip

"`clone()` performs only a shallow copy by default, so mutable objects remain shared. In production applications, I usually prefer copy constructors or builder patterns because they are simpler, safer, and easier to maintain."

## Quick Revision

- Shallow → Shared references
- Deep → Independent objects
- clone() → Shallow copy
- Copy nested mutable objects
- Prefer copy constructors
- Immutable objects are safe
- Builder is often preferred
- Memory Trick: **Shallow Shares, Deep Duplicates**

---

# Q15. Enums Beyond Constants — Can They Implement Interfaces or Have Methods?

## What?

Java enums are special classes that represent a fixed set of constants. Unlike many languages, enums can contain fields, constructors, methods, and even implement interfaces.

Each enum constant is actually an object, allowing behavior to be associated with constants rather than using large `switch` statements.

Enums cannot extend another class because they already extend `java.lang.Enum`.

## Why?

Enums improve type safety by preventing invalid values while allowing behavior to remain close to the data.

They are commonly used for application states, payment methods, user roles, order statuses, and strategy implementations.

## Key Points

- Enums are special classes.
- Enum constants are objects.
- Can have constructors.
- Can have fields and methods.
- Can implement interfaces.
- Cannot extend another class.
- Constructors are implicitly private.
- Often replace integer constants.
- Frequently used with `switch`.
- Common mistake: thinking enums only store constants.

## Example

```java
interface Discount {

    double apply(double amount);
}

enum Membership implements Discount {

    SILVER {
        public double apply(double amount) {
            return amount * 0.95;
        }
    },

    GOLD {
        public double apply(double amount) {
            return amount * 0.90;
        }
    };
}
```

## Interview Tip

"Enums are much more than constants. They are full-fledged classes that can have fields, constructors, methods, and even implement interfaces. This makes them ideal for representing fixed business states while keeping related behavior inside the enum itself."

## Quick Revision

- Enum = Special class
- Constants are objects
- Can have methods
- Can have constructors
- Can implement interfaces
- Cannot extend classes
- Constructors are private
- Memory Trick: **Enum = Class with Fixed Objects**