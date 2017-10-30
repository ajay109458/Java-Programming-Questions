# String Questions

### Is string immutable in java?
String is immutable in Java. An immutable class is simply a class whose instances cannot be modified. 
All information in an instance is initialized when the instance is created and the information can not be modified.

### Why strings are immutable objects in Java?
Were String not immutable, a connection or file would be changed and lead to serious security threat. Mutable strings 
could cause security problem in Reflection too, as the parameters are strings. Efficiency The hashcode of string is 
frequently used in Java.
The string is Immutable in Java because String objects are cached in String pool. Another reason of why String class 
is immutable could die due to HashMap. Since Strings are very popular as HashMap key, it's important for them to be 
immutable so that they can retrieve the value object which was stored in HashMap.

### Why should you be careful about String concatenation(+) operator in loops ?
The reason is that a String object in Java is immutable. This means that whenever we use “+” to concatenate strings a 
new object is created. 

### How do you solve above problem?
Using StringBuilder 

```
StringBuilder sb = new StringBuilder();
         
int n = 100000;
for(int i=0; i<n; ++i){
    sb.append("2");
}

String res = sb.toString();
```

### What are differences between String and StringBuffer?
String is immutable, if you try to alter their values, another object gets created, whereas StringBuffer and StringBuilder 
are mutable so they can change their values. Thread-Safety Difference: The difference between StringBuffer and StringBuilder 
is that StringBuffer is thread-safe.

###### Mutability Difference:

String is immutable, if you try to alter their values, another object gets created, whereas StringBuffer and StringBuilder are mutable so they can change their values.

###### Thread-Safety Difference:

The difference between StringBuffer and StringBuilder is that StringBuffer is thread-safe. So when the application needs to be run only in a single thread then it is better to use StringBuilder. StringBuilder is more efficient than StringBuffer.

###### Situations:

* If your string is not going to change use a String class because a String object is immutable.
* If your string can change (example: lots of logic and operations in the construction of the string) and will only be accessed from a single thread, using a StringBuilder is good enough.
* If your string can change, and will be accessed from multiple threads, use a StringBuffer because StringBuffer is synchronous so you have thread-safety.

### What are differences between StringBuilder and StringBuffer?
StringBuffer and StringBuilder have the same methods with one difference and that's of synchronization. StringBuffer is synchronized( which means it is thread safe and hence you can use it when you implement threads for your methods) whereas StringBuilder
is not synchronized( which implies it isn't thread safe)


