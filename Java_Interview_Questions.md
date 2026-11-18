# Top 30 Java Interview Questions and Answers for Freshers

## 1. What is Java?

Java is a high-level, object-oriented, class-based programming language developed by Sun Microsystems in 1995.

It is widely used for developing web applications, desktop applications, mobile applications, and enterprise applications.

**Key points:**
- Object-oriented programming language.
- Platform-independent.
- Secure and robust.
- Supports multithreading.
- Used for backend development.

## 2. What are the features of Java?

The important features of Java are:

1. **Simple:** Easy-to-understand syntax.
2. **Object-oriented:** Supports classes and objects.
3. **Platform-independent:** Java bytecode runs on different operating systems using JVM.
4. **Secure:** Provides bytecode verification and runtime security.
5. **Robust:** Supports exception handling and automatic memory management.
6. **Multithreaded:** Supports executing multiple tasks simultaneously.
7. **Portable:** Java programs can run on different platforms.
8. **High performance:** JIT compilation improves execution speed.

## 3. Why is Java platform-independent?

Java is platform-independent because Java source code is compiled into bytecode instead of machine-specific code.

This bytecode can run on any operating system that has a compatible JVM.

**Execution process:**

1. Java source code (`.java`) is written.
2. Java compiler (`javac`) converts it into bytecode.
3. Bytecode is stored in `.class` files.
4. JVM executes the bytecode.

**Remember:** Write Once, Run Anywhere (WORA).

## 4. What is JVM, JRE and JDK?

These three are important components of Java.

| Component | Meaning | Purpose |
|---|---|---|
| JVM | Java Virtual Machine | Executes Java bytecode |
| JRE | Java Runtime Environment | Provides the environment to run Java applications |
| JDK | Java Development Kit | Provides tools to develop and run Java applications |

**JVM:**
- Executes bytecode.
- Manages memory.
- Performs garbage collection.

**JRE:**
- Contains JVM and runtime libraries.
- Provides the environment required to run Java applications.

**JDK:**
- Contains development tools.
- Includes the Java compiler (`javac`).
- Used to develop and run Java applications.

**Relationship:** JDK contains the runtime environment, and the runtime environment includes the JVM.

## 5. What is the difference between `==` and `.equals()`?

Both are used for comparison, but they work differently.

- `==` compares primitive values or checks whether two object references point to the same object.
- `.equals()` compares object contents when the class provides an appropriate implementation.

**Example:**

```java
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1 == s2);
System.out.println(s1.equals(s2));
```

**Output:**

```text
false
true
```

**Explanation:**
- `s1 == s2` returns false because they refer to different objects.
- `s1.equals(s2)` returns true because their contents are the same.

## 6. What is the difference between method overloading and overriding?

Both are examples of polymorphism in Java.

| Method Overloading | Method Overriding |
|---|---|
| Same method name with different parameter lists | Subclass provides a new implementation of an inherited method |
| Usually occurs within the same class | Requires inheritance |
| Compile-time polymorphism | Runtime polymorphism |
| Inheritance is not required | Inheritance is required |
| Return type alone cannot distinguish overloaded methods | Return type must be compatible |

**Overloading example:**

```java
class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

**Overriding example:**

```java
class Animal {

    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}
```

## 7. What is OOP?

OOP stands for Object-Oriented Programming.

It is a programming approach based on classes and objects.

It helps us write reusable, maintainable, and organized code.

Java supports four main pillars of OOP:

1. Encapsulation
2. Inheritance
3. Polymorphism
4. Abstraction

## 8. Explain the four pillars of OOP.

The four pillars of OOP are:

### 1. Encapsulation

Wrapping data and methods into a single unit and controlling access to data using access modifiers.

### 2. Inheritance

One class acquires the properties and methods of another class using the `extends` keyword.

### 3. Polymorphism

One thing can have multiple forms. It allows the same method name to behave differently.

### 4. Abstraction

Hiding implementation details and showing only essential functionality.

**Real-world example: Car**

- Encapsulation: Engine data is protected.
- Inheritance: Different car models inherit common vehicle features.
- Polymorphism: Different vehicles implement the same `start()` operation differently.
- Abstraction: We use the steering wheel and pedals without knowing the internal engine implementation.

## 9. What is inheritance?

Inheritance is an OOP concept where one class acquires the properties and methods of another class.

It helps achieve code reusability.

In Java, we use the `extends` keyword for class inheritance.

**Example:**

```java
class Animal {

