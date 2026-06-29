# Hands-On 1: Create a Spring Web Project using Maven

## Objective

The objective of this hands-on exercise is to create a Spring Boot Web project using Maven, import the project into Eclipse IDE, build it successfully using Maven, and execute the application while verifying the successful startup using SLF4J logging.

---

# Software Requirements

* Java 8 or above
* Eclipse IDE for Enterprise Java Developers
* Apache Maven 3.6+
* Spring Boot
* Internet Connection

---

# Project Details

| Property     | Value         |
| ------------ | ------------- |
| Group Id     | com.cognizant |
| Artifact Id  | spring-learn  |
| Project Type | Maven         |
| Language     | Java          |
| Packaging    | Jar           |
| Java Version | 8             |

---

# Dependencies Added

The following dependencies were selected while creating the project using Spring Initializr.

* Spring Boot DevTools
* Spring Web

---

# Step 1: Create Spring Boot Project

Visit:

https://start.spring.io/

Configure the project with the following values:

* **Project:** Maven
* **Language:** Java
* **Spring Boot:** Latest Stable Version
* **Group Id:** com.cognizant
* **Artifact Id:** spring-learn
* **Packaging:** Jar
* **Java Version:** 8

Select the following dependencies:

* Spring Boot DevTools
* Spring Web

Click **Generate** and download the project.

---

# Step 2: Extract and Import the Project

1. Extract the downloaded ZIP file.
2. Open Eclipse IDE.
3. Select **File → Import**.
4. Choose **Existing Maven Projects**.
5. Browse to the extracted folder.
6. Click **Finish**.

The Spring Boot project is now imported into Eclipse.

---

# Step 3: Build the Project

Execute the following Maven command:

```bash
mvn clean package -Dhttp.proxyHost=proxy.cognizant.com -Dhttp.proxyPort=6050 -Dhttps.proxyHost=proxy.cognizant.com -Dhttps.proxyPort=6050 -Dhttp.proxyUser=123456
```

This command:

* Downloads required dependencies.
* Compiles the project.
* Executes tests.
* Packages the application as a JAR file.

---

# Project Structure

```text
spring-learn
│
├── src
│   ├── main
│   │   ├── java
│   │   │      └── SpringLearnApplication.java
│   │   │
│   │   └── resources
│   │          └── application.properties
│   │
│   └── test
│          └── java
│
├── pom.xml
│
└── mvnw
```

---

# SpringLearnApplication.java

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

        SpringApplication.run(SpringLearnApplication.class, args);

        LOGGER.info("Inside main()");
    }
}
```

---

# Explanation of Project Components

## src/main/java

Contains all Java source files including:

* Controllers
* Services
* Repositories
* Models
* Main Application Class

---

## src/main/resources

Contains configuration files such as:

* application.properties
* static resources
* templates

---

## src/test/java

Contains JUnit test classes used for testing the application.

---

## pom.xml

The pom.xml file contains:

* Project information
* Spring Boot dependencies
* Maven plugins
* Build configuration

---

# Purpose of @SpringBootApplication

`@SpringBootApplication` is a combination of three annotations:

* `@Configuration`
* `@EnableAutoConfiguration`
* `@ComponentScan`

It automatically configures the Spring Boot application, scans Spring components, and enables auto-configuration.

---

# Important Dependencies

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

# Dependency Hierarchy

```text
spring-boot-starter-web
│
├── Spring MVC
├── Spring Core
├── Spring Beans
├── Spring Context
├── Embedded Tomcat
├── Jackson
└── Logging Libraries
```

---

# Expected Output

```text
:: Spring Boot ::

Tomcat started on port(s): 8080 (http)

Started SpringLearnApplication

INFO  Inside main()
```

---

# Executed Output

```text
2026-06-29 10:30:15 INFO  Starting SpringLearnApplication

2026-06-29 10:30:18 INFO  Tomcat started on port(s): 8080 (http)

2026-06-29 10:30:18 INFO  Started SpringLearnApplication

2026-06-29 10:30:18 INFO  Inside main()
```

---

# Learning Outcome

* Created a Spring Boot Web project using Spring Initializr.
* Imported a Maven project into Eclipse IDE.
* Successfully built the project using Maven.
* Understood the purpose of the project structure.
* Learned the role of the `@SpringBootApplication` annotation.
* Explored Maven dependency hierarchy.
* Verified successful application startup using SLF4J logging.

---

# Result

Successfully created, configured, built, and executed a Spring Boot Web project using Maven. The application started successfully with the embedded Tomcat server, and the execution of the `main()` method was verified through SLF4J logging.
