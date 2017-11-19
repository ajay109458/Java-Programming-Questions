# 50 Threading Questions

## What is a thread ?
Thread is an independent path of exectution. Its the way to take advantage of multiple CPU available in the system. By employing multiple
thread you can speed up bounded task. 

For example, 
If one thread takes 100 millisecond to complete a task, you can use 10 threads to complete that task in 10 millisecond. 

## What is difference between thread and process in java ?
* Thread is a subset of Process.
* A Process can have multiple threads. 
* Process runs on different memory space though threads for same process runs on same memory space. 

## How do you implement thread in Java ?
An instance of java.lang.Thread represents a thread but it needs a task to execute, which is defined by interface java.lang.Runtime

Since Thread class itself implements Runnable, so you can just extend Thread class or implement Runnable Interface. 

## When to use Runnable or Thread ?
You can create a thread by any of following operations
* Extending Thread class
* Implementing Runnable 

But out of these two which is better ?
Since java doesn't support multiple inheritence once you have extended your class with Thread class you can't extend your class with 
some other class. So it is suggested to implement Runnable interface. 

## Difference between Runnable and Callable in Java ?
Both Runnable and Callable represents the task that are intended to be executed in seperate thread. 

Runnable in from JDK 1.0 and Callable has been introduce in JDK 1.5

Callable call() can return a value and can throw an exception, which is not true for Runnable's run().

Callable call() method return reference to future object, which hold's the result of the computation.

## What is volatile variable ?
It gauranties that whenever it's value will be changed it will be visible to each thread. 

Non-volatile varible, when multiple threads are working on it. Thread first copy vaiable in cache and after change it again saves value
in the instance variable. Because of this if multiple threads are working on same variable it's state might not be correct. 

## What is Thread Safety ?
Thread safety is property of a object or code which gaurantees that if executed and use by multiple threads, read V/S write operation 
will behave as expected. 

## What happen if an execption occurs in a Thread ?
Whenever an execption occurs in a Thread and if that execption is not caught properly then Thread wil die. 

If an exception handler is registered it will get a callback.

## How you share data b/w two threads ?
You can share data b/w two threads using shared object or concurrent data structure. 

## Difference between `notify()` and `notifyAll()` ?
Simply put, it depends on why your threads are waiting to be notified. 
* Do you want to tell one of the waiting threads that something happened, 
* Or Do you want to tell all of them at the same time?

In some cases, all waiting threads can take useful action once the wait finishes. An example would be a set of threads waiting 
for a certain task to finish; once the task has finished, all waiting threads can continue with their business. 
In such a case you would use notifyAll() to wake up all waiting threads at the same time.

Another case, for example mutually exclusive locking, only one of the waiting threads can do something useful after being notified
(in this case acquire the lock). In such a case, you would rather use notify(). Properly implemented, you could use notifyAll()
in this situation as well, but you would unnecessarily wake threads that can't do anything anyway.

## What is a ThreadLocalVariable ? 
A variable created per thread is called ThreadLocalVariable. 

