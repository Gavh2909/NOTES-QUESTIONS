
### 1. Different between normal hashmap and concurrent hashmap?

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
      

17. Abstract class vs Interface.

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