    void eat() {
        System.out.println("Eating");
    }
}

class Dog extends Animal {

    void bark() {
        System.out.println("Barking");
    }
}

public class Main {

    public static void main(String[] args) {

        Dog d = new Dog();

        d.eat();
        d.bark();
    }
}
```

**Output:**

```text
Eating
Barking
```

**Types of inheritance:**
1. Single inheritance
2. Multilevel inheritance
3. Hierarchical inheritance

Java does not support multiple inheritance through classes, but it supports multiple inheritance of type through interfaces.

## 10. What is polymorphism?

Polymorphism means one thing having many forms.

In Java, polymorphism allows the same method name or reference type to perform different operations depending on the situation.

There are two types:

1. **Compile-time polymorphism:** Achieved through method overloading.
2. **Runtime polymorphism:** Achieved through method overriding.

**Example:**

```java
class Animal {

    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {

    public static void main(String[] args) {

        Animal a = new Dog();

        a.sound();
    }
}
```

**Output:**

```text
Dog barks
```

Here, the parent class reference points to a child class object. The overridden method is called at runtime.

## 11. What is abstraction?

Abstraction is the process of hiding implementation details and showing only essential functionality to the user.

In Java, abstraction can be achieved using:
- Abstract classes.
- Interfaces.

**Real-world example:**

When we drive a car, we use the steering wheel, accelerator, and brakes. We don't need to know the internal working of the engine.

**Example:**

```java
abstract class Vehicle {

    abstract void start();
}

class Car extends Vehicle {

    @Override
    void start() {
        System.out.println("Car starts");
    }
}
```

## 12. What is encapsulation?

Encapsulation is the process of wrapping data and methods into a single unit and restricting direct access to the data.

In Java, we achieve encapsulation using:
- Private variables.
- Public getter and setter methods.

**Example:**

```java
class Student {

    private int age;

    public void setAge(int age) {
        this.age = age;
    }

    public int getAge() {
        return age;
    }
}
```

Here, the variable `age` is private and can be accessed through getter and setter methods.

**Benefits:**
- Data security.
- Controlled access.
- Better maintainability.

## 13. What is an interface?

An interface is a reference type in Java that defines a contract that implementing classes must follow.

We use the `interface` keyword to create an interface and the `implements` keyword to implement it.

**Example:**

```java
interface Animal {

    void sound();
}

class Dog implements Animal {

    public void sound() {
        System.out.println("Dog barks");
    }
}
```

**Important points:**
- A class can implement multiple interfaces.
- Interface abstract methods are implicitly public and abstract.
- Interfaces can contain default, static, and private methods.
- Interface fields are implicitly public, static, and final.

## 14. What is an abstract class?

An abstract class is a class declared using the `abstract` keyword.

It cannot be instantiated directly.

It can contain:
- Abstract methods.
- Concrete methods.
- Constructors.
- Instance variables.
- Static methods.

**Example:**

```java
abstract class Animal {

    abstract void sound();

