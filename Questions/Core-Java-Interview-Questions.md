---------------------------------------------
# CORE JAVA 


### 1. What is the difference between `String`, `StringBuilder`, and `StringBuffer`?

   - **Answer:**
     - `String` is immutable, meaning once created, its value cannot be changed.
     - `StringBuilder` is mutable and more efficient for concatenating strings in a single thread.
     - `StringBuffer` is similar to `StringBuilder` but is synchronized, making it thread-safe.

### 2. Explain the concept of method overloading in Java.

   - **Answer:**
     - Method overloading allows defining multiple methods with the same name but different parameters.
     - Parameters can differ in type, number, or both.
     - Overloaded methods are differentiated based on the method signature.

```java
class OverloadingExample {
    void display(int num) {
        System.out.println("Method with int parameter: " + num);
    }

    void display(String text) {
        System.out.println("Method with String parameter: " + text);
    }
}
```

### 3. What is the `super` keyword used for in Java?

   - **Answer:**
     - `super` is used to refer to the superclass (parent class) members in a subclass.
     - It is often used to invoke the superclass's methods, variables, or constructor.
     - Helps avoid ambiguity when subclass and superclass have members with the same name.

```java
class Animal {
    void eat() {
        System.out.println("Animal is eating");
    }
}

class Dog extends Animal {
    void eat() {
        super.eat(); // invoking superclass method
        System.out.println("Dog is eating");
    }
}
```

### 4. Explain the `static` keyword in Java.

   - **Answer:**
     - `static` is used to declare a variable or method as a class-level entity.
     - Static variables are shared among all instances of a class.
     - Static methods belong to the class rather than an instance and can be called without creating an object.

```java
class Example {
    static int count = 0; // static variable

    static void incrementCount() { // static method
        count++;
    }
}
```

### 5. How does exception handling work in Java? Provide an example.

   - **Answer:**
     - Exceptions are events that occur during the execution of a program, disrupting normal flow.
     - Java uses `try`, `catch`, and `finally` blocks for exception handling.
     - Example:

```java
try {
    // code that may throw an exception
    int result = 10 / 0; // ArithmeticException
} catch (ArithmeticException e) {
    // handle the exception
    System.out.println("Error: Division by zero");
} finally {
    // optional block executed regardless of whether an exception is caught
    System.out.println("Finally block executed");
}
```

### 6. What is the purpose of the `equals` method? How is it different from `==`?

   - **Answer:**
     - The `equals` method is used to compare the content or values of objects.
     - The `==` operator compares object references for equality.
     - Overriding `equals` allows custom comparison logic.

```java
String str1 = new String("Hello");
String str2 = new String("Hello");

// Using equals method
boolean isEqual = str1.equals(str2); // true

// Using == operator
boolean isSameReference = (str1 == str2); // false
```

### 7. Explain the concept of polymorphism in Java.

   - **Answer:**
     - Polymorphism allows objects of different types to be treated as objects of a common type.
     - In Java, polymorphism is achieved through method overloading and method overriding.
     - It enhances code reusability and flexibility.

```java
class Animal {
    void makeSound() {
        System.out.println("Some generic sound");
    }
}

class Dog extends Animal {
    void makeSound() {
        System.out.println("Bark");
    }
}

Animal myDog = new Dog(); // Polymorphic behavior
myDog.makeSound(); // Calls Dog's makeSound method
```

### 8. What is the `this` keyword used for in Java?

   - **Answer:**
     - `this` is a reference to the current instance of the class.
     - It is used to differentiate instance variables from parameters in a constructor or method.
     - Helps avoid naming conflicts within a class.

```java
class Example {
    private int number;

    Example(int number) {
        this.number = number; // using this to refer to instance variable
    }
}
```

### 9. What is an abstract class, and how is it different from an interface?

   - **Answer:**
     - An abstract class is a class that cannot be instantiated and may contain abstract methods.
     - Abstract methods are declared without implementation and must be implemented by subclasses.
     - Interfaces only declare abstract methods and are implemented by classes.

```java
abstract class Shape {
    abstract void draw(); // abstract method
}

interface Drawable {
    void draw(); // abstract method in an interface
}
```

