# Exercise 4: Arrange-Act-Assert (AAA) Pattern, Test Fixtures, Setup and Teardown Methods

## Objective

To organize JUnit test cases using the AAA pattern and utilize setup and teardown methods.

---

## AAA Pattern

### Arrange

Prepare test data and required objects.

### Act

Execute the functionality being tested.

### Assert

Verify the expected result.

---

## Example Test Class

```java
import static org.junit.Assert.*;

import org.junit.After;
import org.junit.Before;
import org.junit.Test;

public class CalculatorTest {

    private int number1;
    private int number2;

    @Before
    public void setUp() {

        number1 = 10;
        number2 = 20;

        System.out.println(
                "Setup Executed");
    }

    @Test
    public void testAddition() {

        // Arrange
        int expected = 30;

        // Act
        int actual =
                number1 + number2;

        // Assert
        assertEquals(
                expected,
                actual);
    }

    @After
    public void tearDown() {

        System.out.println(
                "Teardown Executed");
    }
}
```

---

## Explanation

### @Before

Executed before every test method.

Used for initialization.

### @Test

Contains actual test logic.

### @After

Executed after every test method.

Used for cleanup activities.

---

## Expected Output

```text
Setup Executed

Test Passed Successfully

Teardown Executed
```

---

## Result

Successfully implemented AAA pattern, setup methods, and teardown methods using JUnit.
