# Miscellaneous Questions

### What are the default values in an array ?
If we don’t assign values to array elements, and try to access them, compiler does not produce error as in case of simple variables. 
Instead it assigns values which aren’t garbage.

Below are the default assigned values.

    boolean : false
    int : 0
    double : 0.0
    String : null
    User Defined Type : null
    
### How do you loop around an array using enhanced for loop?
for (int i=0; i < array.length; i++) {
    System.out.println("Element: " + array[i]);
}

to the newer form

for (String element : array) {
    System.out.println("Element: " + element);
}

### How to print content of an array ?
Since Java 5 you can use Arrays.toString(arr) or Arrays.deepToString(arr) for arrays within arrays. Note that the Object[] version
calls .toString() on each object in the array. The output is even decorated in the exact way you're asking.

Examples:
Simple Array:
```
String[] array = new String[] {"John", "Mary", "Bob"};
System.out.println(Arrays.toString(array));
```
Output:
```
[John, Mary, Bob]
```
Nested Array:
```
String[][] deepArray = new String[][] {{"John", "Mary"}, {"Alice", "Bob"}};
System.out.println(Arrays.toString(deepArray));
//output: [[Ljava.lang.String;@106d69c, [Ljava.lang.String;@52e922]
System.out.println(Arrays.deepToString(deepArray));
```
Output:
```
[[John, Mary], [Alice, Bob]]
```
double Array:
```
double[] doubleArray = { 7.0, 9.0, 5.0, 1.0, 3.0 };
System.out.println(Arrays.toString(doubleArray));
```
Output:
```
[7.0, 9.0, 5.0, 1.0, 3.0 ]
```
```
int Array:

int[] intArray = { 7, 9, 5, 1, 3 };
System.out.println(Arrays.toString(intArray));
```
Output:
```
[7, 9, 5, 1, 3 ]
```

### How to compare two arrays ?
A simple way is to run a loop and compare elements one by one. Java provides a direct method Arrays.equals() to compare two arrays.
Actually, there is a list of equals() methods in Arrays class for different primitive types (int, char, ..etc) and one for Object
type (which is base of all classes in Java).
```
// we need to import java.util.Arrays to use Arrays.equals().
import java.util.Arrays;
class Test
{
    public static void main (String[] args) 
    {
        int arr1[] = {1, 2, 3};
        int arr2[] = {1, 2, 3};
        if (Arrays.equals(arr1, arr2))
            System.out.println("Same");
        else
            System.out.println("Not same");
    }
}
```

### What are enums and why they are useful ?
You should always use enums when a variable (especially a method parameter) can only take one out of a small set of possible values.
Examples would be things like type constants (contract status: "permanent", "temp", "apprentice"), or flags ("execute now",
"defer execution").

If you use enums instead of integers (or String codes), you increase compile-time checking and avoid errors from passing in invalid 
constants, and you document which values are legal to use.

BTW, overuse of enums might mean that your methods do too much (it's often better to have several separate methods, rather than
one method that takes several flags which modify what it does), but if you have to use flags or type codes, enums are the way to go.

As an example, which is better?
```
/** Counts number of foobangs.
 * @param type Type of foobangs to count. Can be 1=green foobangs,
 * 2=wrinkled foobangs, 3=sweet foobangs, 0=all types.
 * @return number of foobangs of type
 */
public int countFoobangs(int type)
```
versus
```
/** Types of foobangs. */
public enum FB_TYPE {
 GREEN, WRINKLED, SWEET, 
 /** special type for all types combined */
 ALL;
}

/** Counts number of foobangs.
 * @param type Type of foobangs to count
 * @return number of foobangs of type
 */
public int countFoobangs(FB_TYPE type)
```
A method call like:
```
int sweetFoobangCount = countFoobangs(3);
```
then becomes:
```
int sweetFoobangCount = countFoobangs(FB_TYPE.SWEET);
```
In the second example, it's immediately clear which types are allowed, docs and implementation cannot go out of sync, and the 
compiler can enforce this. Also, an invalid call like
```
int sweetFoobangCount = countFoobangs(99);
```
is no longer possible.