### 10. How does multithreading work in Java? Provide an example.

   - **Answer:**
     - Multithreading allows concurrent execution of multiple threads within a program.
     - Java supports multithreading through the `Thread` class or implementing the `Runnable` interface.
     - Example:

```java
class MyThread extends Thread {
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println(Thread.currentThread().getId() + " Value " + i);
        }
    }
}

public class Example {
    public static void main(String args[]) {
        MyThread t1 = new MyThread();
        t1.start();
    }
}
```

### 11. What is the purpose of the `hashCode` method in Java?

   - **Answer:**
     - `hashCode` is a method in the `Object` class used to generate a unique integer code for an object.
     - It is often overridden in classes that override the `equals` method.
     - Used in hash-based collections like `HashMap` for efficient retrieval.

```java
class Example {
    private String name;

    @Override
    public int hashCode() {
        return name.hashCode(); // custom hash code implementation
    }
}
```

### 12. Explain the concept of the `finalize` method in Java.

   - **Answer:**
     - The `finalize` method is called by the garbage collector before reclaiming an object's memory.
     - It allows an object to perform cleanup operations before being garbage collected.
     - However, its usage is discouraged, and the `try-with-resources` statement is preferred for resource management.

```java
class Example {
    protected void finalize() throws Throwable {
        // cleanup operations
        super.finalize();
    }
}
```

### 13. How does the `super()` constructor call work in Java?

   - **Answer:**
     - `super()` is used to call the constructor of the superclass from the subclass.
     - It must be the first statement in the subclass constructor.
     - If not explicitly called, the compiler inserts a default ` constructor call to the superclass's no-argument constructor.

```java
class Animal {
    Animal() {
        System.out.println("Animal constructor");
    }
}

class Dog extends Animal {
    Dog() {
        super(); // calling the constructor of the superclass
        System.out.println("Dog constructor");
    }
}
```

### 14. What is the `instanceof` operator used for in Java?

   - **Answer:**
     - The `instanceof` operator is used to test whether an object is an instance of a particular class or interface.
     - It returns `true` if the object is an instance; otherwise, it returns `false`.
     - Useful for type checking before casting objects.

```java
class Example {
    public static void main(String[] args) {
        Object obj = "Hello";
        if (obj instanceof String) {
            String str = (String) obj; // safe casting
            System.out.println("Length of the string: " + str.length());
        }
    }
}
```

### 15. Explain the purpose of the `transient` keyword in Java.

   - **Answer:**
     - The `transient` keyword is used to indicate that a variable should not be serialized.
     - When an object is serialized, transient variables are ignored.
     - Useful for excluding sensitive or non-serializable information during object serialization.

```java
import java.io.Serializable;

class Example implements Serializable {
    transient int sensitiveData; // transient variable
    int regularData;
}
```

### 16. How does autoboxing and unboxing work in Java?

   - **Answer:**
     - Autoboxing is the automatic conversion of primitive data types to their corresponding wrapper classes.
     - Unboxing is the automatic conversion of wrapper class objects to their primitive data types.
     - Simplifies code by allowing the use of primitive types in collections that require objects.

```java
// Autoboxing
Integer intValue = 42; // int to Integer

// Unboxing
int primitiveValue = intValue; // Integer to int
```

### 17. What is the purpose of the `assert` statement in Java?

   - **Answer:**
     - The `assert` statement is used for debugging and testing purposes.
     - It allows you to test assumptions about your code during development.
     - Assertions can be enabled or disabled at runtime using the `-ea` or `-da` JVM options.

```java
int age = -1;
assert age >= 0 : "Age cannot be negative"; // Assertion with an error message
```

### 18. Explain the concept of lambda expressions in Java.

   - **Answer:**
     - Lambda expressions introduce functional programming features to Java.
     - They provide a concise way to express anonymous functions (functional interfaces).
     - Lambda expressions are often used with Java's functional interfaces and in stream operations.

```java
// Before Java 8
Runnable runnable = new Runnable() {
    public void run() {
        System.out.println("Hello");
    }
};

