# Modifiers

### Which is the default access modifier in Java?
Java provides a default specifier which is used when no access modifier is present. Any class, field, method or constructor 
that has no declared access modifier is accessible only by classes in the same package. The default modifier is not used for 
fields and methods within an interface.

### What is private access modifier ?
Methods, variables, and constructors that are declared private can only be accessed within the declared class itself.
Private access modifier is the most restrictive access level. Class and interfaces cannot be private.
Variables that are declared private can be accessed outside the class, if public getter methods are present in the class.
Using the private modifier is the main way that an object encapsulates itself and hides data from the outside world.

### What is default or package access modifier?
The members of a class defined without using any explicit access modifier are defined with package accessibility (also
called default accessibility). The members with package access are only accessible to classes and interfaces defined in the
same package.

### What is protected access modifier?
Protected Access Modifier - protected: Variables, methods and constructors which are declared protected in a superclass can 
be accessed only by the subclasses in other package or any class within the package of the protected members' class.

### Access modifiers 
```
           | Class | Package | Subclass | Subclass | World
            |       |         |(same pkg)|(diff pkg)| 
————————————+———————+—————————+——————————+——————————+————————
public      |   +   |    +    |    +     |     +    |   +     
————————————+———————+—————————+——————————+——————————+————————
protected   |   +   |    +    |    +     |     +    |         
————————————+———————+—————————+——————————+——————————+————————
no modifier |   +   |    +    |    +     |          |    
————————————+———————+—————————+——————————+——————————+————————
private     |   +   |         |          |          |    

+ : accessible
blank : not accessible
```

### What is the use of a final modifier on a class?
The final modifier is used to specify that a class cannot be extended or that a method or property cannot be overridden. This 
prevents other classes from changing the behavior of the class by overriding important functions.

### What is the use of a final modifier on a method?
The final modifier is used to specify that a class cannot be extended or that a method or property cannot be overridden. 
This prevents other classes from changing the behavior of the class by overriding important functions.
Methods with the final modifier can be hidden or overloaded by methods in derived classes.

### What is a final variable?
In Java we use final keyword with variables to specify its values are not to be changed. But I see that you can change the value
in the constructor / methods of the class.

### What is a final argument?
As a formal method parameter is a local variable, you can access them from inner anonymous classes only if they are declared 
as final.

This saves you from declaring another local final variable in the method body:
```
 void m(final int param) {
        new Thread(new Runnable() {
            public void run() {
                System.err.println(param);
            }
        }).start();
    }
```

### What is volatile variable ?
 The Java volatile keyword is used to mark a Java variable as "being stored in main memory". More precisely that means,
 that every read of a volatile variable will be read from the computer's main memory, and not from the CPU cache, and
 that every write to a volatile variable will be written to main memory, and not just to the CPU cache. 
 
 * [Volatile Varaible -JavaRevisited](http://javarevisited.blogspot.in/2011/06/volatile-keyword-java-example-tutorial.html#axzz4xIDNSnso)
 * [Volatile Variable - Dzone](https://dzone.com/articles/java-volatile-keyword-0)
 * [Volatile Variable - JENKOV](http://tutorials.jenkov.com/java-concurrency/volatile.html)
 
### What is static variable ?
In computer programming, a static variable is a variable that has been allocated "statically", meaning that its
lifetime (or "extent") is the entire run of the program.
