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