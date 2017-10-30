# Class Question

### What is a class ?
A class is a blueprint from which individual objects are created.

### What is a object ?
An entity that has state and behavior is known as an object e.g. chair, bike,
marker, pen, table, car etc. It can be physical or logical (tangible and intangible). The example of intangible object 
is banking system. 

Real-world objects share two characteristics: They all have state and behavior. Dogs have state (name, color, breed, hungry)
and behavior (barking, fetching, wagging tail). Bicycles also have state (current gear, current pedal cadence, current speed) 
and behavior (changing gear, changing pedal cadence, applying brakes). Identifying the state and behavior for real-world objects 
is a great way to begin thinking in terms of object-oriented programming.

### What is state of an object ?
An object-oriented system integrates the terms of code and data using the concept of an "object". An object has state (data) and 
ehavior (code). Hence, the states of object are the instances(variables) inside the object that contains the data.

###  What is behavior of an object?
An object's state is defined by its attributes. An object's attributes are usually static, and the values of the attributes are
usually dynamic. The term "behavior" refers to how objects interact with each other, and it is defined by the operations
an object can perform.

### What is the super class of every class in Java?
Object class is the super most class for all the class in JAVA. Class Object is the root of the class hierarchy. Every class
has Object as a superclass. All objects, including arrays, implement the methods of this class.

### Explain about toString method ?
The main purpose of toString is to generate a String representation of an object, means the return value is always a String.
In most cases this simply is the object's class and package name, but on some cases like StringBuilder you will got actually
a String-text.

### What is the equals method in Java?
The equals() method compares two objects for equality and returns true if they are equal. The equals() method provided in the 
Object class uses the identity operator ( == ) to determine whether two objects are equal.

