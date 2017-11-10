---
title: 'Painful threading to painless threading'
date: 2016-09-08 21:31:40 +0200
author: amit-upadhyay-it
categories: [java]
---

**Thread** – is an independent path of execution within a program. Many threads can run concurrently within a program and that way we say that multithreading refers to two or more task executing concurrently within a single program.


[**Thread class (java.lang.Thread)**](https://docs.oracle.com/javase/7/docs/api/java/lang/Thread.html)

Every Thread in java is created and controlled by the `java.lang.Thread` class. Whenever we create an object of Thread class then we say that we have created a Thread. Suppose that I have created 3 objects of Thread class `t1`, `t2`, `t3` then we can say that we have created 3 threads. The important thing is to assign code to these threads, i.e. the codes which will get executed by these threads.

Before learning how to attach segment/snippet of code with a thread we will see way to create a Thread.

**Benefits of creating Thread**

Normally program gets executed sequentially, so after execution of first statement the second statement will get executed and so on. Now if the first statement and second statement are independent from each other then we can even run them parallel. This will save the time in execution of the program.

**Creating Thread**

There are two ways to create Thread in java

* Implement the Runnable interface. (java.lang.Runnable),
* By extending the Thread class (java.lang.Thread).

**Steps involved to implement the concept of Thread**

* Create the object of Thread class.
* Attach the segment of code with the object of Thread class which should run on execution of the Thread.

**NOTE**: We use multithreading for the concurrent execution of segments which are totally independent from each other.😄


Threads using Runnable Interface
Our objective –
- Create Thread
- Attach code to Thread
- Executing Thread

**a) Create Thread**

```java
Thread t1 = new Thread(..); // .. represent arguments
Thread t2 = new Thread(..); // .. represent arguments
```

Now the process of creation of thread is done, next objective is to attach the code snippet to the
Thread.

**b) Attaching code**

For this we make a class:

Example:
```java
class A
{
	function(){}
}
```

Suppose that I want the code inside function() method to get attached with the Thread. For this we need to create object of class A and then pass that object in the constructor of Thread class which create the Thread.

Now the question is **Since the Thread class is already predefined, so what type of argument does
the constructor of Thread class takes?**

One thing is clear that we need to pass the object of class A in the constructor of Thread class but the class A has been created now in our program. And passing the reference of class A as argument in constructor of Thread may result in type mismatching.

Now for this reason we use interface. We have Runnable interface (a predefined interface). There is only one method declared inside Runnable interface and that is **run()** method.

Now class A will implement the Runnable interface so it is important to **override the run()** method.

So we have to write the class A as :

```java
class A
{
  public void run()
  {
  	function(){}
  }
}
```
or we can just replace the body of method function() with the body of run() function.


**Benefits of implementing Runnable interface**

Since A implements, the Runnable interface, so any reference variable of Runnable interface can be
kept in the reference variable of class A (i.e. object of class A).

i.e.
```java
 Runnable r1 = new A();
```

Since Runnable is predefined so we can say that constructor of Thread class can receive a Runnable
type of value. i.e. we can pass the object which has implemented the Runnable interface into the
constructor of Thread class.

So we can say that one of the constructor of Thread class could be something like :

```java
Thread (Runnable r1)
{
}
```

**c) To execute Thread**

`t1.start(); // this will start execution of Thread t1`

Example Program :

```java

class A implements Runnable
{
  @Override
  public void run()
  {
    for(int i = 1; i <= 10; ++i)
    {
    	System.out.println("Thread A "+i);
    }
  }
}
class B implements Runnable
{
  @Override
  public void run()
  {
    for (int i = 1; i <= 10; ++i)
    {
    	System.out.println("Thread B "+i);
    }
  }
}

public class ExampleThreading {
  public static void main(String arp[])
  {
    Thread t1 = new Thread(new A());
    Thread t2 = new Thread(new B());
    
    t1.start();
    t2.start();
  }
}

```

Sample output:
```
Thread A 1
Thread A 2
Thread B 1
Thread B 2
Thread B 3
Thread B 4
Thread B 5
Thread B 6
Thread B 7
Thread A 3
Thread A 4
Thread A 5
Thread A 6
Thread A 7
Thread A 8
Thread A 9
Thread A 10
Thread B 8
Thread B 9
Thread B 10
```

**Threading using Thread class**

Here we will extend the Thread class. Again objective will be same :

1. Creating Thread
1. Attaching code to thread
1. Executing Thread.


Here our class will inherit Thread class and override the run() method. The code snippet which we need to run of the Thread will be inside the run() method.

```java
class A extends Thread
{
  public void run()
  {
  	function(){}
  }
}
```

The object of class A is also a Thread. So to create a new Thread we can write:

`A obj = new A();`

And now we can call the method of Thread class using object subclass of Thread class (i.e. object of A) So to start a Thread we can write :

`obj.start();`


This seems to be little bit simple, but there is difference in implementing Thread through Runnable interface and extending Thread class.

Example :

```java
class A extends Thread
{
  @Override
  public void run()
  {
    for(int i = 1; i <= 10; ++i)
    {
    	System.out.println("Thread A "+i);
    }
  }
}

class B extends Thread
{
  @Override
  public void run()
  {
    for (int i = 1; i <= 10; ++i)
    {
    	System.out.println("Thread B "+i);
    }
  }
}


public class ExampleThreading {
  public static void main(String arp[])
  {
    A t1 = new A();
    B t2 = new B();
    
    t1.start();
    t2.start();
  }
}

```

**Difference between implementing Runnable and extending Thread**

