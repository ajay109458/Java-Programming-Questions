# Wrapper Class Questions

### What is wrapper classes in Java ?
All the wrapper classes (Integer, Long, Byte, Double, Float, Short) are subclasses of the abstract class Number. 
The object of the wrapper class contains or wraps its respective primitive data type. Converting primitive data 
types into object is called boxing, and this is taken care by the compiler.

### What is the use of wrapper classes in Java?
Wrapper classes are used to convert any data type into an object. The primitive data types are not objects; they 
do not belong to any class; they are defined in the language itself. Sometimes, it is required to convert data types 
into objects in Java language.

### What is auto boxing ?
Autoboxing is the automatic conversion that the Java compiler makes between the primitive types and their corresponding 
object wrapper classes. For example, converting an int to an Integer, a double to a Double, and so on. If the conversion
goes the other way, this is called unboxing.

### What are the advantages of auto boxing ?
The addition of autoboxing and auto-unboxing greatly simplifies writing algorithms, eliminating the bait manually boxing and
unboxing of values. It is also helpful to avoid mistakes. It is also very important for generics, who only operate on objects. 
Lastly, autoboxing facilitates work with the Collections Framework.

### What is casting ?
Well, all casting really means is taking an Object of one particular type and “turning it into” another Object type. This
process is called casting a variable. This topic is not specific to Java, as many other programming languages support casting
of their variable types

### Why type casting is required in Java?
The cast can be to its own class type or to one of its subclass or superclass types or interfaces. Any object reference
can be assigned to a reference variable of the type Object, because the Object class is a superclass of every Java class.

#### What is Downcasting and Upcasting in Java?
upcasting means casting the object to a supertype, while downcasting means casting to a subtype. 
In java, upcasting is not necessary as it's done automatically.And it's usually referred as implicit casting.

### What is implicit casting?
Casts can be unsafe; they can fail at run-time or lose information. Implicit conversion is a type conversion or a primitive 
data conversion performed by the compiler to comply with data promotion rules or to match the signature of a method.
In Java, only safe implicit conversions are performed: upcasts and promotion

### What do you mean by Downcasting in Java?
In class-based programming, downcasting or type refinement is the act of casting a reference of a base class to one of its 
derived classes. In other words, when a variable of the base class (parent class) has a value of the derived class (child class),
downcasting is possible.



