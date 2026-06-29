# Hands-On 1: Create a Spring Web Project using Maven

## Objective

To create a Spring Boot Web project using Maven, import it into Eclipse, configure the project, build it successfully, and execute the Spring Boot application.

---

# Project Details

| Property     | Value         |
| ------------ | ------------- |
| Group Id     | com.cognizant |
| Artifact Id  | spring-learn  |
| Project Type | Maven         |
| Language     | Java          |
| Packaging    | Jar           |
| Java Version | 8 or above    |

---

# Dependencies Added

The following dependencies were selected while creating the project using Spring Initializr:

* Spring Boot DevTools
* Spring Web

---

# Step 1: Create Spring Boot Project

Project created using **https://start.spring.io/** with the following configuration:

* Group : com.cognizant
* Artifact : spring-learn
* Dependencies :

  * Spring Boot DevTools
  * Spring Web

---

# Step 2: Build the Project

Build Command:

```bash
mvn clean package -Dhttp.proxyHost=proxy.cognizant.com -Dhttp.proxyPort=6050 -Dhttps.proxyHost=proxy.cognizant.com -Dhttps.proxyPort=6050 -Dhttp.proxyUser=123456
```

The Maven build downloads all required dependencies and generates the executable JAR file.

---

# Step 3: Project Structure

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

# Step 4: Main Class

## SpringLearnApplication.java

```java
package com.cognizant.springlearn;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class SpringLearnApplication {

    private static final Logger LOGGER =
            LoggerFactory.getLogger(
                    SpringLearnApplication.class);

    public static void main(String[] args) {

        SpringApplication.run(
                SpringLearnApplication.class,
                args);

        LOGGER.info("Inside main()");
    }
}
```

---

# Explanation

## @SpringBootApplication

The `@SpringBootApplication` annotation is a combination of:

* `@Configuration`
* `@EnableAutoConfiguration`
* `@ComponentScan`

It enables auto configuration and starts the Spring Boot application.

---

## src/main/java

Contains all Java source files including controllers, services, repositories, and the main application class.

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

The pom.xml file manages:

* Project information
* Maven dependencies
* Plugins
* Build lifecycle
* Spring Boot starter dependencies

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

```
spring-boot-starter-web
        │
        ├── Spring MVC
        ├── Spring Core
        ├── Spring Beans
        ├── Spring Context
        ├── Jackson
        ├── Tomcat Embedded Server
        └── Logging Libraries
```

---

# Expected Output

```
:: Spring Boot ::

Tomcat started on port(s): 8080 (http)

Started SpringLearnApplication

INFO  Inside main()
```

---

# Result

Successfully created a Spring Boot Web project using Maven, imported it into Eclipse, built the project successfully, and executed the application. The Spring Boot application started successfully with embedded Tomcat, and the main() method execution was verified using SLF4J logging.