    void eat() {
        System.out.println("Eating");
    }
}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Barking");
    }
}
```

## 15. Difference between interface and abstract class?

| Interface | Abstract Class |
|---|---|
| Created using `interface` | Created using `abstract class` |
| Implemented using `implements` | Extended using `extends` |
| A class can implement multiple interfaces | A class can extend only one class |
| Cannot have constructors | Can have constructors |
| Fields are implicitly public, static and final | Can have instance and static variables |
| Supports abstract, default, static and private methods | Supports abstract and concrete methods |

**When to use?**

- Use an interface when you want to define a common contract for different classes.
- Use an abstract class when you want to share common state and implementation among related classes.

## 16. Difference between `final`, `finally` and `finalize()`?

These three look similar but have different purposes.

| final | finally | finalize() |
|---|---|---|
| Keyword | Block | Method |
| Used to restrict changes | Used in exception handling | Historically associated with garbage collection |
| A final variable cannot be reassigned | Usually executes after try/catch | Could be called before object reclamation |
| A final method cannot be overridden | Used for cleanup code | Deprecated for removal |

**final example:**

```java
final int x = 10;
// x = 20; // Compilation error
```

**finally example:**

```java
try {
    int a = 10 / 2;
}
catch (Exception e) {
    System.out.println(e);
}
finally {
    System.out.println("Finally block");
}
```

**finalize():**

It was historically used for cleanup before garbage collection, but it is deprecated for removal and should not be used in modern Java.

## 17. What is a constructor?

A constructor is a special member of a class used to initialize objects.

**Important points:**
- Constructor name must be the same as the class name.
- It does not have a return type, not even `void`.
- It is automatically invoked when an object is created.
- Constructors can be overloaded.

**Example:**

```java
class Student {

    String name;

    Student() {
        name = "Java";
    }

    void display() {
        System.out.println(name);
    }
}

public class Main {

    public static void main(String[] args) {

        Student s = new Student();

        s.display();
    }
}
```

**Output:**

```text
Java
```

## 18. Can a constructor be overloaded?

Yes. Constructor overloading is possible in Java.

We can create multiple constructors in the same class with different parameter lists.

**Example:**

```java
class Student {

    String name;
    int age;

    Student() {
        name = "Unknown";
        age = 0;
    }