// With Lambda Expression
Runnable runnableLambda = () -> System.out.println("Hello");
```

### 19. How does the `try-with-resources` statement improve resource management?

   - **Answer:**
     - `try-with-resources` is used for automatic resource management in Java.
     - It ensures that each resource (implementing `AutoCloseable` or `Closeable`) is closed after the try block, even if an exception occurs.
     - Simplifies code and reduces the chance of resource leaks.

```java
try (FileReader fr = new FileReader("example.txt");
     BufferedReader br = new BufferedReader(fr)) {
    // code that uses FileReader and BufferedReader
} catch (IOException e) {
    // handle exception
}
```

### 20. What is the purpose of the `enum` keyword in Java?

   - **Answer:**
     - The `enum` keyword is used to define an enumeration, a special kind of class.
     - Enums can have constants, methods, and constructors.
     - They provide a way to represent a fixed set of values.

```java
enum Day {
    SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY;
}
```

### 21. Explain the concept of method references in Java.

   - **Answer:**
     - Method references provide a shorthand notation to refer to methods using `::` syntax.
     - They are often used in lambda expressions to call methods directly.
     - There are four types of method references: static, instance, constructor, and arbitrary object method references.

```java
// Static Method Reference
List<String> names = Arrays.asList("John", "Jane", "Doe");
names.forEach(System.out::println); // equivalent to: names.forEach(name -> System.out.println(name))
```

### 22. What is the purpose of the `package` statement in Java?

   - **Answer:**
     - The `package` statement is used to organize related classes into a namespace.
     - It helps avoid naming conflicts and provides a structured way to manage code.
     - Packages can be hierarchical, allowing subpackages.

```java
package com.example;

public class MyClass {
    // class implementation
}
```

### 23. How does the `Collections` framework differ from arrays in Java?

   - **Answer:**
     - Arrays are fixed in size, while collections in the `Collections` framework are dynamic and can grow or shrink.
     - Collections provide high-level interfaces and classes for working with groups of objects.
     - Arrays can store primitive types directly, while collections work with objects.

```java
// Using List from Collections framework
List<String> namesList = new ArrayList<>();
namesList.add("John");
namesList.add("Jane");

// Using an array
String[] namesArray = new String[]{"John", "Jane"};
```

### 24. Explain the concept of a wildcard in generics in Java.

   - **Answer:**
     - Wildcards in generics allow flexibility in specifying generic types.
     - The wildcard `?` represents an unknown type.
     - `<? extends T>` is an upper-bounded wildcard, and `<? super T>` is a lower-bounded wildcard.

```java
// Upper-bounded wildcard
List<? extends Number> numbers = new ArrayList<>();
// Lower-bounded wildcard
List<? super Integer> integerList = new ArrayList<>();
```

### 25. What is the purpose of the `java.util.stream` package?

   - **Answer:**
     - The `java.util.stream` package provides a framework for processing sequences of elements using a functional programming approach.
     - It introduces the Stream API, which allows declarative processing on collections.
     - Stream operations can be parallelized, enhancing performance.

```java
List<String> names = Arrays.asList("John", "Jane", "Doe");

// Using Stream API to filter and print names starting with "J"
names.stream()
     .filter(name -> name.startsWith("J"))
     .forEach(System.out::println);
```

### 26. How does the `TreeMap` differ from `HashMap` in Java?

   - **Answer:**
     - `TreeMap` is a sorted map based on a natural order or a custom comparator.
     - `HashMap` is an unordered map with faster lookup times.
     - Use `TreeMap` when a sorted order of keys is required;

- use `HashMap` for faster key retrieval in an unordered manner.

```java
// Using TreeMap
TreeMap<Integer, String> treeMap = new TreeMap<>();
treeMap.put(3, "Three");
treeMap.put(1, "One");
treeMap.put(2, "Two");

// Entries in TreeMap will be sorted based on keys
System.out.println(treeMap); // {1=One, 2=Two, 3=Three}

// Using HashMap
HashMap<Integer, String> hashMap = new HashMap<>();
hashMap.put(3, "Three");
hashMap.put(1, "One");
hashMap.put(2, "Two");

// Entries in HashMap are not guaranteed to be in any specific order
System.out.println(hashMap); // {1=One, 2=Two, 3=Three}
```

### 27. What is the purpose of the `java.nio` package in Java?

   - **Answer:**
     - The `java.nio` package provides support for non-blocking I/O operations.
     - It introduces buffers, channels, and selectors for efficient handling of I/O operations.
     - Useful for building scalable and responsive network applications.

```java
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.io.IOException;
import java.util.List;

