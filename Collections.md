# Collections

### Why collection is required ?
There are several reasons we require collections. So here it is.

 * When input size is dynamic.
 * Collection framework is nothing but the data structure in Java. So we can use it’s functionality instead of writing too much
 code.
 * Whenever you are required to store heterogeneous data.
 * When data grows and shrinks frequently.
 * Arrays are not resizable.
 * Java Collections Framework provides lots of different useful data types, such as linked lists (allows insertion anywhere in
 constant time), resizeable array lists (like Vector but cooler), red-black trees, hash-based maps (like Hashtable but cooler).
 * Java Collections Framework provides abstractions, so you can refer to a list as a List, whether backed by an array list or
 a linked list; and you can refer to a map/dictionary as a Map, whether backed by a red-black tree or a hashtable
 
 ### What are the important interfaces in collection ?
 [Important interfaces in collections](https://www.programcreek.com/2009/02/the-interface-and-class-hierarchy-for-collections/)
 [Collection in java](https://www.javatpoint.com/collections-in-java)
 
 ### Brief about list interface in java?
 [List interface in java](https://docs.oracle.com/javase/tutorial/collections/interfaces/list.html)
 
 ### Arraylist with example ?
 [ArrayList with example](https://beginnersbook.com/2013/12/java-arraylist/)
 
 ### Can ArrayList have duplicate values ?
 Yes
 
 ### How do you iterate around an ArrayList using iterator?
 [ArrayList with Iterator](http://www.java-examples.com/iterate-through-elements-java-arraylist-using-iterator-example)
    
 ### How do you sort an ArrayList ?
Collections.sort(testList);
Collections.reverse(testList);

### Sort List using Comparable or Comparator Interfaces?
[Sort using comparable or comparator](https://beginnersbook.com/2013/12/java-arraylist-of-object-sort-example-comparable-and-comparator/)

### What is Vector class in Java and how it differs from ArrayList ?
Vector implements a dynamic array. It is similar to ArrayList, but with two differences −
* Vector is synchronized.
* Vector contains many legacy methods that are not part of the collections framework.

Vector proves to be very useful if you don't know the size of the array in advance or you just need one that can change sizes over the lifetime of a program.

### What is LinkedList ? What interface does it implements ?
A linked list is a linear data structure where each element is a separate object. Each element (we will call it a node) of a list is comprising of two items - the data and a reference to the next node. The last node has a reference to null. The entry point into a linked list is called the head of the list.

[LinkList in Java](https://www.javatpoint.com/java-linkedlist)

### Describe about sets in Java ?
* Set is an interface which extends Collection. It is an unordered collection of objects in which duplicate values cannot be stored.
* Basically, Set is implemented by HashSet, LinkedSet or TreeSet (sorted representation).
* Set has various methods to add, remove clear, size, etc to enhance the usage of this interface

[Sets - Oracle Documentation](https://docs.oracle.com/javase/tutorial/collections/interfaces/set.html)
[Sets - GeeksForGeeks](http://www.geeksforgeeks.org/set-in-java/)

### Documenation about Java Collection ? 
[Java collection](http://www.beingjavaguys.com/2013/03/java-collection-framework.html)

### Difference between a set and a sortedSet ?
It is not a logical failure but a property by design. Note that if your comparison algorithm is consistent with equals,
a.compareTo(b) == 0 will be equivalent to a.equals(b).

The javadoc is actually very explicit about it:

    The behavior of a sorted set is well-defined even if its ordering is inconsistent with equals; it just fails to obey the general contract of the Set interface.

Is that useful?

That actually gives flexibility where you want to reach a specific behaviour. Let's say for example that you want to put strings in your SortedSet and have them sorted ignoring the case, you can use:
```
Set<String> set = new TreeSet<> (String.CASE_INSENSITIVE_ORDER);
```
That will achieve the expected result, but this:
```
set.add("ABC");
set.add("abc");
```
will only add one string to your set because they will be deemed equal with that specific comparator.

