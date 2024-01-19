
### 1. Different between normal hashmap and concurrent hashmap?
- `HashMap` and `ConcurrentHashMap` are both implementations of the `Map` interface in Java, but they have significant differences, especially in terms of thread-safety and performance in concurrent environments:

#### 1. **Thread Safety:**
   - **HashMap:** `HashMap` is not thread-safe. If multiple threads try to modify the `HashMap` concurrently, it can lead to data corruption or infinite loops. You need to synchronize access to a `HashMap` explicitly using external synchronization (e.g., `Collections.synchronizedMap(map)`).
   - **ConcurrentHashMap:** `ConcurrentHashMap` is designed to be thread-safe without the need for external synchronization. It supports concurrent reads and writes. Different segments of the map can be updated concurrently, which can lead to better performance in highly concurrent scenarios.

#### 2. **Segmentation:**
   - **HashMap:** A regular `HashMap` is not divided into segments. When multiple threads try to update the map simultaneously, they can interfere with each other.
   - **ConcurrentHashMap:** `ConcurrentHashMap` is internally divided into segments. Each segment acts as an independent hash table, and different segments can be updated concurrently. This helps to minimize contention and provides better concurrency.

#### 3. **Locking Strategy:**
   - **HashMap:** It uses a single lock for the entire map during modifications. This means that if one thread is modifying the map, other threads are blocked, leading to potential performance bottlenecks in a highly concurrent environment.
   - **ConcurrentHashMap:** It uses a finer-grained locking strategy. Each segment has its own lock, allowing multiple threads to operate on different segments simultaneously. This reduces contention and improves concurrency.