public class Example {
    public static void main(String[] args) {
        Path filePath = Paths.get("example.txt");

        try {
            List<String> lines = Files.readAllLines(filePath);
            lines.forEach(System.out::println);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

### 28. Explain the concept of the Observer design pattern in Java.

   - **Answer:**
     - The Observer pattern is a behavioral design pattern where an object, known as the subject, maintains a list of dependents, known as observers.
     - When the subject's state changes, all registered observers are notified and updated automatically.
     - Useful for implementing distributed event handling systems.

```java
import java.util.ArrayList;
import java.util.List;

// Subject
class NewsAgency {
    private List<NewsObserver> observers = new ArrayList<>();
    private String news;

    void addObserver(NewsObserver observer) {
        observers.add(observer);
    }

    void removeObserver(NewsObserver observer) {
        observers.remove(observer);
    }

    void setNews(String news) {
        this.news = news;
        notifyObservers();
    }

    private void notifyObservers() {
        observers.forEach(observer -> observer.update(news));
    }
}

// Observer
interface NewsObserver {
    void update(String news);
}

// Concrete Observer
class NewsChannel implements NewsObserver {
    private String news;

    @Override
    public void update(String news) {
        this.news = news;
        System.out.println("NewsChannel received news: " + news);
    }
}
```

### 29. What is the `ConcurrentHashMap` in Java, and how is it different from `HashMap`?

   - **Answer:**
     - `ConcurrentHashMap` is a thread-safe version of `HashMap` designed for concurrent operations.
     - It allows multiple threads to read and write concurrently without the need for external synchronization.
     - `HashMap` is not thread-safe, and concurrent modifications can result in unpredictable behavior.

```java
// Using ConcurrentHashMap
ConcurrentHashMap<Integer, String> concurrentHashMap = new ConcurrentHashMap<>();
concurrentHashMap.put(1, "One");
concurrentHashMap.put(2, "Two");

// Using HashMap (without external synchronization)
HashMap<Integer, String> hashMap = new HashMap<>();
hashMap.put(1, "One");
hashMap.put(2, "Two");
```

### 30. How does the `StringBuilder` class differ from the `String` class in Java?

   - **Answer:**
     - `StringBuilder` is mutable, allowing for efficient modification of character sequences.
     - `String` is immutable, and any modification creates a new string instance.
     - Use `StringBuilder` when frequent string modifications are needed for better performance.

```java
// Using StringBuilder for efficient string modification
StringBuilder stringBuilder = new StringBuilder("Hello");
stringBuilder.append(", World!");
System.out.println(stringBuilder.toString()); // Hello, World!

// Using String (creates a new instance for each modification)
String str = "Hello";
str += ", World!";
System.out.println(str); // Hello, World!
```

---------------------------------------------
# Collection Framework and data structures
---------------------------------------------

### 1. What is the difference between `List`, `Set`, and `Map` interfaces in the Collection Framework?

   - **Answer:**
     - `List`: Ordered collection allowing duplicate elements.
     - `Set`: Unordered collection with no duplicates.
     - `Map`: Key-value pair collection where each key is associated with a single value.

### 2. Explain the `ArrayList` class in Java and provide an example.

   - **Answer:**
     - `ArrayList` is a dynamic array that can grow or shrink as needed.
     - Example:

```java
List<String> arrayList = new ArrayList<>();
arrayList.add("Java");
arrayList.add("is");
arrayList.add("awesome");
System.out.println(arrayList); // [Java, is, awesome]
```

### 3. What is the purpose of the `HashSet` class in Java?

   - **Answer:**
     - `HashSet` is an implementation of the `Set` interface.
     - It uses a hash table for storage, providing constant-time performance for basic operations.
     - Does not allow duplicate elements.

```java
Set<String> hashSet = new HashSet<>();
hashSet.add("Apple");
hashSet.add("Banana");
hashSet.add("Apple"); // Duplicate entry, will be ignored
System.out.println(hashSet); // [Banana, Apple]
```

### 4. Explain the concept of a linked list and how it differs from an array.

   - **Answer:**
     - A linked list is a data structure where elements are connected by pointers.
     - Unlike arrays, linked lists do not require contiguous memory.
     - Insertion and deletion are efficient in linked lists, while random access is slower compared to arrays.

```java
// Example of a simple linked list node
class Node {
    int data;
    Node next;
}
```

### 5. What is the purpose of the `TreeSet` class in Java?

   - **Answer:**
     - `TreeSet` is an implementation of the `NavigableSet` interface.
     - It uses a red-black tree for storage, providing sorted elements in natural order.
     - Does not allow duplicate elements.

```java
Set<Integer> treeSet = new TreeSet<>();
treeSet.add(3);
treeSet.add(1);
treeSet.add(2);
System.out.println(treeSet); // [1, 2, 3]
```

### 6. Explain the `HashMap` class in Java and provide an example.

   - **Answer:**
     - `HashMap` is an implementation of the `Map` interface using a hash table.
     - It stores key-value pairs and allows for constant-time average complexity for basic operations.
     - Example:

```java
Map<String, Integer> hashMap = new HashMap<>();
hashMap.put("Java", 1);
hashMap.put("Python", 2);
System.out.println(hashMap.get("Java")); // 1
```

### 7. What is the purpose of the `Queue` interface in the Collection Framework?

   - **Answer:**
     - `Queue` represents a collection designed for holding elements prior to processing.
     - Common implementations include `LinkedList` and `PriorityQueue`.
     - Follows the FIFO (First-In-First-Out) principle.

### 8. Explain the concept of a stack and provide an example.

   - **Answer:**
     - A stack is a data structure that follows the Last-In-First-Out (LIFO) principle.
     - Elements are added or removed from the top of the stack.
     - Example:

```java
// Example of a simple stack
class Stack {
    private List<Integer> stackList = new ArrayList<>();

    void push(int item) {
        stackList.add(item);
    }

    int pop() {
        if (!stackList.isEmpty()) {
            int lastIndex = stackList.size() - 1;
            int poppedItem = stackList.get(lastIndex);
            stackList.remove(lastIndex);
            return poppedItem;
        }
        return -1; // Stack is empty
    }
}
```

### 9. How does the `LinkedList` class differ from the `ArrayList` class?

   - **Answer:**
     - `ArrayList` uses a dynamic array for storage, providing fast random access.
     - `LinkedList` uses a doubly-linked list, offering efficient insertion and deletion but slower random access.

```java
// Using ArrayList
List<String> arrayList = new ArrayList<>();
arrayList.add("Java");
arrayList.add("is");
arrayList.add("awesome");

// Using LinkedList
List<String> linkedList = new LinkedList<>();
linkedList.add("Java");
linkedList.add("is");
linkedList.add("awesome");
```

### 10. What is the purpose of the `Deque` interface in the Collection Framework?

   - **Answer:**
     - `Deque` represents a double-ended queue that allows elements to be added or removed from both ends.
     - Common implementations include `ArrayDeque` and `LinkedList`.
     - Supports both LIFO and FIFO operations.

### 11. Explain the `WeakHashMap` class in Java and its use case.

   - **Answer:**
     - `WeakHashMap` is an implementation of the `Map` interface.
     - It uses weak references for keys, allowing them to be garbage collected when no longer in use.
     - Useful for caching scenarios where entries can be automatically removed when not strongly referenced.

```java
WeakHashMap<Key, Value> weakHashMap = new WeakHashMap<>();
Key key = new Key();
Value value = new Value();
weakHashMap.put(key, value);
```

### 12. What is the purpose of the `Comparator` interface in Java?

   - **Answer:**
     - `Comparator` is used to define a custom order for objects.
     - It provides a way to compare objects, allowing sorting based on custom criteria.
     - Often used in sorting collections and arrays.

```java
// Example of sorting using Comparator
List<String> strings = Arrays.asList("Apple", "Banana", "Orange");
Collections.sort(strings, Comparator.reverseOrder());
System.out.println(strings); // [Orange, Banana, Apple]
```

### 13. Explain the `PriorityQueue` class in Java and provide an example.

   - **Answer:**
     - `PriorityQueue` is an implementation of the `Queue` interface.
     - Elements are dequeued based on their natural order or according to a provided comparator.
     - Example:

```java
Queue<Integer> priorityQueue = new PriorityQueue<>();
priorityQueue.offer(3);
priorityQueue.offer(1);
priorityQueue.offer(2);
System.out.println(priorityQueue.poll()); // 1
```

### 14. How does the `ConcurrentLinkedQueue` differ from `LinkedBlockingQueue`?

   - **Answer:**
     - `ConcurrentLinkedQueue` is a non-blocking, unbounded queue.
     - `LinkedBlockingQueue` is a blocking, optionally-bounded queue.
     - In `ConcurrentLinkedQueue`, operations like `poll()` do not block.

```java
// Using ConcurrentLinkedQueue

```java
ConcurrentLinkedQueue<String> concurrentQueue = new ConcurrentLinkedQueue<>();
concurrentQueue.offer("Java");
concurrentQueue.offer("is");
concurrentQueue.offer("concurrent");
System.out.println(concurrentQueue.poll()); // Java

// Using LinkedBlockingQueue
LinkedBlockingQueue<String> blockingQueue = new LinkedBlockingQueue<>(2); // Bounded to 2 elements
blockingQueue.put("Linked");
blockingQueue.put("Blocking");
System.out.println(blockingQueue.take()); // Linked
```

### 15. What is the purpose of the `Collections` class in Java?

   - **Answer:**
     - The `Collections` class provides utility methods for working with collections.
     - It includes methods for sorting, searching, shuffling, and creating synchronized collections.
     - Example:

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

// Using Collections class to shuffle the list
Collections.shuffle(names);
System.out.println(names);
```

### 16. Explain the `IdentityHashMap` class in Java and its use case.

   - **Answer:**
     - `IdentityHashMap` is an implementation of the `Map` interface.
     - It uses reference equality (`==`) for comparing keys, rather than the `equals` method.
     - Useful in scenarios where distinct objects with the same content need to be treated as separate keys.

```java
IdentityHashMap<String, Integer> identityMap = new IdentityHashMap<>();
String key1 = new String("Java");
String key2 = new String("Java");
identityMap.put(key1, 1);
identityMap.put(key2, 2);
System.out.println(identityMap.size()); // 2
```

### 17. How does the `EnumSet` class differ from other set implementations?

   - **Answer:**
     - `EnumSet` is a specialized implementation of the `Set` interface for use with enum types.
     - It is more memory-efficient than general-purpose set implementations.
     - Provides constant-time performance for basic operations.

```java
enum Days {MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY}

// Using EnumSet
EnumSet<Days> weekDays = EnumSet.of(Days.MONDAY, Days.TUESDAY, Days.WEDNESDAY);
System.out.println(weekDays); // [MONDAY, TUESDAY, WEDNESDAY]
```

### 18. Explain the `BitSet` class in Java and its use case.

   - **Answer:**
     - `BitSet` is a class that represents a resizable array of bits.
     - It is often used to perform operations on sets of bits.
     - Useful for scenarios where memory efficiency and bitwise operations are critical.

```java
BitSet bitSet1 = new BitSet(8);
BitSet bitSet2 = new BitSet(8);

bitSet1.set(0, 4); // Set bits 0 to 3
bitSet2.set(2, 6); // Set bits 2 to 5

// Performing bitwise AND operation
bitSet1.and(bitSet2);
System.out.println(bitSet1); // {2, 3}
```

### 19. What is the purpose of the `Arrays` class in Java?

   - **Answer:**
     - The `Arrays` class provides utility methods for working with arrays.
     - Includes methods for sorting, searching, comparing, and converting arrays.
     - Example:

```java
int[] numbers = {5, 2, 8, 1, 6};

// Using Arrays class to sort the array
Arrays.sort(numbers);
System.out.println(Arrays.toString(numbers)); // [1, 2, 5, 6, 8]
```

### 20. Explain the concept of a `WeakReference` in Java and its use case.

   - **Answer:**
     - A `WeakReference` is a class in Java that allows an object to be garbage-collected when no longer strongly referenced.
     - Useful for scenarios where temporary references to objects are needed without preventing their garbage collection.

```java
WeakReference<String> weakReference = new WeakReference<>(new String("Java"));

// Retrieving the referenced object
String value = weakReference.get();
System.out.println(value); // Java

// Making the object eligible for garbage collection
value = null;
System.gc();

// The object may be garbage-collected, and weakReference.get() may return null
System.out.println(weakReference.get());
```