    Student(String name) {
        this.name = name;
    }

    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

Here, we have three constructors with different parameter lists.

## 19. What is the difference between static and non-static methods?

| Static Method | Non-static Method |
|---|---|
| Belongs to the class | Belongs to an instance |
| Called using class name | Usually called using an object |
| Does not require an object | Requires an object |
| Can directly access only static members | Can access both static and instance members |
| Cannot use `this` keyword | Can use `this` keyword |

**Example:**

```java
class Demo {

    static void display1() {
        System.out.println("Static method");
    }

    void display2() {
        System.out.println("Non-static method");
    }
}

public class Main {

    public static void main(String[] args) {

        Demo.display1();

        Demo d = new Demo();
        d.display2();
    }
}
```

## 20. What is the String class?

String is a predefined class in Java used to store a sequence of characters.

Strings are immutable, which means once a String object is created, its value cannot be changed.

**Example:**

```java
String name = "Java";

System.out.println(name.length());
System.out.println(name.toUpperCase());
```

**Output:**

```text
4
JAVA
```

Strings can be created using string literals or the `new` keyword.

## 21. Difference between String, StringBuilder and StringBuffer?

All three are used to work with strings, but they differ in mutability and thread safety.

| String | StringBuilder | StringBuffer |
|---|---|---|
| Immutable | Mutable | Mutable |
| Cannot modify existing object | Can modify existing object | Can modify existing object |
| Not designed for mutable operations | Not synchronized | Synchronized |
| Suitable for fixed text | Suitable for frequent modifications | Suitable for synchronized mutable operations |

**StringBuilder example:**

```java
StringBuilder sb = new StringBuilder("Java");

sb.append(" Programming");

System.out.println(sb);
```

**Output:**

```text
Java Programming
```

**Remember:**
- String: When the value should not change.
- StringBuilder: When frequent modifications are needed in a single-threaded context.
- StringBuffer: When synchronized mutable string operations are required.

## 22. Why is String immutable in Java?

String is immutable in Java, meaning its value cannot be changed after creation.

**Important reasons:**

1. **Security:** Helps protect sensitive string values used in paths, class loading, and other operations.
2. **Thread safety:** Multiple threads can safely share String objects.
3. **String pool:** Allows Java to reuse String objects efficiently.
4. **HashCode caching:** Helps improve performance when Strings are used as HashMap keys.

**Example:**

```java
String s = "Hello";

s.concat(" Java");

System.out.println(s);
```

**Output:**

```text
Hello
```

The `concat()` method creates a new String rather than modifying the original String.

To get the modified value:

```java
s = s.concat(" Java");
```

## 23. What is exception handling?

Exception handling is a mechanism used to handle runtime problems so that the normal flow of a program can be maintained.

Java provides five important keywords:

1. `try` – Contains code that may cause an exception.
2. `catch` – Handles the exception.
3. `finally` – Executes cleanup code.
4. `throw` – Explicitly throws an exception.
5. `throws` – Declares exceptions that a method may pass to its caller.

**Example:**

```java
public class Main {

    public static void main(String[] args) {

        try {
            int result = 10 / 0;
        }
        catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero");
        }
        finally {
            System.out.println("Program completed");
        }
    }
}
```

**Output:**

```text
Cannot divide by zero
Program completed
```

## 24. Difference between checked and unchecked exceptions?

| Checked Exception | Unchecked Exception |
|---|---|
| Checked at compile time | Not checked at compile time |
| Must be caught or declared | Catching or declaring is not mandatory |
| Subclasses of Exception excluding RuntimeException | Subclasses of RuntimeException |
| Example: IOException | Example: NullPointerException |

**Checked exception example:**

```java
import java.io.*;

class Main {

    public static void main(String[] args) {

        try {
            FileReader fr = new FileReader("test.txt");
        }
        catch (IOException e) {
            System.out.println(e);
        }
    }
}
```

**Unchecked exception example:**

```java
public class Main {

    public static void main(String[] args) {

        int a = 10 / 0;
    }
}
```

This causes `ArithmeticException`.

## 25. Difference between `throw` and `throws`?

| throw | throws |
|---|---|
| Used to explicitly throw an exception | Used to declare possible exceptions |
| Used inside a method or block | Used in a method or constructor declaration |
| Followed by an exception object | Followed by exception class names |

**throw example:**

```java
class Main {

    public static void main(String[] args) {

        int age = 15;

        if (age < 18) {
            throw new ArithmeticException("Not eligible");
        }
    }
}
```

**throws example:**

```java
import java.io.*;

class Main {

    static void readFile() throws IOException {
        FileReader fr = new FileReader("test.txt");
    }
}
```

## 26. What is the Collections Framework?

The Java Collections Framework is a set of classes and interfaces used to store and manipulate groups of objects.

It provides ready-made data structures and algorithms.

**Important interfaces:**
- List
- Set
- Queue
- Map (part of the Collections Framework, but not a subtype of Collection)

**Important classes:**
- ArrayList
- LinkedList
- HashSet
- TreeSet
- HashMap
- Hashtable
- PriorityQueue

**Benefits:**
- Code reusability.
- Dynamic data storage.
- Easy data manipulation.
- Built-in searching and sorting operations.

## 27. Difference between ArrayList and LinkedList?

Both implement the List interface.

| ArrayList | LinkedList |
|---|---|
| Uses a dynamic array | Uses a doubly linked list |
| Fast random access | Slow random access |
| Usually faster for retrieving elements by index | Usually slower for retrieving elements by index |
| Insertions and deletions in the middle may require shifting elements | Insertions and deletions can be efficient when the position is already reached |
| Uses less memory per element in typical implementations | Requires extra memory for links |

**Example:**

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        ArrayList<String> list = new ArrayList<>();

        list.add("Java");
        list.add("Python");
        list.add("React");

