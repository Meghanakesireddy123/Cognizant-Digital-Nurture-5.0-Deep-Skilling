# Exercise 1: Mocking and Stubbing using Mockito

## Objective

To test a service that depends on an external API by creating mock objects and stubbing method responses using Mockito.

---

## Prerequisites

Dependencies Required:

```xml id="0hck6e"
<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-core</artifactId>
    <version>5.11.0</version>
    <scope>test</scope>
</dependency>

<dependency>
    <groupId>org.junit.jupiter</groupId>
    <artifactId>junit-jupiter</artifactId>
    <version>5.10.2</version>
    <scope>test</scope>
</dependency>
```

---

## ExternalApi.java

```java id="9m0bl7"
public interface ExternalApi {

    String getData();
}
```

---

## MyService.java

```java id="67zmwh"
public class MyService {

    private ExternalApi externalApi;

    public MyService(
            ExternalApi externalApi) {

        this.externalApi = externalApi;
    }

    public String fetchData() {

        return externalApi.getData();
    }
}
```

---

## Test Class

MyServiceTest.java

```java id="s17sxt"
import static org.mockito.Mockito.*;
import static org.junit.jupiter.api.Assertions.*;

import org.junit.jupiter.api.Test;
import org.mockito.Mockito;

public class MyServiceTest {

    @Test
    public void testExternalApi() {

        ExternalApi mockApi =
                Mockito.mock(
                        ExternalApi.class);

        when(mockApi.getData())
                .thenReturn(
                        "Mock Data");

        MyService service =
                new MyService(mockApi);

        String result =
                service.fetchData();

        assertEquals(
                "Mock Data",
                result);
    }
}
```

---

## Explanation

### Mocking

Mockito creates a fake implementation of ExternalApi.

```java id="b8vmvs"
ExternalApi mockApi =
Mockito.mock(ExternalApi.class);
```

### Stubbing

Defines the value returned by the mocked method.

```java id="i6b79t"
when(mockApi.getData())
.thenReturn("Mock Data");
```

### Assertion

Verifies that expected and actual values match.

```java id="0k4yvg"
assertEquals(
"Mock Data",
result);
```

---

## Expected Output

```text id="2g9g3r"
Test Passed Successfully

Expected : Mock Data

Actual   : Mock Data
```

---

## Result

Successfully implemented Mockito Mocking and Stubbing to test service behavior without accessing a real external API.
