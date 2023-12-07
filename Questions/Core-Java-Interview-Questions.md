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
     - If not explicitly called, the compiler inserts a default `

