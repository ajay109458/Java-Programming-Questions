# Advanced object oriented concepts

### What is polymorphism?
Polymorphism is the ability of an object to take on many forms. The most common use of polymorphism in OOP occurs when a parent class
reference is used to refer to a child class object. Any Java object that can pass more than one IS-A test is considered to be 
polymorphic.

### What is the use of instanceof operator in Java?
The java instanceof operator is used to test whether the object is an instance of the specified type (class or subclass or interface).
The instanceof in java is also known as type comparison operator because it compares the instance with type. It returns either true
or false.

### What is meant by coupling in Java?
Tight coupling is when a group of classes are highly dependent on one another.

This scenario arises when a class assumes too many responsibilities, or when one concern is spread over many classes rather than 
having its own class.

Loose coupling is achieved by means of a design that promotes single-responsibility and separation of concerns.

A loosely-coupled class can be consumed and tested independently of other (concrete) classes.

Interfaces are a powerful tool to use for decoupling. Classes can communicate through interfaces rather than other concrete classes,
and any class can be on the other end of that communication simply by implementing the interface.

Example of tight coupling:
```
class CustomerRepository
{
    private readonly Database database;

    public CustomerRepository(Database database)
    {
        this.database = database;
    }

    public void Add(string CustomerName)
    {
        database.AddRow("Customer", CustomerName);
    }
}

class Database
{
    public void AddRow(string Table, string Value)
    {
    }
}
```

Example of loose coupling:

```
class CustomerRepository
{
    private readonly IDatabase database;

    public CustomerRepository(IDatabase database)
    {
        this.database = database;
    }

    public void Add(string CustomerName)
    {
        database.AddRow("Customer", CustomerName);
    }
}

interface IDatabase
{
    void AddRow(string Table, string Value);
}

class Database : IDatabase
{
    public void AddRow(string Table, string Value)
    {
    }
}
```

###  What is cohesion ?
Cohesion : Cohesion is the OO principle most closely associated with making sure that a class is designed with a single,
well-focused purpose.

An element’s cohesion is a measure of whether its responsibilities form a meaningful unit. For example, a class that parses 
both dates and URLs is not coherent, because they’re unrelated concepts. Think of a machine that washes both clothes and
dishes—it’s unlikely to do both well.2 At the other extreme, a class that parses only the punctuation in a URL is unlikely to 
be coherent, because it doesn’t represent a whole concept. To get anything done, the programmer will have to find other parsers 
for protocol, host, resource, and so on. Features with “high” coherence are easier to maintain.

### What is encapsulation ?
Encapsulation is one of the four fundamental OOP concepts. The other three are inheritance, polymorphism, and abstraction.
Encapsulation in Java is a mechanism of wrapping the data (variables) and code acting on the data (methods) together as a single unit.

### What is an inner class ?
In object-oriented programming (OOP), an inner class or nested class is a class declared entirely within the body of another
class or interface. It is distinguished from a subclass.

### What is a static inner class?
A static class i.e. created inside a class is called static nested class in java. It cannot access non-static data members and methods.
It can be accessed by outer class name. It can access static data members of outer class including private

### What is anonymous class ?
Anonymous Classes. Anonymous classes enable you to make your code more concise. They enable you to declare and instantiate a class at 
the same time.
Accessing Local Variables of the Enclosing Scope, and Declaring and Accessing Members of the Anonymous Class.

### Can you create an inner class inside a method? 
```
public final class Test {
  // In this method.
  private void test() {
    // With this local variable.
    final List<String> localList = new LinkedList<String>();
    // We can define a class
    class InnerTest {
      // Yes you can!!
      void method () {
        // You can even access local variables but only if they are final.
        for ( String s : localList ) {
          // Like this.
        }
      }
    }
  }

}
```
