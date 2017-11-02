# Exceptions

### Why exception handling is important ?
Most programs are very large, very complex and written by multiple people. This combination of factors almost always leads to
some kind of software bug. It's not that programmers are malicious, stupid or lazy .it's just that in the rush to meet a deadline
we often don't forsee every possible thing that a user can do to our programs and something is bound to happen.

In this respect error handling serves two purposes.

    First, it lets the user know, in a relatively friendly manner, that something has gone wrong and that they should contact 
    the technical support department or that someone from tech support has been notified. As we all know there's a HUGE difference
    between receiving a rather nasty, tech riddled notice that says something like "Object not set to reference of an object" etc.
    ... and receiving a nice popup type window that says "There has been an issue. Please contact the helpdesk".

    Second it allows the programmer to put in some niceties to aid in the debugging of issues. For instance ... in my code, I 
    typically write a custom error handler that takes in a number of parameters and spits back a nice, formatted message that 
    can either be emailed to the helpdesk, stashed in an event log, written to a log file etc.. The error message will contain 
    as much info as I can cram in there to help me figure out what happened, stack traces, function parameters, database calls 
    ... you name it. I like verbose error messages to help me figure out what actually happened. The user never has to see any 
    of it, they get the nice, friendly message above, letting them know that someone can figure out what's going on.
    
### What design pattern is used to implement exception handling features in most languages?
These patterns and best practices are often bound to a specific platform/language, so they are the first place to look for them.

    [Exception patterns wiki](http://wiki.c2.com/?ExceptionPatterns) is a general patterns resource.

As an example check the following links for java:

    [Best Practices for Exception Handling](http://www.onjava.com/pub/a/onjava/2003/11/19/exceptions.html)
    [15 Best practices about exception handling](http://codebuild.blogspot.in/2012/01/15-best-practices-about-exception.html)

Going through such materials would give you a general idea to follow in exception handling mechanisms.

Also check other SO questions:

    [Exception handling pattern](https://stackoverflow.com/questions/4589750/exception-handling-pattern)
    [Java Style: Properly handling exceptions](https://stackoverflow.com/questions/425281/java-style-properly-handling-exceptions?rq=1)
    
### What is the need for finally block?
[Stackovrflow](https://stackoverflow.com/questions/15768645/what-is-the-benefit-to-use-finally-after-try-catch-block-in-java)


###  In what scenarios is code in finally not executed?
If you call System.exit() the program exits immediately without finally being called.
A JVM Crash e.g. Segmentation Fault, will also prevent finally being called. i.e. the JVM stops immediately at this point and 
produces a crash report.
An infinite loop would also prevent a finally being called.
The finally block is always called when a Throwable is thrown. Even if you call Thread.stop() which triggers a ThreadDeath to 
be thrown in the target thread. This can be caught (it's an Error) and the finally block will be called.

### In Java, will the code in the finally block be called and run after a return statement is executed?
The answer to this question is a simple yes – the code in a finally block will take precedence over the return statement.

### Can try work without catch?
The try block defines which lines of code will be followed by the finally code. If an exception is thrown prior to the try
block, the finally code will not execute. The finally block always executes when the try block exits. So you can use finally
without catch but you must use try.

### Exception Hierarchy 
[Exception Hierarchy](https://www.programcreek.com/2009/02/diagram-for-hierarchy-of-exception-classes/)

### What is differece between Error and Exception in Java?
   Error "indicates serious problems that a reasonable application should not try to catch."

while

    An Exception "indicates conditions that a reasonable application might want to catch."

Error along with RuntimeException & their subclasses are unchecked exceptions. All other Exception classes are checked 
exceptions.

Checked exceptions are generally those from which a program can recover & it might be a good idea to recover from such 
exceptions programmatically. Examples include FileNotFoundException, ParseException, etc. A programmer is expected to check
for these exceptions by using the try-catch block or throw it back to the caller

On the other hand we have unchecked exceptions. These are those exceptions that might not happen if everything is in order, 
but they do occur. Examples include ArrayIndexOutOfBoundException, ClassCastException, etc. Many applications will use
try-catch or throws clause for RuntimeExceptions & their subclasses but from the language perspective it is not required 
to do so. Do note that recovery from a RuntimeException is generally possible but the guys who designed the class/exception
deemed it unnecessary for the end programmer to check for such exceptions.

Errors are also unchecked exception & the programmer is not required to do anything with these. In fact it is a bad idea 
to use a try-catch clause for Errors. Most often, recovery from an Error is not possible & the program should be allowed 
to terminate. Examples include OutOfMemoryError, StackOverflowError, etc.

Do note that although Errors are unchecked exceptions, we shouldn't try to deal with them, but it is ok to deal with 
RuntimeExceptions(also unchecked exceptions) in code. Checked exceptions should be handled by the code.

###  What is the difference between checked exceptions and unchecked exceptions?
[CheckedVsUncheckedException - GeeksForGeeks](http://www.geeksforgeeks.org/checked-vs-unchecked-exceptions-in-java/)

###  How do you throw an exception from a method?
[Exception throwing - From a method](https://docs.oracle.com/javase/tutorial/essential/exceptions/declaring.html)

### What are the options you have to eliminate compilation errors when handling checked exceptions?
[Eliminate exception](https://stackoverflow.com/questions/40794381/is-disabling-checked-exceptions-in-java-possible)

### How do you create a custom exception?
[Custom Exception](http://www.codejava.net/java-core/exception/how-to-create-custom-exceptions-in-java)

### Try with resources ?
[Try with Resources](http://tutorials.jenkov.com/java-exception-handling/try-with-resources.html)




