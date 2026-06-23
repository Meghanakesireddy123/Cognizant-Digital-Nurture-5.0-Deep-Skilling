# Exercise 1: Implementing the Singleton Pattern

## Objective

To implement the Singleton Design Pattern and ensure that only one instance of the Logger class exists throughout the application lifecycle.

---

## Project Name

SingletonPatternExample

---

## Logger.java

```java
package com.singleton;

public class Logger {

    private static Logger instance;

    private Logger() {
        System.out.println("Logger Instance Created");
    }

    public static Logger getInstance() {

        if(instance == null) {
            instance = new Logger();
        }

        return instance;
    }

    public void log(String message) {
        System.out.println("LOG : " + message);
    }
}
```

---

## SingletonTest.java

```java
package com.singleton;

public class SingletonTest {

    public static void main(String[] args) {

        Logger logger1 = Logger.getInstance();

        Logger logger2 = Logger.getInstance();

        logger1.log("Application Started");

        logger2.log("User Logged In");

        System.out.println(
                "Logger1 HashCode : "
                        + logger1.hashCode());

        System.out.println(
                "Logger2 HashCode : "
                        + logger2.hashCode());

        if(logger1 == logger2) {
            System.out.println(
                    "Only One Logger Instance Exists");
        }
    }
}
```

---

## Explanation

1. Constructor is declared private.
2. Static instance variable stores the only object.
3. getInstance() method returns the same object every time.
4. Singleton pattern prevents multiple object creation.

---

## Expected Output

```text
Logger Instance Created

LOG : Application Started

LOG : User Logged In

Logger1 HashCode : 12345678

Logger2 HashCode : 12345678

Only One Logger Instance Exists
```

---

## Result

Successfully implemented the Singleton Design Pattern. Only one Logger object was created and reused throughout the application.