#### 4. **Iterators:**
   - **HashMap:** If the `HashMap` is modified while iterating over it (except through the iterator's own `remove` method), it can lead to `ConcurrentModificationException`.
   - **ConcurrentHashMap:** Iterators of `ConcurrentHashMap` provide weakly consistent views. They reflect the state of the map at some point in time and do not throw `ConcurrentModificationException` even if the map is modified during iteration.

#### 5. **Performance:**
   - **HashMap:** In a single-threaded environment or when there is limited contention, a regular `HashMap` might perform well.
   - **ConcurrentHashMap:** In highly concurrent scenarios, where multiple threads are frequently reading and writing, `ConcurrentHashMap` is designed to provide better performance by allowing concurrent updates to different segments.

- In summary, `ConcurrentHashMap` is a more suitable choice in concurrent environments due to its built-in thread-safety and better support for concurrent operations. If you are dealing with a single-threaded environment or can ensure external synchronization, a regular `HashMap` may be sufficient.

 ### 2. Immutability concept.
   - immuntability in java refers to the property of an object whose state cannot be modified after it has been created.
   - 1. How to make a class immutable?
   - Make the class itself 'final' to prevent it from being extended.
   - Declare fields as 'final' to ensure they cannot be modified after initialization.
   - Use a private cunstructor to control object creation and initialization.
   - Don’t provide setter methods for variables.
    ### Mutable and immutable string:
   - In java strings are immutable by default. Once a String object is created, its content cannot be changed.
   - However, if you use StringBuilder or StringBuffer you are working with mutable String-like objects.

### 3. WHat is concurrent apps?
- refers to programs or systems that are designed to execute multiple tasks or processes simultaneously.
- Can be achieved usng threads or processes. Threads are lighter-weight units of execution within a process, while processes are independent programs with their own memory space.
  
### 4. Threading and multi-threading  **  [DONE]

### 5. Wrapper Classes.   [Done]
- A Wrapper class in Java is a class whose object wraps or contains primitive data types

### 6. How to make a class immutable? [DONE]

### 7. Different between jaa 8 and 7

### 8. stream, filter, map in arraylist[done]
    ```
    //STREAM 
        Stream<String> stream=list.stream();
        stream.filter(s->s.startsWith("f")).forEach(System.out::println);
        //fILTER
        List<String> filteredlist=list.stream().filter(s->s.length()>5).collect(Collectors.toList());
    ```

### 9. What is method reference?[done]

### 10. what is SYSTEM.OUT.PRINTLN in syso?
- system.out.println is a java statement used to print output to the console.
- it belongs to java.lang package and its a member of system class
- System: this is a class in Java's 'java.lang' package. It provides access to various system-related properties and methods.
- out: This is public static member of the 'System' class and represents the standard output stream. It is an instance of PrintStream class.
- println or print : it is a method of 'PrintStream' class.
- 

### 11. Variable length arguments in java?
- In Java, you can use variable-length argument lists, also known as varargs, to allow a method to accept a variable number of arguments of the same type. Varargs were introduced in Java 5. To use varargs, you specify an ellipsis (...) followed by the argument type in the method parameter declaration.
- 
```
public class VariableLengthArg {
    public static int sum(int... numbers){
        int result=0;
        
        for(int n:numbers){
            result+=n;
        }
        return result;
    }
    public static void main(String[] args) {
        System.out.println(sum(1,2,3));
    }
}
```

### 12. JRM ,JDK, JVM
    - What runs on a machine(JVM) is bytecode 

- Type java code -> Compile it --> converted into bytecode

- JVM : The space where actual code will run [Java Virtual macine] if there only JVM installed we can run our java code

- But if that code needs some extra packages like List, HashMap then we need one external thing for that.[JRE-> Java Runtime Environment]

- JRE -> 
   - JVM is a part of JRE.

- JDK : Top layer -> After installing JDK u'll get JRE and JVM

### 14. is there a diference between int i=9 and int i=09
- Yes, there is a difference between int i = 9 and int i = 09 in Java.

- In the first case, int i = 9, you are assigning the decimal value 9 to the variable i. This is a straightforward assignment of an integer literal in base 10.

- In the second case, int i = 09, the leading zero indicates that the value is specified in octal (base 8). In octal representation, valid digits are 0 through 7. Therefore, 09 is not a valid octal number because 9 is not a valid octal digit. If you try to compile code with int i = 09, it will result in a compilation error.

### 15. What is base class?
- In object-oriented programming, classes can be organized into hierarchies where one class inherits properties and behaviors from another. The class that is being inherited from is called the "superclass" or "base class," and the class that inherits from it is called the "subclass" or "derived class."

### 16. base class vs abstract class?
#### Base Class:
- In a general sense, a "base class" refers to any class that is extended or inherited by another class.
- The term is not explicitly used in Java, but it's common to refer to the superclass in a class hierarchy as the "base class."
- The base class provides a common set of attributes and behaviors that can be reused by its subclasses.

#### An abstract class :
- in Java is a class that cannot be instantiated on its own and may contain abstract methods.
- Abstract methods are declared without an implementation in the abstract class and must be implemented by concrete (non-abstract) subclasses.
- Abstract classes can have both abstract and non-abstract (concrete) methods.
- used to achieve abstarction like interface.
```
 abstract class Shape { //abstract class
    abstract void draw(); // Abstract method
    
    void resize() {
        System.out.println("Resizing the shape");
    }
}

// Concrete subclass
class Circle extends Shape {
    void draw() {
        System.out.println("Drawing a circle");
    }
}
```
  03:01:2024
      
### 16: Interface-
- In Java, an interface is a reference type that is similar to a class. It is a collection of abstract methods. When a class implements an interface, it inherits the abstract methods defined in that interface. Additionally, starting from Java 8, interfaces can also include default and static methods with implementations.
- used to achieve abstraction like abstract class.

Here are some key points about interfaces in Java:

1. **Declaration:**
   - You declare an interface using the `interface` keyword.
   - Example:

     ```java
     interface MyInterface {
         void abstractMethod(); // Abstract method (implicitly public and abstract)
         
         default void defaultMethod() {
             // Default method with implementation
             System.out.println("Default method");
         }

         static void staticMethod() {
             // Static method with implementation
             System.out.println("Static method");
         }
     }
     ```

2. **Abstract Methods:**
   - In an interface, methods are implicitly public and abstract. You don't need to use the `public` or `abstract` modifiers explicitly.
   - Example:

     ```java
     interface MyInterface {
         void abstractMethod(); // Abstract method
     }
     ```

3. **Default Methods:**
   - Starting from Java 8, interfaces can include default methods, which provide a default implementation.
   - Classes implementing the interface can choose to override the default method.
   - Example:

     ```java
     interface MyInterface {
         default void defaultMethod() {
             System.out.println("Default method");
         }
     }
     ```

4. **Static Methods:**
   - Starting from Java 8, interfaces can include static methods with an implementation.
   - Static methods are associated with the interface, not with instances of implementing classes.
   - Example:

     ```java
     interface MyInterface {
         static void staticMethod() {
             System.out.println("Static method");
         }
     }
     ```

5. **Implementing an Interface:**
   - To use an interface in a class, you use the `implements` keyword.
   - Example:

     ```java
     class MyClass implements MyInterface {
         @Override
         public void abstractMethod() {
             System.out.println("Implemented abstract method");
         }
     }
     ```

6. **Multiple Inheritance:**
   - Unlike classes, a class can implement multiple interfaces in Java, enabling a form of multiple inheritance through interfaces.
   - Example:

     ```java
     interface Interface1 {
         // methods
     }

     interface Interface2 {
         // methods
     }

     class MyClass implements Interface1, Interface2 {
         // Implementation of methods from Interface1 and Interface2
     }
     ```


### 17. Abstract class vs Interface.
In Java, both abstract classes and interfaces are used to achieve abstraction, but they have some key differences in terms of functionality and usage. Here are the main distinctions between abstract classes and interfaces:

1. **Abstract Class:**
   - An abstract class is a class that cannot be instantiated on its own and may contain both abstract and concrete methods.
   - Abstract methods declared in an abstract class are implicitly abstract and must be implemented by concrete subclasses.
   - An abstract class can have instance variables (fields), constructors (including a default constructor), and non-abstract methods with or without implementations.
   - It supports the concept of constructors, which can be used to initialize instance variables and perform other tasks during object creation.
   - A class can extend only one abstract class.

   Example:

   ```java
   abstract class AbstractClass {
       int commonField;

       AbstractClass(int commonField) {
           this.commonField = commonField;
       }

       abstract void abstractMethod();

       void concreteMethod() {
           System.out.println("Concrete method");
       }
   }
   ```

2. **Interface:**
   - An interface is a collection of abstract methods, default methods, and static methods. Starting from Java 8, interfaces can have methods with implementations.
   - All methods declared in an interface are implicitly public and abstract (except for static and default methods).
   - Interfaces can't have instance variables (fields), constructors, or non-abstract methods with implementations (except for static and default methods).
   - It supports multiple inheritance, as a class can implement multiple interfaces.
   - Interfaces are often used to define contracts for classes that implement them.

   Example:

   ```java
   interface MyInterface {
       void abstractMethod(); // Implicitly public and abstract

       default void defaultMethod() {
           System.out.println("Default method");
       }

       static void staticMethod() {
           System.out.println("Static method");
       }
   }
   ```

**When to Use Abstract Class vs Interface:**

- Use an abstract class when you want to provide a common base class for other classes to inherit from. Abstract classes are useful for sharing code and providing a common structure.

- Use an interface when you want to define a contract that multiple classes can implement. Interfaces are more suitable for scenarios where a class may need to inherit from multiple sources.

- If you need to provide a default implementation for some methods, use an abstract class. If you want to define a contract without providing any default implementation, use an interface.

In some cases, a combination of abstract classes and interfaces may be used to achieve the desired level of abstraction and code reuse in a Java application.


### 18. functional interface. 

In Java, a functional interface is an interface that contains only one abstract method. Functional interfaces are a key concept in the functional programming paradigm introduced in Java 8 with the addition of lambda expressions and the `java.util.function` package.

Here are the characteristics of a functional interface:

1. **Single Abstract Method (SAM):**
   - A functional interface should declare exactly one abstract method. This method is often referred to as the "functional method" or "single abstract method" (SAM).
   - The presence of a single abstract method allows instances of functional interfaces to be created using lambda expressions or method references.

2. **Optional Default and Static Methods:**
   - A functional interface can have additional default methods or static methods with implementations, but it must have only one abstract method.
   - Default methods provide a default implementation for a method, and static methods are associated with the interface itself.

3. **Annotation:**
   - While not required, it's a good practice to use the `@FunctionalInterface` annotation on a functional interface to indicate its intended use as a functional interface. This annotation is optional but helps prevent accidental addition of more than one abstract method.

Here's an example of a functional interface:

```java
@FunctionalInterface
interface MyFunctionalInterface {
    void myMethod(); // Single abstract method

    // Optional: Default method
    default void defaultMethod() {
        System.out.println("Default method");
    }

    // Optional: Static method
    static void staticMethod() {
        System.out.println("Static method");
    }
}
```

With functional interfaces, you can use lambda expressions to concisely represent instances of these interfaces. For example:

```java
public class Main {
    public static void main(String[] args) {
        // Using a lambda expression to create an instance of MyFunctionalInterface
        MyFunctionalInterface functionalInstance = () -> System.out.println("Lambda expression implementation");
        
        // Calling the method defined in the functional interface
        functionalInstance.myMethod();

        // Calling default and static methods
        functionalInstance.defaultMethod();
        MyFunctionalInterface.staticMethod();
    }
}
```

Functional interfaces are commonly used in conjunction with lambda expressions to write more concise and expressive code, particularly when working with features introduced in Java 8 and later, such as the Stream API and the functional programming enhancements.


19. Hashmap hashcode overriden scenario [PENDING]

### 20. Rehashing
- 
Rehashing is a process used in hash-based data structures, such as HashMap, to resize the underlying hash table and reorganize the elements when the load factor exceeds a certain threshold. The load factor is the ratio of the number of elements to the size of the hash table. Rehashing helps in maintaining a reasonable balance between the number of elements and the size of the hash table, ensuring efficient performance.

- In Java, HashMap is an example of a hash-based data structure that uses rehashing. When the number of elements in a HashMap exceeds a certain threshold (determined by the load factor), the HashMap automatically increases the size of the underlying array and rehashes the elements into the new array.

### 21. Criteria for hashmap.
When choosing to use a `HashMap` in Java, you need to consider various factors and criteria to ensure that it is the appropriate data structure for your specific use case. Here are some criteria to consider when deciding whether to use a `HashMap`:

1. **Efficient Lookup:**
   - Use a `HashMap` when you need fast and efficient lookups. The average time complexity for search operations (get and containsKey) in a `HashMap` is O(1).

2. **Key-Value Pairs:**
   - Use a `HashMap` when you have a collection of key-value pairs. It allows you to store and retrieve values based on unique keys.

3. **Uniqueness of Keys:**
   - Each key in a `HashMap` must be unique. If you need to associate unique keys with values, a `HashMap` is suitable.

4. **Null Values:**
   - `HashMap` allows one `null` key and multiple `null` values. If your application needs to handle null keys or values, a `HashMap` is a good choice.

5. **Unordered Elements:**
   - The order of elements in a `HashMap` is not guaranteed. If you don't need a specific order for your elements, a `HashMap` is appropriate.

6. **No Duplicate Values:**
   - While keys must be unique, values can be duplicated. If you need to store duplicate values associated with different keys, a `HashMap` is suitable.

7. **Dynamic Size:**
   - `HashMap` automatically adjusts its size as elements are added or removed. If you have a dynamic set of elements and the size may change frequently, a `HashMap` is a good choice.

8. **Complexity of Operations:**
   - `HashMap` provides O(1) time complexity for basic operations like get, put, and remove in the average case. This makes it efficient for scenarios where these operations are frequently performed.

9. **Memory Efficiency:**
   - `HashMap` uses memory to store key-value pairs. If memory efficiency is a concern, consider the memory requirements of your application and the size of the data set.

10. **Concurrency Considerations:**
    - If your application requires thread safety, consider using `ConcurrentHashMap` instead of a regular `HashMap`. `ConcurrentHashMap` supports concurrent access by multiple threads without the need for external synchronization.

11. **Custom Object Equality:**
    - If you have custom objects as keys, ensure that you override the `hashCode()` and `equals()` methods appropriately to maintain the contract required by `HashMap`.

### 22. Can string and stringbuilder and primitive integer, Wrapper Integer be a hashmap key?

Yes, both `String`, `StringBuilder`, and instances of `Integer` (primitive wrapper class for `int`) can be used as keys in a `HashMap` in Java. However, there are some considerations and differences between them:

1. **String as a Key:**
   - `String` is commonly used as a key in a `HashMap`. Strings are immutable, and their hash codes are calculated based on their content.
   - Example:

     ```java
     HashMap<String, Integer> stringHashMap = new HashMap<>();
     stringHashMap.put("one", 1);
     stringHashMap.put("two", 2);
     ```

2. **StringBuilder as a Key:**
   - `StringBuilder` is mutable, and its hash code is calculated based on its current content. However, using a mutable object as a key in a `HashMap` can lead to unexpected behavior if the key is modified after being used in the `HashMap`.
   - It's generally not recommended to use mutable objects as keys in hash-based data structures because modifications can change the hash code, leading to difficulties in retrieving the associated value.

     ```java
     HashMap<StringBuilder, Integer> stringBuilderHashMap = new HashMap<>();
     stringBuilderHashMap.put(new StringBuilder("one"), 1);
     stringBuilderHashMap.put(new StringBuilder("two"), 2);
     ```

3. **Integer (Primitive) as a Key:**
   - Primitive data types, including `int`, cannot be used directly as keys in a `HashMap`. However, their corresponding wrapper classes, such as `Integer`, can be used.
   - Example:

     ```java
     HashMap<Integer, String> integerHashMap = new HashMap<>();
     integerHashMap.put(1, "one");
     integerHashMap.put(2, "two");
     ```

4. **Wrapper Integer as a Key:**
   - Instances of `Integer` (and other wrapper classes for primitive types) can be used as keys in a `HashMap`.
   - Example:

     ```java
     HashMap<Integer, String> integerHashMap = new HashMap<>();
     integerHashMap.put(new Integer(1), "one"); // Before Java 9
     integerHashMap.put(2, "two"); // Autoboxing (Java 9 and later)
     ```

   - Autoboxing allows you to use primitive literals directly as keys in a `HashMap` without explicitly creating instances of wrapper classes.


### 23. Can store primitive Integer as a value of hashmap?
    - In Java, the HashMap class only allows objects to be used as values. Primitive types, including int, cannot be directly used as values in a HashMap. However, you can use the corresponding wrapper classes for primitive types, such as Integer, to store integers as values.
----
## Types of Data Types:

### 1. Primitive:
In Java, there are eight primitive data types. They are:

1. **byte:**
   - 8-bit signed integer.
   - Range: -128 to 127.

   ```java
   byte myByte = 127;
   ```

2. **short:**
   - 16-bit signed integer.
   - Range: -32,768 to 32,767.

   ```java
   short myShort = 32767;
   ```

3. **int:**
   - 32-bit signed integer.
   - Range: -2^31 to 2^31 - 1.

   ```java
   int myInt = 2147483647;
   ```

4. **long:**
   - 64-bit signed integer.
   - Range: -2^63 to 2^63 - 1.

   ```java
   long myLong = 9223372036854775807L;
   ```

5. **float:**
   - 32-bit IEEE 754 floating-point.
   - Example:

   ```java
   float myFloat = 3.14f;
   ```

6. **double:**
   - 64-bit IEEE 754 floating-point.
   - Example:

   ```java
   double myDouble = 3.14;
   ```

7. **char:**
   - 16-bit Unicode character.
   - Example:

   ```java
   char myChar = 'A';
   ```

8. **boolean:**
   - Represents true or false.

   ```java
   boolean myBoolean = true;
   ```

These primitive data types are used to represent simple values and are not objects. They have corresponding wrapper classes (e.g., `Byte`, `Short`, `Integer`, `Long`, `Float`, `Double`, `Character`, `Boolean`) that allow them to be used in contexts that require objects, such as collections and generics.

### 2. Non-Primitive:
In Java, non-primitive data types are reference types or objects. They are instances of classes or interfaces, and they can be more complex than primitive data types. Here are some common non-primitive data types in Java:

1. **Object Types:**
   - The most general type, representing any object.
   - Example:

     ```java
     Object myObject = new Object();
     ```

2. **String:**
   - A sequence of characters.
   - Example:

     ```java
     String myString = "Hello, Java!";
     ```

3. **Arrays:**
   - Collections of elements of the same type.
   - Example:

     ```java
     int[] myIntArray = {1, 2, 3, 4, 5};
     ```

4. **Classes:**
   - User-defined types that encapsulate data and behavior.
   - Example:

     ```java
     class MyClass {
         // class definition
     }

     MyClass myInstance = new MyClass();
     ```

5. **Interfaces:**
   - Defines a contract for implementing classes.
   - Example:

     ```java
     interface MyInterface {
         // interface definition
     }

     class MyImplementation implements MyInterface {
         // implementation of the interface
     }
     ```

6. **Enum Types:**
   - A special type that defines a set of constants.
   - Example:

     ```java
     enum Day {
         MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY
     }

     Day today = Day.MONDAY;
     ```

7. **Collections:**
   - Various classes and interfaces in the `java.util` package that represent dynamic groups of elements.
   - Examples:

     ```java
     List<String> myList = new ArrayList<>();
     Set<Integer> mySet = new HashSet<>();
     ```

8. **Maps:**
   - Classes in the `java.util` package that represent key-value pairs.
   - Example:

     ```java
     Map<String, Integer> myMap = new HashMap<>();
     ```

9. **Custom Classes:**
   - User-defined classes created to model specific entities or concepts in an application.
   - Example:

     ```java
     class Person {
         String name;
         int age;
     }

     Person person = new Person();
     person.name = "John";
     person.age = 25;
     ```

04/01/2024

### 25. Failfast and failsafe collection  [PENDING]
"Failfast" and "failsafe" are terms commonly associated with collections in programming, particularly in the context of concurrent programming and data structures. Let's explore each term:

1. **Failfast:**
   - **Definition:** A failfast strategy involves detecting and addressing errors as soon as they occur, rather than allowing the program to continue with potentially corrupted or inconsistent data.
   - **Collections:** In the context of collections (like lists, sets, or maps), a failfast iterator will throw a ConcurrentModificationException if the collection is modified structurally while it is being iterated. This is done to prevent potential issues that may arise from concurrent modifications.

   ```java
   List<String> list = new ArrayList<>();
   Iterator<String> iterator = list.iterator();

   list.add("Item 1");
   iterator.next(); // This may throw ConcurrentModificationException
   ```

   - **Use Case:** Failfast mechanisms are beneficial in situations where detecting errors early is crucial to prevent further issues or data corruption.

2. **Failsafe:**
   - **Definition:** A failsafe strategy aims to provide a reliable and consistent behavior even in the presence of errors or failures. Instead of terminating the program or throwing exceptions, failsafe mechanisms attempt to recover or continue execution in a safe manner.
   - **Collections:** Failsafe collections are designed to be thread-safe and handle concurrent modifications without causing exceptions or corruption. They typically use techniques such as locking or atomic operations to ensure consistency.

   ```java
   List<String> list = new CopyOnWriteArrayList<>();
   Iterator<String> iterator = list.iterator();

   list.add("Item 1");
   // No exception will be thrown, and iterator will reflect the original state of the list
   ```

   - **Use Case:** Failsafe mechanisms are suitable for scenarios where graceful degradation or continued operation is more important than immediate failure due to errors. They are often used in concurrent programming to ensure data integrity.

In summary, failfast collections aim to detect errors early and raise exceptions to prevent further issues, while failsafe collections focus on providing consistent behavior even in the presence of errors, allowing programs to continue running with a potentially degraded but safe state. 


26. biddecimal comaprison

## 27. Heap and Stack memory.  lasting

### Heap Memory:
  - The heap is used for dynamic memory allocation. Objects, such as instances of classes, are created on the heap.
  - It is a region of memory managed by JVM.
  - The heap memory is subject to automatic garbage collection.
  - The JVM periodically identifies and reclaims memory occupied by objects that are no longer rechable, freeing up resource.

### Stack memory:
  - The stack is used for method execution.
  - Each thread in java has its own stack, and it is where method variables and method call information  are stored.
  - LIFO structure --> Last In First Out
    

## 29. Marker interface in java   
- has no methods.
- It serves as a marker to convey information about the class implementiong it.
- Example : Serializable interface, which is used to indicate that a class can be serialized.

## 30. POJO
- Plain Old Java Object
- Java class that doesn't follow any special programming model or framework, and it follows basic principles of OOP.
- A POJO typically represents a simple data structure and doesn't have any dependencies.
```
public class Person{
   private String name;
   private int age;
   //constructirs
   public Person(){
   }
   public Person(String name,int age){
     this.name=name;
     this.age=age;
   }
 //setters and getters
}
```

## 31. Optional classes  

- The `Optional` class in Java is part of the java.util package and was introduced in Java 8.
- It is designed to help eliminate null pointer exceptions and encourage more explicit handling of cases where a value might be absent.

Here's a brief overview of the `Optional` class:

1. **Creation of Optional:**
   - You can create an `Optional` instance using the `of`, `ofNullable`, or `empty` methods.

   ```java
   Optional<String> presentOptional = Optional.of("Value is present");
   Optional<String> nullableOptional = Optional.ofNullable(null); // Value may or may not be present
   Optional<String> emptyOptional = Optional.empty(); // Represents an empty value
   ```

2. **Checking for Presence:**
   - You can check if a value is present in the `Optional` using methods like `isPresent()`.

   ```java
   if (presentOptional.isPresent()) {
       System.out.println(presentOptional.get());
   }
   ```

3. **Getting the Value:**
   - You can retrieve the value if it is present using the `get` method. However, it's recommended to use other methods like `orElse`, `orElseGet`, or `orElseThrow` to handle absent values more effectively.

   ```java
   String value = presentOptional.orElse("Default Value");
   ```

4. **Chaining Operations:**
   - You can chain operations on `Optional` using methods like `map`, `flatMap`, and `filter`.

   ```java
   Optional<String> result = presentOptional.map(s -> s.toUpperCase());
   ```

5. **Avoiding Null Checks:**
   - Instead of checking for null, you can use `Optional` to handle the absence of a value in a more expressive way.

   ```java
   String result = nullableOptional.orElse("Value is absent");
   ```

Using `Optional` can lead to more readable and less error-prone code when dealing with situations where a value might be absent.


## 32. CIrcuit breaker design pattern
- used to handle faults and failures in a distributed system.

## 33. fault isolation
- Managing and containing errors or faults to prevent them from cancading and affecting the overall stability of a system.
- 1. Exception Handling : using Try and Catch
- 2. Circuit breaker Pattern :Implement the circuit breaker to detect and handle failures in a distributed system.
- Isolation with threads:
- Microservices : In a microservices architecture, faults in one service shuld not bring down the entore system.
- Each microservice operates independently, and failures are isolaed to the specific service.

34. Executer framework in threading

### 35. How do you decide no of threads required for designing the appliacation? count??
using various factors like
- 1. Nature of your task
  2. The characteristics of your system.
  3. available resources.
     
### 36. Deadlogs in threading? deadlock..?
   - occurs when two or more threads are blocked forever, each waiting for other to release a lock.
   - This situation results in a standstill, where no thread ca proceed, leading to a ha;t in the execution of the program.

### 38. what is synchronized?
- used to control acccess to critical section of code in multithreaded environment.
- provides way to prevent mulltiple threads from concurrently executing certain sections of code, ensuring only one can access it at a time.
- Purpose : Thread safety

### 39. when to use linkedlist over list?

40. What is struct framework?
41. Reading file in java?
42. Stringbuilder vs StringBuffer?
43. Synchronization
44. Custom Exception handling
45. Stream API.
    



SPRING :

### 1. What is Dependency injection?
- involves injecting dependencies into components,
- promoting loose coupling.
- TYPES: Construcotr, Setter, Field Injection.
- @Autowired, @Qualifier, @Resource facilitate DI.
- XML conf is alternative
- Benefits : 1. Loose coupling  2. Testability,  3. Flexibility abd adherence to best practices.
- Spring IOC container manages object creation and dependency injection.

### 2. Solid principles?
- set of design principles that aim to create more maintainable, scalable, and flexible software.
- widely used in OOP.
  
  #### 1. Single Responsibility Principle(SRP):
  - a class should have only one reason to change.
  - one responsibility.
  - promotes maintainability and readability.
  #### 2. Open and Closed Principle;
  - should be open for extension but not for modification.
  - encourages use of interfaces, abstract classes, and polimorphism.
  ### 3. LISKOV Substituiton Principle:
  ### 4. Interface Segregation Principle:
  ### 5. Dependency Inversion Principle:

### 3. How Singleton design pattern coulb be breck?
- Singleton design pattern intended to ensure that a class has only one object and prvides global point of access tp that object.
  #### How to break:
  #### Reflection:
  - using Java reflection , it's possible to maccess the private constructor of a singleton class and creating enw instances.
  #### Serialization and Deserialization:
  - If singleton class is serializable deserializing an object can create a new instance.
  #### Multithreading:
   - im MT env, if the singleton instance is not properly synchronized during creation, it may lead to creation of multiple instances.

### 4. Step we have to for saving data in DB using PostAPI[postmapping]?
- 1. configure DB connection in 'application.properties' file.
  2. Create entity class. @Entity @Id @GeneratedValue(strategy=GenerationType.AUTO)
  3. create Repository interface extends JpaRepository<EntityName, Primary_Key_Datatype> -->
  4. Create service class --> @Service --> create method to save the data --> Inject Repository here only
  5. Create controller--> @postmapping -->inject service bean -->save it
  6. Test with postman

### 5. Difference between POST and PUT?
- POST : Creating a new resource
- Submitting form data.
- Uploading file

- PUT: update existing data.
- Creating a new resource if it doesnot exit at the specified URL.

6. PUT and PATCH difference?
- Patch
- Updating specific fields.
- like updating only one field
  
### 7. How do you find the second or nth highest salary of employee?
   - SELECT DISTINCT salary
     FROM employees
     ORDER BY salary DESC
     LIMIT 1 OFFSET (n-1);

### 9. how to manage DB threads in spring?

10. How to set limit for REST API?

11. What is pool?

### 12. Resttemplate in springboot?
- RestTemplate is a class in sring framework that simplifies the process of making HTTP requests to remote services.

### 13. How to implement cashing in sprboot?
- using @cashble @CachePut, @CacheEvict.
- Caching --> technique used in computing to store and manage copies of freque=ntly accessed or computed data in order to improve the performance of apps.

14. JPA or ORM or Hybernate?   which one u are using
15. Web service vs microservice
16.  



## Suggested REDIS, KAFKA

videos:

Lj9RG8cehTk
eD9Q_c1-z24
