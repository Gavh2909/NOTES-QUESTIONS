
# **Java Interview Questions**

1. **What is the difference between `==` and `.equals()` in Java?**
   - `==` compares object references, while `.equals()` compares the content of objects.

   ```java
   String str1 = new String("Hello");
   String str2 = new String("Hello");
   boolean result = (str1 == str2); // false
   boolean isEqual = str1.equals(str2); // true
   ```

2. **Explain the concept of polymorphism in Java.**
   - Polymorphism allows objects of different types to be treated as objects of a common type.

   ```java
   interface Shape {
       void draw();
   }

   class Circle implements Shape {
       void draw() { /* Circle specific draw logic */ }
   }

   Shape shape = new Circle(); // Polymorphism
   shape.draw(); // Calls Circle's draw method
   ```

3. **What is the difference between `ArrayList` and `LinkedList`?**
   - `ArrayList` uses a dynamic array, while `LinkedList` uses a doubly-linked list.

   ```java
   // ArrayList
   ArrayList<String> arrayList = new ArrayList<>();
   arrayList.add("Item 1");
   String item = arrayList.get(0);

   // LinkedList
   LinkedList<String> linkedList = new LinkedList<>();
   linkedList.add("Item 1");
   String item = linkedList.get(0);
   ```

4. **Explain the concept of encapsulation in Java.**
   - Encapsulation is the bundling of data and methods that operate on the data into a single unit (class).

   ```java
   public class Car {
       private String model;

       public String getModel() {
           return model;
       }

       public void setModel(String model) {
           this.model = model;
       }
   }
   ```

5. **How does Java handle runtime polymorphism?**
   - Java uses method overriding and dynamic method dispatch to achieve runtime polymorphism.

   ```java
   class Animal {
       void makeSound() {
           System.out.println("Animal makes a sound");
       }
   }

   class Dog extends Animal {
       void makeSound() {
           System.out.println("Dog barks");
       }
   }

   Animal myPet = new Dog();
   myPet.makeSound(); // Calls Dog's makeSound at runtime
   ```

6. **What is the `NullPointerException` in Java?**
   - `NullPointerException` occurs when you try to access or call methods on an object that is `null`.

   ```java
   String str = null;
   int length = str.length(); // Throws NullPointerException
   ```

7. **Explain the `final` keyword in Java.**
   - The `final` keyword is used to make a variable, method, or class unchangeable.

   ```java
   final int MAX_VALUE = 100;
   final void myMethod() { /* Method implementation */ }
   ```

8. **What is the purpose of the `super` keyword in Java?**
   - The `super` keyword is used to refer to the immediate parent class's members (fields or methods).

   ```java
   class Animal {
       void eat() {
           System.out.println("Animal is eating");
       }
   }

   class Dog extends Animal {
       void eat() {
           super.eat(); // Calls Animal's eat method
           System.out.println("Dog is eating");
       }
   }
   ```

9. **Explain the difference between `throw` and `throws` in Java.**
   - `throw` is used to explicitly throw an exception, while `throws` is used in method declarations to indicate that the method may throw an exception.

   ```java
   void myMethod() throws MyException {
       // Method logic
   }

   void anotherMethod() {
       throw new MyException("This is an exception");
   }
   ```

10. **What is the purpose of the `static` keyword in Java?**
    - The `static` keyword is used to create class-level members (variables or methods) that can be accessed without creating an instance of the class.

    ```java
    class MathUtil {
        static int add(int a, int b) {
            return a + b;
        }
    }

    int result = MathUtil.add(5, 3); // Accessing static method without instance
    ```

**11. Explain the concept of method overloading in Java.**
   - Method overloading allows a class to have multiple methods with the same name but different parameter lists.

   ```java
   class Calculator {
       int add(int a, int b) {
           return a + b;
       }

       double add(double a, double b) {
           return a + b;
       }
   }

   Calculator myCalc = new Calculator();
   int sumInt = myCalc.add(5, 3);
   double sumDouble = myCalc.add(5.5, 3.2);
   ```

**12. What is the purpose of the `this` keyword in Java?**
   - The `this` keyword is used to refer to the current instance of the class.

   ```java
   class Person {
       private String name;

       void setName(String name) {
           this.name = name; // Refers to the instance variable 'name'
       }
   }
   ```

**13. Explain the use of the `transient` keyword in Java.**
   - The `transient` keyword is used to indicate that a variable should not be serialized during object serialization.

   ```java
   class MyClass implements java.io.Serializable {
       transient int myTransientVariable;
       int myNonTransientVariable;
   }
   ```

**14. What is the purpose of the `volatile` keyword in Java?**
   - The `volatile` keyword is used to indicate that a variable's value may be changed by multiple threads simultaneously.

   ```java
   class SharedResource {
       volatile boolean flag = false;
   }
   ```

**15. How does the `try`, `catch`, `finally` block work in Java exception handling?**
   - The `try` block contains the code that may throw an exception, `catch` block handles the exception, and `finally` block contains code that will be executed regardless of whether an exception is thrown or not.

   ```java
   try {
       // Code that may throw an exception
   } catch (ExceptionType ex) {
       // Handle the exception
   } finally {
       // Code that always executes
   }
   ```

**16. Explain the concept of an anonymous class in Java.**
   - An anonymous class is a class without a name that is defined on the fly for creating an object.

   ```java
   interface MyInterface {
       void myMethod();
   }

   MyInterface myObj = new MyInterface() {
       public void myMethod() {
           System.out.println("Anonymous class implementation");
       }
   };
   ```

**17. What is the purpose of the `enum` keyword in Java?**
   - The `enum` keyword is used to define a fixed set of constants.

   ```java
   enum Day {
       SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY
   }

   Day currentDay = Day.MONDAY;
   ```

**18. Explain the concept of a thread-safe class in Java.**
   - A thread-safe class is designed to safely support multiple threads accessing its methods without causing data inconsistency or other issues.

   ```java
   class ThreadSafeCounter {
       private int count = 0;

       synchronized void increment() {
           count++;
       }
   }
   ```

**19. What is the purpose of the `clone()` method in Java?**
   - The `clone()` method is used to create a copy of an object.

   ```java
   class MyClass implements Cloneable {
       int value;

       public Object clone() throws CloneNotSupportedException {
           return super.clone();
       }
   }

   MyClass originalObj = new MyClass();
   MyClass clonedObj = (MyClass) originalObj.clone();
   ```

**20. Explain the concept of the Java Virtual Machine (JVM).**
   - JVM is an abstract machine that provides the runtime environment for executing Java bytecode. It interprets the bytecode or compiles it to native machine code for the host machine.
