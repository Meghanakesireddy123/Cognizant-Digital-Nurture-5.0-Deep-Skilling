# Exercise 1: Setting Up JUnit

## Objective

To configure JUnit in a Java project and create a basic test class for unit testing.

---

## Step 1: Create Java Project

Project Name:

```text
JUnitExample
```

Created a Java project using Eclipse/IntelliJ IDEA.

---

## Step 2: Add JUnit Dependency

pom.xml

```xml
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.13.2</version>
    <scope>test</scope>
</dependency>
```

---

## Step 3: Create Test Class

CalculatorTest.java

```java
import org.junit.Test;

public class CalculatorTest {

    @Test
    public void testAddition() {

        int result = 10 + 20;

        System.out.println(
                "Addition Result : "
                        + result);
    }
}
```

---

## Explanation

* @Test annotation identifies test methods.
* JUnit executes methods marked with @Test.
* Unit testing helps validate program functionality.

---

## Expected Output

```text
Addition Result : 30
```

---

## Result

Successfully configured JUnit and executed a basic unit test.
