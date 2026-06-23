# Exercise 3: Assertions in JUnit

## Objective

To verify test results using various JUnit assertion methods.

---

## AssertionsTest.java

```java
import static org.junit.Assert.*;

import org.junit.Test;

public class AssertionsTest {

    @Test
    public void testAssertions() {

        assertEquals(5, 2 + 3);

        assertTrue(5 > 3);

        assertFalse(5 < 3);

        assertNull(null);

        assertNotNull(new Object());
    }
}
```

---

## Assertions Used

### assertEquals()

Checks whether expected and actual values are equal.

```java
assertEquals(5, 2 + 3);
```

### assertTrue()

Checks whether condition is true.

```java
assertTrue(5 > 3);
```

### assertFalse()

Checks whether condition is false.

```java
assertFalse(5 < 3);
```

### assertNull()

Checks whether object is null.

```java
assertNull(null);
```

### assertNotNull()

Checks whether object exists.

```java
assertNotNull(new Object());
```

---

## Expected Output

```text
All test cases passed successfully.
```

---

## Result

Successfully validated application behavior using JUnit assertions.
