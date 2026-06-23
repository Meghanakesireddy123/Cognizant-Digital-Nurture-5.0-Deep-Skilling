# Exercise: Logging Using SLF4J

## Objective

To implement logging in a Java application using SLF4J and Logback and demonstrate different logging levels such as ERROR and WARN.

---

## Project Name

SLF4JLoggingExample

---

## Required Dependencies

Add the following dependencies in pom.xml

```xml id="h6s1o4"
<dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-api</artifactId>
    <version>1.7.30</version>
</dependency>

<dependency>
    <groupId>ch.qos.logback</groupId>
    <artifactId>logback-classic</artifactId>
    <version>1.2.3</version>
</dependency>
```

---

## LoggingExample.java

```java id="lzb6y7"
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class LoggingExample {

    private static final Logger logger =
            LoggerFactory.getLogger(
                    LoggingExample.class);

    public static void main(String[] args) {

        logger.info(
                "Application Started");

        logger.warn(
                "This is a warning message");

        logger.error(
                "This is an error message");

        logger.info(
                "Application Execution Completed");
    }
}
```

---

## Explanation

### Logger Creation

```java id="00c2s5"
private static final Logger logger =
LoggerFactory.getLogger(
LoggingExample.class);
```

Creates a logger object for the class.

---

### INFO Level

```java id="4n6mca"
logger.info(
"Application Started");
```

Used to display general application information.

---

### WARN Level

```java id="3h3vzh"
logger.warn(
"This is a warning message");
```

Used to indicate potential issues.

---

### ERROR Level

```java id="0a3h31"
logger.error(
"This is an error message");
```

Used to log serious application errors.

---

## Expected Output

```text id="g9g7c9"
INFO  - Application Started

WARN  - This is a warning message

ERROR - This is an error message

INFO  - Application Execution Completed
```

---

## Logging Levels Supported by SLF4J

| Level | Purpose                        |
| ----- | ------------------------------ |
| TRACE | Detailed debugging information |
| DEBUG | Development debugging          |
| INFO  | General application events     |
| WARN  | Potential problems             |
| ERROR | Serious errors                 |

---

## Benefits of SLF4J

* Simple Logging Facade for Java
* Supports multiple logging frameworks
* Better log management
* Improves debugging and monitoring
* Easy integration with Spring Boot applications

---

## Result

Successfully implemented logging using SLF4J and demonstrated INFO, WARN, and ERROR logging levels using Logback.
