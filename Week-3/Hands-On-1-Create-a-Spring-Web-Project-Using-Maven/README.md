# Hands-On 1: Create a Spring Web Project using Maven

## Objective

The objective of this hands-on exercise is to create a Spring Boot Web project using Maven, import the project into Eclipse IDE, build it successfully using Maven, and execute the Spring Boot application while verifying the application startup through logging.

---

## Software Requirements

- Java 8 or above
- Eclipse IDE for Enterprise Java Developers
- Apache Maven
- Spring Boot
- Internet Connection

---

## Project Details

| Property | Value |
|----------|-------|
| Group Id | com.cognizant |
| Artifact Id | spring-learn |
| Project Type | Maven |
| Packaging | Jar |
| Language | Java |
| Java Version | 8 |

---

## Dependencies Used

The following dependencies were selected while creating the project:

- Spring Boot DevTools
- Spring Web

---

## Step 1: Create Spring Boot Project

Project created using **Spring Initializr**.

Configuration:

- Group Id : com.cognizant
- Artifact Id : spring-learn
- Dependencies:
  - Spring Boot DevTools
  - Spring Web

---

## Step 2: Build the Project

Execute the following Maven command:

```bash
mvn clean package -Dhttp.proxyHost=proxy.cognizant.com -Dhttp.proxyPort=6050 -Dhttps.proxyHost=proxy.cognizant.com -Dhttps.proxyPort=6050 -Dhttp.proxyUser=123456
```

This command downloads all required dependencies, compiles the source code, executes tests, and packages the application.

---

## Step 3: Project Structure

```text
spring-learn
│
├── src
│   ├── main
│   │   ├── java
│   │   └── resources
│   │
│   └── test
│       └── java
│
├── pom.xml
│
└── SpringLearnApplication.java
```

---

## Step 4: SpringLearnApplication.java

```java
package com.cognizant.springlearn;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class SpringLearnApplication {

    private static final Logger LOGGER =
            LoggerFactory.getLogger(SpringLearnApplication.class);

    public static void main(String[] args) {

        SpringApplication.run(
                SpringLearnApplication.class,
                args);

        LOGGER.info("Inside main()");
    }
}
```

---

## Project Components

### src/main/java

Contains the application's Java source code including controllers, services, repositories, models, and the main application class.

### src/main/resources

Contains configuration files such as:

- application.properties
- static resources
- templates

### src/test/java

Contains JUnit test classes for unit and integration testing.

### pom.xml

The pom.xml file is responsible for:

- Managing project dependencies
- Configuring Maven plugins
- Defining project information
- Managing the build lifecycle

---

## Important Dependencies

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>

<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
</dependency>
```

---

## Purpose of @SpringBootApplication

The @SpringBootApplication annotation combines the following annotations:

- @Configuration
- @EnableAutoConfiguration
- @ComponentScan

It automatically configures the Spring Boot application and scans for components.

---

## Dependency Hierarchy

```text
spring-boot-starter-web
│
├── Spring MVC
├── Spring Core
├── Spring Beans
├── Spring Context
├── Jackson
├── Embedded Tomcat
└── Logging Libraries
```

---

## Expected Output

```text
:: Spring Boot ::

Tomcat started on port(s): 8080 (http)

Started SpringLearnApplication

INFO  Inside main()
```

---

## Learning Outcome

- Created a Spring Boot Web project using Spring Initializr.
- Built the project successfully using Maven.
- Imported the project into Eclipse IDE.
- Understood the purpose of project folders and pom.xml.
- Learned the role of the @SpringBootApplication annotation.
- Verified successful application startup using SLF4J logging.

---

## Result

Successfully created, configured, built, and executed a Spring Boot Web project using Maven. The application started successfully, and the execution of the main() method was verified through logging.
