# Hands-On 2: Loan Microservice

## Objective

The objective of this exercise is to develop an independent Loan Microservice capable of returning loan details using REST APIs.

---

# Scenario

The banking system separates Loan operations into an independent Microservice.

Unlike the Account Microservice, this service runs independently on Port **8081**.

---

# Why Port 8081?

Both Account and Loan services cannot run on Port 8080 simultaneously.

Therefore,

```
Account Service → 8080

Loan Service → 8081
```

Configuration

application.properties

```properties
server.port=8081
```

---

# Loan.java

```java
public class Loan {

    private String number;

    private String type;

    private double loan;

    private int emi;

    private int tenure;

    public Loan() {
    }

    public Loan(String number,
                String type,
                double loan,
                int emi,
                int tenure) {

        this.number = number;
        this.type = type;
        this.loan = loan;
        this.emi = emi;
        this.tenure = tenure;
    }

}
```

---

# LoanController.java

```java
@RestController

@RequestMapping("/loans")

public class LoanController {

    @GetMapping("/{number}")

    public Loan getLoan(
            @PathVariable String number) {

        return new Loan(
                number,
                "Car",
                400000,
                3258,
                18);

    }

}
```

---

# REST API Details

| Property | Value |
|----------|-------|
| Method | GET |
| Endpoint | /loans/{number} |

Example

```
http://localhost:8081/loans/H00987987972342
```

---

# Sample JSON Response

```json
{
  "number":"H00987987972342",
  "type":"Car",
  "loan":400000,
  "emi":3258,
  "tenure":18
}
```

---

# Expected Output

```json
{
  "number":"H00987987972342",
  "type":"Car",
  "loan":400000,
  "emi":3258,
  "tenure":18
}
```

---

# Understanding Port Conflict

When both services start on Port 8080:

```
APPLICATION FAILED TO START

Port 8080 is already in use.
```

Solution

```
server.port=8081
```

Now both services execute simultaneously.

---

# Running Services

| Service | Port |
|----------|------|
| Account Service | 8080 |
| Loan Service | 8081 |

---

# Learning Outcome

- Created independent Loan Microservice.
- Configured custom server port.
- Built REST APIs.
- Understood independent deployment.

---

# Result

Successfully developed a Loan Microservice running independently on Port 8081 and returning loan details in JSON format.