        System.out.println(list);
    }
}
```

**Output:**

```text
[Java, Python, React]
```

**Remember:** Use ArrayList when frequent index-based access is required. LinkedList may be useful for frequent insertions or removals at known positions or at the ends, depending on the workload.

## 28. Difference between HashMap and Hashtable?

Both are used to store data in key-value pairs.

| HashMap | Hashtable |
|---|---|
| Not synchronized | Synchronized |
| Not thread-safe by default | Thread-safe for individual operations |
| Allows one null key | Does not allow null keys |
| Allows multiple null values | Does not allow null values |
| Generally faster in single-threaded usage | Generally slower due to synchronization |
| Modern collection class | Legacy class |

**Example:**

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        HashMap<Integer, String> map = new HashMap<>();

        map.put(1, "Java");
        map.put(2, "Python");

        System.out.println(map);
    }
}
```

**Output:**

```text
{1=Java, 2=Python}
```

## 29. How does HashMap work internally?

**Important interview question.**

HashMap internally uses an array of buckets. Each bucket can contain entries stored as nodes.

**When we insert a key-value pair:**

1. HashMap calculates the hash code of the key.
2. It uses the hash to determine the bucket index.
3. It stores the key-value pair in that bucket.
4. If multiple keys map to the same bucket, a collision occurs.
5. HashMap handles collisions using a linked list and, under certain conditions, a balanced tree (typically a red-black tree).

**Example:**

```java
HashMap<Integer, String> map = new HashMap<>();

map.put(1, "Java");
map.put(2, "Python");
map.put(3, "React");
```

**How does HashMap retrieve a value?**

When we call:

```java
map.get(1);
```

HashMap:

1. Calculates the hash of key `1`.
2. Finds the corresponding bucket.
3. Compares keys using `equals()`.
4. Returns the associated value if the key is found.

**Important additional points:**

- Default initial capacity is 16.
- Default load factor is 0.75.
- When the threshold is exceeded, the HashMap resizes.
- Average time complexity of `put()` and `get()` is O(1), assuming good hash distribution.
- In Java 8+, sufficiently large collision chains can be converted into balanced trees under specified conditions.

## 30. Difference between List, Set and Map?

These are three important interfaces in the Java Collections Framework.

| List | Set | Map |
|---|---|---|
| Stores elements | Stores unique elements | Stores key-value pairs |
| Allows duplicates | Does not allow duplicates | Keys must be unique |
| Maintains insertion order in common implementations | Ordering depends on implementation | Ordering depends on implementation |
| Supports index-based access | Does not support index-based access | Accesses values using keys |
| Example: ArrayList | Example: HashSet | Example: HashMap |

**Example:**

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        // List
        List<String> list = new ArrayList<>();
        list.add("Java");
        list.add("Java");

        // Set
        Set<String> set = new HashSet<>();
        set.add("Java");
        set.add("Java");

        // Map
        Map<Integer, String> map = new HashMap<>();
        map.put(1, "Java");
        map.put(2, "Python");

        System.out.println(list);
        System.out.println(set);
        System.out.println(map);
    }
}
```

**Output (illustrative):**

```text
[Java, Java]
[Java]
{1=Java, 2=Python}
```

---

# Additional Important Java Interview Topics

After completing these 30 questions, prepare the following topics:

| Topic | Important Concepts |
|---|---|
| Java 8 | Lambda expressions, Stream API, Functional interfaces |
| Multithreading | Thread, Runnable, synchronization |
| Memory Management | Heap, Stack, Garbage Collection |
| Access Modifiers | public, private, protected, default |
| Arrays | Searching, sorting, reversing |
| Java Coding | Palindrome, Fibonacci, prime number, duplicate elements |
| Collections | HashSet, TreeMap, Iterator |
| Java Keywords | this, super, static, final |

# Interview Preparation Tips

1. Understand each concept instead of memorizing answers.
2. Practice writing the code examples yourself.
3. Understand the differences between similar concepts.
4. Practice explaining your answers aloud.
5. Prepare to explain your own projects.
6. Practice Java coding programs every day.

**Important:** For fresher interviews, focus on Core Java fundamentals, OOP concepts, Collections, Exception Handling, Java 8, and basic coding problems.