### What are the important things to consider when implementing equals method?
```
@Override
public boolean equals(Object o) {
    // self check
    if (this == o)
        return true;
    // null check
    if (o == null)
        return false;
    // type check and cast
    if (getClass() != o.getClass())
        return false;
    Person person = (Person) o;
    // field comparison
    return Objects.equals(firstName, person.firstName)
            && Objects.equals(lastName, person.lastName);
}
```
[Equality Contract](https://www.sitepoint.com/implement-javas-equals-method-correctly/)

### What is the Hashcode method used for in Java?
Returns a hash code value for the object. The general contract of hashCode is: Whenever it is invoked on 
the same object more than once during an execution of a Java application, the hashCode method must consistently 
return the same integer, provided no information used in equals comparisons on the object is modified.

### Explain inheritance with examples 
Inheritance is a process of defining a new class based on an existing class by extending its common data members and methods.
Inheritance allows us to reuse of code, it improves reusability in your java application.
Note: The biggest advantage of Inheritance is that the code that is already present in base class need not be rewritten
in the child class.

```
class Teacher {
   String designation = "Teacher";
   String collegeName = "Beginnersbook";
   void does(){
	System.out.println("Teaching");
   }
}

public class PhysicsTeacher extends Teacher{
   String mainSubject = "Physics";
   public static void main(String args[]){
	PhysicsTeacher obj = new PhysicsTeacher();
	System.out.println(obj.collegeName);
	System.out.println(obj.designation);
	System.out.println(obj.mainSubject);
	obj.does();
   }
}
```

### What is method overloading?
Method Overloading is a feature that allows a class to have more than one method having the same name, 
if their argument lists are different. 

### What is method overriding?
Method overriding, in object-oriented programming, is a language feature that allows a subclass or child 
class to provide a specific implementation of a method that is already provided by one of its superclasses or parent classes.

###  Can super class reference variable can hold an object of sub class?
In Java, all non-static methods are "virtual", meaning that they are based on the runtime type of the underlying object rather 
than the type of the reference that points to that object. Therefore, it doesn't matter which type you use in the declaration
of the object, the behavior will be the same.

What the declaration does affect, is the methods that are visible at compile-time. If SubClass has a method that SuperClass 
does not (let's call it subMethod()), and you construct your object as
```
SuperClass s = new SubClass();
```
Then you will only be able to call methods on it that are available on SuperClass. That is, attempting to call s.subMethod()
will give you a compile time error. But, as you have discovered, if there methods are present in SuperClass, 
but overridden by SubClass, it will be the overridden method that will be executed.

Static methods, on the other hand, are not virtual. Running the code below
```
public class StaticTest {
    public static void main(String[] args) {
        SuperClass s = new SubClass();
        s.method();  // bad idea - calling static method via an object reference
    }

    public static class SuperClass {
        public static void method() {
            System.out.println("SuperMethod");
        }
    }

    public static class SubClass extends SuperClass {
        public static void method() {
            System.out.println("SubMethod");
        }
    }
}
```
prints out "SuperMethod". You should rarely care, however, that static methods are non-virtual because you should
never call them via an object reference as I have done above. You should call them via the class name:
```
SuperClass.method();
```

### Is multiple inheritance allowed in Java?
Multiple Inheritance is not allowed in Java directly , but through interfaces it is allowed. 
Reason : Multiple Inheritance : Introduces more complexity and ambiguity. One of the most common scenario is Diamond problem.

### What is Interface in Java ?
An interface in java is a blueprint of a class. It has static constants and abstract methods.

The interface in java is a mechanism to achieve abstraction. There can be only abstract methods in the java interface not
method body. It is used to achieve abstraction and multiple inheritance in Java.

Java Interface also represents IS-A relationship.

It cannot be instantiated just like abstract class.

[Stackoverflow - Interface explained](https://stackoverflow.com/questions/1321122/what-is-an-interface-in-java)

### How to define an interface ?
```
public interface GroupedInterface extends Interface1, Interface2, Interface3 {

    // constant declarations
    
    // base of natural logarithms
    double E = 2.718282;
 
    // method signatures
    void doSomething (int i, double x);
    int doSomethingElse(String s);
}
```

### What is an interface in Java.

* Before Java 8 interfaces are pure abstract classes which allow us to define public static final variables and public 
abstract methods(by default).
* In java 8 introduced static methods and default methods in interfaces. 
* Java 8 Interface Static and Default Methods
* We can develop interfaces by using "interface" keyword.  
* A class will implements all the methods in an interface.

### What will happen if we define a concrete method in an interface?
* By default interface methods are abstract.
* if we declare any concrete method in an interface compile time error will come.

### Can we create non static variables in an interface?

* No.We can not create non static variables in an interface.
* If we try to create non static variables compile time error comes.
* By default members will be treated as public static final variables so it expects some value to be initialized.

### What will happen if we not initialize variables in an interface.

Compile time error will come because by default members will be treated as public static final variables so it expects
some value to be initialized.

### Can we declare interface members as private or protected?
No

### What is an abstract class?
Abstract classes are classes that contain one or more abstract methods. An abstract method is a method that is declared, 
but contains no implementation.
Abstract classes may not be instantiated, and require subclasses to provide implementations for the abstract methods.

### When do you use an abstract class?
bstract Classes are a good fit if you want to provide implementation details to your children but don't want to allow an 
instance of your class to be directly instantiated (which allows you to partially define a class). If you want to simply 
define a contract for Objects to follow, then use an Interface.

### How do you define an abstract method?
An abstract class is a class that is declared abstract—it may or may not include abstract methods.
Abstract classes cannot be instantiated, but they can be subclassed.

An abstract method is a method that is declared without an implementation (without braces, and followed by a semicolon),
like this:
```
abstract void moveTo(double deltaX, double deltaY);
```
If a class includes abstract methods, then the class itself must be declared abstract, as in:
```
public abstract class GraphicObject {
   // declare fields
   // declare nonabstract methods
   abstract void draw();
}
```

### Compare abstract class vs interface?
1.Main difference is methods of a Java interface are implicitly abstract and cannot have implementations. 
A Java abstract class can have instance methods that implements a default behavior. 
2.Variables declared in a Java interface is by default final. An abstract class may contain non-final variables.

### What is a constructor?
A constructor is a special method of a class or structure in object-oriented programming that initializes an object of that
type. A constructor is an instance method that usually has the same name as the class, 
and can be used to set the values of the members of an object, either to default or to user-defined values.

### What is a default constructor in java ?
a "default constructor" refers to a nullary constructor that is automatically generated by the compiler if no constructors
have been defined for the class. 
The default constructor implicitly calls the superclass's nullary constructor, then executes an empty body.

### What is the use of this()?
Using the this Keyword. Within an instance method or a constructor, this is a reference to the current object — the object whose
method or constructor is being called. You can refer to any member of the current object from within an instance method or a
constructor by using this.

### Can a constructor be called directly from a method?
Constructors can't be called directly; they are called implicitly when the new keyword creates an object. Methods can be called
directly on an object that has already been created with new.


