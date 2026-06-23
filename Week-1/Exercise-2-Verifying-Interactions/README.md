# Exercise 2: Verifying Interactions using Mockito

## Objective

To verify whether a mocked method is invoked with the expected interaction using Mockito.

---

## ExternalApi.java

```java id="0sl1d2"
public interface ExternalApi {

    String getData();
}
```

---

## MyService.java

```java id="js5efr"
public class MyService {

    private ExternalApi externalApi;

    public MyService(
            ExternalApi externalApi) {

        this.externalApi = externalApi;
    }

    public void fetchData() {

        externalApi.getData();
    }
}
```

---

## Test Class

MyServiceTest.java

```java id="mr3l1k"
import static org.mockito.Mockito.*;

import org.junit.jupiter.api.Test;
import org.mockito.Mockito;

public class MyServiceTest {

    @Test
    public void testVerifyInteraction() {

        ExternalApi mockApi =
                Mockito.mock(
                        ExternalApi.class);

        MyService service =
                new MyService(mockApi);

        service.fetchData();

        verify(mockApi)
                .getData();
    }
}
```

---

## Explanation

### Create Mock Object

```java id="j3r7vc"
ExternalApi mockApi =
Mockito.mock(
ExternalApi.class);
```

### Execute Method

```java id="zj9dn4"
service.fetchData();
```

### Verify Interaction

```java id="ph4hqe"
verify(mockApi)
.getData();
```

Mockito checks whether getData() was called during execution.

---

## Expected Output

```text id="0d4u7x"
Test Passed Successfully

Verified:

getData() method invoked exactly once.
```

---

## Benefits

* Ensures expected interactions occur.
* Validates service behavior.
* Improves test reliability.
* Eliminates dependency on external systems.

---

## Result

Successfully verified method interactions using Mockito verify() functionality.
