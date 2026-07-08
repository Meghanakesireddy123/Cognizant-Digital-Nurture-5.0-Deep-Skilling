# Hands-On 1: Account Microservice

## Objective

The objective of this hands-on exercise is to develop an independent Account Microservice using Spring Boot. The microservice exposes a REST API that returns dummy account information based on the account number supplied in the request URL.

---

# Scenario

A banking application is being migrated from a monolithic architecture to a Microservices Architecture.

Instead of handling all banking operations within a single application, the Account functionality is separated into an independent Spring Boot Microservice.

This service is responsible only for Account-related operations.

---

# What is a Microservice?

A Microservice is a small, independent application responsible for a single business functionality.

Characteristics include:

- Independent Deployment
- Independent Database (optional)
- REST Communication
- Loose Coupling
- High Scalability
- Easier Maintenance

---

# Software Requirements

- Java 8+
- Eclipse IDE
- Apache Maven
- Spring Boot
- Spring Web
- Spring Boot DevTools

---

# Project Configuration

| Property | Value |
|----------|-------|
| Group Id | com.cognizant |
| Artifact Id | account |
| Packaging | Jar |
| Project Type | Maven |

---

# Dependencies Used

- Spring Boot DevTools
- Spring Web

---

# Project Structure

```text
account
│
├── src
│   ├── main
│   │      ├── java
│   │      └── resources
│   │
│   └── test
│
├── pom.xml
│
└── AccountApplication.java
```

---

# Account.java

```java
package com.cognizant.account.model;

public class Account {

    private String number;
    private String type;
    private double balance;

    public Account() {
    }

    public Account(String number,
                   String type,
                   double balance) {

        this.number = number;
        this.type = type;
        this.balance = balance;
    }

    public String getNumber() {
        return number;
    }

    public String getType() {
        return type;
    }

    public double getBalance() {
        return balance;
    }
}
```

---

# AccountController.java

```java
package com.cognizant.account.controller;

import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/accounts")
public class AccountController {

    @GetMapping("/{number}")

    public Account getAccount(
            @PathVariable String number) {

        return new Account(
                number,
                "Savings",
                234343);
    }

}
```

---

# REST API Details

| Property | Value |
|----------|-------|
| Method | GET |
| Endpoint | /accounts/{number} |

Example

```
http://localhost:8080/accounts/00987987973432
```

---

# Sample JSON Response

```json
{
  "number":"00987987973432",
  "type":"Savings",
  "balance":234343
}
```

---

# Expected Output

```json
{
  "number":"00987987973432",
  "type":"Savings",
  "balance":234343
}
```

---

# Explanation

## @RestController

Marks the class as a REST Controller.

## @RequestMapping

Maps all requests beginning with /accounts.

## @GetMapping

Maps HTTP GET requests.

## @PathVariable

Reads the account number directly from the URL.

---

# Learning Outcome

- Created first Microservice.
- Built Maven project.
- Developed REST API.
- Returned JSON Response.
- Understood Spring Boot Microservice Architecture.

---

# Result

Successfully created an Account Microservice capable of returning account details as a JSON response.
