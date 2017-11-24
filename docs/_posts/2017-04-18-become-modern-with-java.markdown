---
title: 'Become modern with Java 8'
date: 2017-04-18 12:01:40 +0100
author: amit-upadhyay-it
categories: [java]
---

**Do you still have a habit of writing the Java programs in old fashion?** It's okay if you have, but I would suggest you become modern with `Java8`. You must be knowing that `Java8` came with the concept of `lambdas` and `stream APIs` and these things have been introduced long before.

{: .info .note}
**Why prefer lambdas?**


Lambdas let us write code in more readable and concise way. With the use of lambdas, we avoid writing `Anonymous classes`. Now as you know each anonymous class will result in the formation of a `.class` file which will result in the increase of `zar` file(built project). So if you have 10 anonymous classes that are 10 more classes in the final jar.

In Java 1.7 a new `JVM Opcode` was released named `invokedynamic` and Java 8 `Lambda` uses this. Java 8 lambda uses `invokedynamic` to call lambdas thus if you have 10 lambdas it will not result in any anonymous classes.

**Lets consider an example app where you have a list of people and you want to**:

- `sort` according to last name.
- print them.
- print people who have last name beginning with `P`.

### Programming:

First, we need to create a blueprint of `Person`.

```java
public class Person {

	private String firstName, lastName;
	int age;
	public Person(String firstName, String lastName, int age) {
		super();
		this.firstName = firstName;
		this.lastName = lastName;
		this.age = age;
	}
	public String getFirstName() {
		return firstName;
	}
	public void setFirstName(String firstName) {
		this.firstName = firstName;
	}
	public String getLastName() {
		return lastName;
	}
	public void setLastName(String lastName) {
		this.lastName = lastName;
	}
	public int getAge() {
		return age;
	}
	public void setAge(int age) {
		this.age = age;
	}
	@Override
	public String toString() {
		return "Person [firstName=" + firstName + ", lastName=" + lastName + ", age=" + age + "]";
	}
}
```

Thank you 👏
