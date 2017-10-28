# Java Platform Questions

### Why Java is so popular ?
* Platform Independence
* Object oriented

### What is platform independence ?
It describes that you can implement things on one machine and can run on other machine without any change.

### What is bytecode?
Bytecode is computer object code that is processed by a program, usually referred to as a virtual machine, 
rather than by the "real" computer machine, the hardware processor.The best-known language today that uses 
the bytecode and virtual machine approach is Java.

### Compare JDK vs JVM vs JRE
* JVM is Java Virtual Machine -- the JVM actually runs Java bytecode.
* JDK is Java Developer Kit -- the JDK is what you need to compile Java source code.
* JRE is Java Runtime Environment -- is what you need to run a Java program and contains a JVM, among other things.

###  What are the important differences between C++ and Java ?
[Differences between C++ and Java](http://cs-fundamentals.com/tech-interview/java/differences-between-java-and-cpp.php)

### What is the role for a classloader in Java ?
The Java Classloader is a part of the Java Runtime Environment that dynamically loads Java classes into the Java Virtual Machine. 
Usually classes are only loaded on demand.

* [Class Loader - Stackoverflow](https://stackoverflow.com/questions/2424604/what-is-a-java-classloader)
* [Class Loader - JavaWorld](https://www.javaworld.com/article/2077260/learn-java/learn-java-the-basics-of-java-class-loaders.html)

### What are the types of class loaders in Java?

* Bootstrap Class Loader. Bootstrap class loader loads java's core classes like java.lang, java.util etc.
* Extensions Class Loader. JAVA_HOME/jre/lib/ext contains jar packages that are extensions of standard core java classes.
* System Class Loader.

### What is the use of classpath in Java?
Classpath is a parameter in the Java Virtual Machine or the Java compiler that specifies the location of user-defined classes and packages. 
The parameter may be set either on the command-line, or through an environment variable.

### What is bootstrapping in Java?
When a JVM starts up, a special chunk of machine code runs that loads the system classloader. This machine code is known as the Bootstrap / Primordial (or sometimes - Null) 
classloader. It is not a Java class at all, as are all other classloaders.

### What is bootstrap class loader in Java?
Whenever a new JVM is started by typing java MyMainClass , the "bootstrap class loader" is responsible for loading key Java classes like java.lang.Object and other runtime code into memory first.
The runtime classes are packaged inside of the JRE\lib\rt.jar file.