Implementing Runnable to use Threading is better because in Java we don't have multiple inheritance, so here as Thread is parent class of A, so it is not possible to have any other parent of A where as if we use Runnable interface then we can even have a parent of class A (other than the Thread class).

**Thread States**

A java Thread is always in one of the several states which could be :

1. New Thread
1. Runnable
1. Not Runnable
1. Dead

So, there are 4 stages of thread in its whole life

#### **1 st state : New Thread**

A Thread is in this state when the instantiate of a Thread object gets created but doesn't get started.] A Thread starts life in the Ready-to-run state. You can call only the start() or stop() method when the thread is in this state. Calling any method besides start() or stop() cause an IllegalThreadStateException ( A descendant class of RuntimeException)

#### **2 nd state: Runnable**

When the start() method is invoked on a new Thread() it gets to the runnable state r running state by calling run() method.

A Runnable thread may actually be running or may be waiting its turn to run.


#### **3 rd state: Not Runnable**

A Thread becomes Not Runnable when one of the following four events occurs:

1. When sleep() method is invoked and it sleeps for a specified amount of time.
1. When suspend() method is invoked.
1. When wait() method is invoked and the thread waits for notification of few resource or waits for the completion of another thread or wait to acquire a lock of an object.
1. Thread is blocking an I/O and waits for its completion.



- sleep() is a method in Thread class and the argument of sleep is time in milliseconds.
- suspend() method is not used these days.

**Switching from Not Runnable to Runnalb state**

- If a thread has been put to sleep, then specified number of milliseconds must elapse ( or it must be interrupted).
- If a thread has been suspended, then its resume() method must be invoked.
- If a thread is waiting on a condition variable, whatever object owns the variable must relinquish it by calling either notify() or notifyAll().
- If a thread is blocked or I/O, then I/O must be completed.

#### **4 th state: Dead State**

A thread enters this state when run() method has finished executing or when the stop() method is
invoked or when any exception occurs. Once in this state, the thread can not ever run again.


### **Thread Priority**

In java we can specify the priority of each thread relative to the other thread. Those threads having higher priority get grated access to the available resources. The thread priority is specified as a integer number.

By default there is some priority number set for a thread even if we don't set any priority to a thread.


- **Thread priority is inherited**

A java Thread inherits its priority from the thread that created it.
By default our program runs into a thread whose priority number is 5. So each thread that we make is a child thread of parent thread. We can change the priority level if we want.

#### - **Setting thread priority**

We can modify a thread's priority at any time after its creation using a method setPriority() and retrieve the thread priority by using a method `getPriority()`.

The following static final integer constant are defined in the Thread class.

```java
MIN_PRIORITY(0) : lowest priority
NORM_PRIORITY(5) : default priority
MAX_PRIORITY(10) : highest priority
```


##  **Synchronizing multiple thread**

We have created more than one thread know as multiple threading, but multiple threading has an issue which is :

When we start two or more threads within a program, there may be a situation when multiple threads
try to access the same resource. Whenever multiple threads are trying to access a same object, then we have to synchronize the thread such that unless the work of thread one gets completely executed for the object, no other thread should interfere its execution.

`Synchronous – in sequence
Asynchronous – parallel execution
`

**NOTE** : when we start two or more threads within a program there may be a situation when multiple threads try to access the same resource.

So there is need to synchronize the action of multiple threads and make sure that only one thread can access the resource at a given point of time.


### **Example of unsynchronized thread**

```java
class Account
{
  private int balance;
  
  public Account(int balance){ this.balance = balance; }
  
  public boolean isSufficient(int amt)
  {
    if (amt > balance)
    return false;
    else
    return true;
  }
  public void withdrawel(int amt)
  {
    balance -= amt;
    System.out.println("The money withdrawn is "+amt);
    System.out.println("Available balance is "+balance);
  }
}

class Customer implements Runnable
{
  private String name;
  private Account account;
  public Customer(Account account, String name)
  {
    this.name = name;
    this.account = account;
  }
  @Override
  public void run()
  {
    java.util.Scanner scanner = new java.util.Scanner(System.in);
    System.out.println("Enter amount to widhdraw : ");
    int amount = scanner.nextInt();
    if(account.isSufficient(amount))
    	account.withdrawel(amount);
    else
    	System.out.println("Insufficient balance");
    scanner.close();
  }
}


public class ExampleThreading {
  public static void main(String []args)
  {
    Account a = new Account(1000);
    Customer c1 = new Customer(a, "Amit"), c2 = new Customer(a, "Kat");
    
    Thread t1 = new Thread(c1), t2 = new Thread(c2);
    t1.start(); t2.start();
  }
}
```


Now lets see how to synchronize the threads.

We want to synchronize the code written inside the run() method. For this we write keyword `synchronized(){}`

**NOTE**: Syntax of synchronized may look like a method, but it is a keyword in java.

**Argument inside the synchronized**

Again, I choose wrong word because synchronized is not a function. But I need to write the “shared
resource” (i.e. the object that is getting shared) inside the parenthesis. Now all the code that we want to synchronize will be written inside the curly braces.

Eg :

```java
@Override
public void run()
{
  java.util.Scanner scanner = new java.util.Scanner(System.in);
  System.out.println("Enter amount to widhdraw : ");
  int amount = scanner.nextInt();
  synchronized (account)
  {
    if(account.isSufficient(amount))
    	account.withdrawel(amount);
    else
    	System.out.println("Insufficient balance");
  }
  scanner.close();
}
```






Thank you 🎂 👏
