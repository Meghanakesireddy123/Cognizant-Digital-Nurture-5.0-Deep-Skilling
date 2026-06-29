# Hands-On 8: Create Authentication Service That Returns JWT

## Objective

The objective of this hands-on exercise is to implement an authentication service using Spring Boot that validates user credentials and generates a JSON Web Token (JWT). This token is returned to the client and is used for authenticating future requests.

---

# Scenario

In a JWT-based authentication system, the client first sends the username and password to the authentication service. After validating the credentials, the server generates a JWT token and returns it to the client. The client then includes this token in the Authorization header for all subsequent requests.

---

# REST API Details

| Property       | Value                    |
| -------------- | ------------------------ |
| HTTP Method    | GET                      |
| URL            | /authenticate            |
| Controller     | AuthenticationController |
| Port           | 8090                     |
| Authentication | Basic Authentication     |

---

# Sample Request

```bash
curl -s -u user:pwd http://localhost:8090/authenticate
```

---

# Sample Response

```json
{
  "token":"eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VyIiwiaWF0IjoxNTcwMzc5NDc0LCJleHAiOjE1NzAzODA2NzR9.t3LRvlCV-hwKfoqZYlaVQqEUiBloWcWn0ft3tgv0dL0"
}
```

---

# Step 1: Create AuthenticationController.java

```java
package com.cognizant.jwt.controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class AuthenticationController {

    @GetMapping("/authenticate")
    public AuthenticationResponse authenticate() {

        String token = JwtUtil.generateToken("user");

        return new AuthenticationResponse(token);
    }
}
```

---

# Step 2: Create AuthenticationResponse.java

```java
package com.cognizant.jwt.model;

public class AuthenticationResponse {

    private String token;

    public AuthenticationResponse() {
    }

    public AuthenticationResponse(String token) {
        this.token = token;
    }

    public String getToken() {
        return token;
    }

    public void setToken(String token) {
        this.token = token;
    }
}
```

---

# Step 3: Configure Security

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http)
            throws Exception {

        http
            .csrf().disable()
            .authorizeRequests()
            .anyRequest().authenticated()
            .and()
            .httpBasic();
    }
}
```

---

# Step 4: Read Authorization Header

```java
String authorizationHeader =
request.getHeader("Authorization");
```

The Authorization header contains the Base64 encoded username and password sent by the client.

Example:

```
Authorization: Basic dXNlcjpwd2Q=
```

---

# Step 5: Decode Username and Password

```java
String encodedCredentials =
authorizationHeader.substring("Basic ".length());

byte[] decodedBytes =
Base64.getDecoder().decode(encodedCredentials);

String credentials =
new String(decodedBytes);

String[] values =
credentials.split(":");

String username = values[0];
String password = values[1];
```

---

# Step 6: Generate JWT Token

```java
String token =
JwtUtil.generateToken(username);
```

The generated JWT contains:

* Username
* Issued Time
* Expiry Time
* Digital Signature

---

# Authentication Flow

```text
Client
   │
   │ Username + Password
   ▼
Authentication Controller
   │
   ▼
Decode Credentials
   │
   ▼
Validate User
   │
   ▼
Generate JWT Token
   │
   ▼
Return Token to Client
```

---

# Explanation

## Authentication Controller

Handles incoming authentication requests and returns the generated JWT token.

---

## Authorization Header

Carries the user's credentials encoded using Base64.

---

## Basic Authentication

The username and password are sent using HTTP Basic Authentication.

Example:

```
user:pwd
```

---

## JWT (JSON Web Token)

JWT is a compact and secure token used for authenticating users in REST APIs without maintaining server-side sessions.

---

# Expected Output

```json
{
  "token":"eyJhbGciOiJIUzI1NiJ9.xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
}
```

---

# Executed Output

```text
Request

GET http://localhost:8090/authenticate

Authorization:
Basic user:pwd

Response

{
   "token":"eyJhbGciOiJIUzI1NiJ9.xxxxxxxxxxxxxxxxx"
}
```

---

# SME Questions and Answers

## 1. What is JWT?

JWT (JSON Web Token) is a secure token used to authenticate users in stateless web applications. It contains user information, issue time, expiry time, and a digital signature.

---

## 2. Why is Basic Authentication used?

Basic Authentication securely sends the username and password to the authentication service so that the server can verify the user before generating a JWT.

---

## 3. What happens when `/authenticate` is called?

* The client sends username and password.
* Spring Security authenticates the request.
* The Authorization header is decoded.
* Username is extracted.
* A JWT token is generated.
* The token is returned as a JSON response.

---

## 4. Why do we return a JWT instead of the password?

A JWT allows the client to authenticate future requests without repeatedly sending the username and password, improving both security and performance.

---

# Learning Outcome

* Implemented JWT-based authentication.
* Configured Spring Security.
* Used HTTP Basic Authentication.
* Read and decoded the Authorization header.
* Generated JWT tokens.
* Returned authentication responses in JSON format.

---

# Result

Successfully implemented an authentication service that accepts user credentials using Basic Authentication, generates a JWT token after successful authentication, and returns the token as a JSON response. This forms the first step in implementing JWT-based security for RESTful web services.
