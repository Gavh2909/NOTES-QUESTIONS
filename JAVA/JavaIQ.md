
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


18. functional interface. **

19. Hashmap hashcode overriden scenario

20. Rehashing

21. Criteria for hashmap.

22. Can string and stringbuilder and primitive integer, qrapper Integer be a hashmap key?

23. Can store primitive Integer as a value of hashmap?

24. Failfast and failsafe collection



25. biddecimal comaprison

26. Heap and Stack memory.  lasting

27. Marker interface in java

28. POJO 

29. Optional classes  

30. CIrcuit breaker design pattern

31. fault isolation

32. Executer framework in threading

33. How do you decide no of threads required for designing the appliacation? count??

34. Deadlogs in threading? deadlock..?

35. what is synchronized?

36. when to use linkedlist over list?





SPRING :

1. What is Dependency injection?

2. Solid principles?

3. How Singleton design pattern coulb be breck?

4. Step we have to for saving data in DB using PostAPI[postmapping]?

5. Difference between POST and PUT?

6. PUT and PATCH difference?

7. How do you find the second highest salary of employee?

8. how to manage DB threads in spring?

9. How to set limit for REST API?

10. What is pool?

11. Resttemplate in springboot?

12. How to implement cashing in sprboot?




## Suggested REDIS, KAFKA

videos:

Lj9RG8cehTk
eD9Q_c1-z24