### What are variable arguments or varargs?
In JDK 5, Java has included a feature that simplifies the creation of methods that need to take a variable number of arguments.
This feature is called varargs and it is short-form for variable-length arguments.
A method that takes a variable number of arguments is a varargs method.
Prior to JDK 5, variable-length arguments could be handled two ways. One using overloaded method(one for each) and another put the
arguments into an array, and then pass this array to the method. Both of them are potentially error-prone and require more code.
The varargs feature offers a simpler, better option.
* [Varargs - GeeksForGeeks](http://www.geeksforgeeks.org/variable-arguments-varargs-in-java/)

### What is garbage collection ?
The garbage collector is a program which runs on the Java Virtual Machine which gets rid of objects which are not being used by 
a Java application anymore. It is a form of automatic memory management.

### When does garabage collection runs ?
It runs when it determines that it is time to run. A common strategy in generational garbage collectors is to run the collector when
an allocation of generation-0 memory fails. That is, every time you allocate a small block of memory (big blocks are typically placed
directly into "older" generations), the system checks whether there's enough free space in the gen-0 heap, and if there isn't,
it runs the GC to free up space for the allocation to succeed. Old data is then moved to the gen-1 heap, and when space runs out there,
the GC runs a collection on that, upgrading the data which has been there longest to the gen-2 heap, and so on. So the GC doesn't 
just "run". It might run on the gen-0 heap only (and most collections will do just that), or it might check every generation if it
really has to free up a lot of memory (which is only necessary fairly rarely).

But this is far from the only strategy. A concurrent GC runs in the background, cleaning up while the program is running. Some GC's 
might run as part of every memory allocation. An incremental collector might do that, scanning a few objects at every memory allocation.

The entire point in a garbage collector is that it should just do its thing without requiring any input from the user. So in general, 
you can't, and shouldn't, predict when it'll run.

Other JVM's are of course free to pick whichever strategy they like.

EDIT: The above part about Java and generational GC is not true. See below for more details:

The 1.0 and 1.1 Virtual Machines used a mark-sweep collector, which could fragment the heap after a garbage collection. 
Starting with Java 1.2, the Virtual Machines switched to a generational collector, which has a much better defragmentation
behavior (see Java theory and practice: Garbage collection and performance).

So Java actually has a generational GC for ages. What's new in Java 6 is the Garbage-First garbage collector (G1) that is available
in Java 6u14. According to the article claiming the release in 1.6.0_14: It is not enabled by default. The parallel collector is
still the default GC and is the most efficient GC for common household usage. G1 is meant to be an alternative for the concurrent 
collector. It is designed to be more predictable and enable fast allocation with memory regions design.


### Read about garbage collection and best practices 
[Garbage collection best practices](https://dzone.com/articles/java-garbage-collection-best-practices-tutorials-and-more)

### What are initialization blocks?
Initializer block contains the code that is always executed whenever an instance is created. It is used to declare/initialise 
the common part of various constructors of a class. The order of initialization constructors and initializer block doesn't matter, 
initializer block is always executed before constructor.

First of all, there are two types of initialization blocks:

    instance initialization blocks, and
    static initialization blocks.

This code should illustrate the use of them and in which order they are executed:
```
public class Test {

    static int staticVariable;
    int nonStaticVariable;        

    // Static initialization block:
    // Runs once (when the class is initialized)
    static {
        System.out.println("Static initalization.");
        staticVariable = 5;
    }

    // Instance initialization block:
    // Runs each time you instantiate an object
    {
        System.out.println("Instance initialization.");
        nonStaticVariable = 7;
    }

    public Test() {
        System.out.println("Constructor.");
    }

    public static void main(String[] args) {
        new Test();
        new Test();
    }
}
```
Prints:
```
Static initalization.
Instance initialization.
Constructor.
Instance initialization.
Constructor.
```

### What is tokenizing in java ?
The java.util.StringTokenizer class allows an application to break a string into tokens. This class is a legacy class that is retained 
for compatibility reasons although its use is discouraged in new code. Its methods do not distinguish among identifiers, numbers, 
and quoted strings.

### What is serialization ?
Simply speaking Serialization is a process of converting an Object into stream of bytes so that it can be transferred over a network 
or stored in a persistent storage.

Deserialzation is exact opposite - Fetch a stream of bytes from network or persistence storage and convert it back to the Object
with the same state.

Only thing to understand now is how those stream of bytes are interpreted or manipulated so that we get the exact same Object/ same
state. There are various ways to achieve that. Some of them are -

    XML : Convert Object to XML, transfer it over a network or store it in a file/db. Retrieve it and convert it back to the object 
    with same state. In Java we use JAXB(Java architecture for XML binding) library.(From java 6 it comes bundled with JDK).
    JSON :Same can be done by converting the Object to JSON (Javascript Object notation). Again there is GSON library that can be 
    used for this.
    Or we can use the Serialization that is provided by the OOP language itself. For eg. in Java you can serialize an Object my 
    making it implement Serializable interface and writing to Object Stream
    
### How do you serialize an object using serializable interface?
* [Serialization](https://www.javatpoint.com/serialization-in-java)
* [Serialization - geeksforgeeks](http://www.geeksforgeeks.org/serialization-in-java/)
