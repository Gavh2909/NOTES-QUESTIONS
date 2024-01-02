
### Different between normal hashmap and concurrent hashmap?

 ### Immutability concept.
   - immuntability in java refers to the property of an object whose state cannot be modified after it has been created.
   - 1. How to make a class immutable?
   - Make the class itself 'final' to prevent it from being extended.
   - Declare fields as 'final' to ensure they cannot be modified after initialization.
   - Use a private cunstructor to control object creation and initialization.
   - Don’t provide setter methods for variables.
    ### Mutable and immutable string:
   - In java strings are immutable by default. Once a String object is created, its content cannot be changed.
   - However, if you use StringBuilder or StringBuffer you are working with mutable String-like objects.

### WHat is concurrent apps?
- refers to programs or systems that are designed to execute multiple tasks or processes simultaneously.
- Can be achieved usng threads or processes. Threads are lighter-weight units of execution within a process, while processes are independent programs with their own memory space.
  
### Threading and multi-threading  **  [DONE]

### Wrapper Classes.   [Done]
- A Wrapper class in Java is a class whose object wraps or contains primitive data types

### How to make a class immutable? [DONE]

### Different between jaa 8 and 7

### streat, filter, mapOInt in arraylist[done]
    ```
    //STREAM 
        Stream<String> stream=list.stream();
        stream.filter(s->s.startsWith("f")).forEach(System.out::println);
        //fILTER
        List<String> filteredlist=list.stream().filter(s->s.length()>5).collect(Collectors.toList());
    ```

### What is method reference?[done]

### what is SYSTEM.OUT.PRINTLN in syso?
- system.out.println is a java statement used to print output to the console.
- it belongs to java.lang package and its a member of system class
- System: this is a class in Java's 'java.lang' package. It provides access to various system-related properties and methods.
- out: This is public static member of the 'System' class and represents the standard output stream. It is an instance of PrintStream class.
- println or print : it is a method of 'PrintStream' class.
