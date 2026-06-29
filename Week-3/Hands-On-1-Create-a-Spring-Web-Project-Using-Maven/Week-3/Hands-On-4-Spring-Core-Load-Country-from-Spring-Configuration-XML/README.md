# Hands-On 4: Spring Core – Load Country from Spring Configuration XML

## Objective

The objective of this hands-on exercise is to configure a Spring bean using an XML configuration file, load the bean into the Spring IoC Container, retrieve it using `ApplicationContext`, and display the country details. This exercise demonstrates the fundamentals of Spring Core, Dependency Injection (DI), and Inversion of Control (IoC).

---

# Software Requirements

- Java 8 or above
- Eclipse IDE
- Apache Maven
- Spring Core Libraries
- Spring Context
- SLF4J Logging

---

# Project Name

**spring-learn**

---

# Country Details

| Code | Country Name |
|------|--------------|
| US | United States |
| DE | Germany |
| IN | India |
| JP | Japan |

For this exercise, the following country has been configured:

| Code | Name |
|------|------|
| IN | India |

---

# Step 1: Create Spring XML Configuration

Create a file named **country.xml** inside **src/main/resources**.

## country.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>

<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="country"
          class="com.cognizant.springlearn.Country">

        <property name="code" value="IN"/>

        <property name="name" value="India"/>

    </bean>

</beans>
```

---

# Step 2: Create Country.java

```java
package com.cognizant.springlearn;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class Country {

    private static final Logger LOGGER =
            LoggerFactory.getLogger(Country.class);

    private String code;

    private String name;

    public Country() {

        LOGGER.debug("Inside Country Constructor.");
    }

    public String getCode() {

        LOGGER.debug("Inside getCode()");
        return code;
    }

    public void setCode(String code) {

        LOGGER.debug("Inside setCode()");
        this.code = code;
    }

    public String getName() {

        LOGGER.debug("Inside getName()");
        return name;
    }

    public void setName(String name) {

        LOGGER.debug("Inside setName()");
        this.name = name;
    }

    @Override
    public String toString() {

        return "Country [code=" + code +
                ", name=" + name + "]";
    }
}
```

---

# Step 3: SpringLearnApplication.java

```java
package com.cognizant.springlearn;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class SpringLearnApplication {

    private static final Logger LOGGER =
            LoggerFactory.getLogger(SpringLearnApplication.class);

    public static void main(String[] args) {

        displayCountry();
    }

    public static void displayCountry() {

        ApplicationContext context =
                new ClassPathXmlApplicationContext("country.xml");

        Country country =
                context.getBean("country", Country.class);

        LOGGER.debug("Country : {}", country);

    }
}
```

---

# Explanation of Spring XML Tags

## `<bean>`

Defines an object managed by the Spring IoC Container.

Example:

```xml
<bean id="country"
class="com.cognizant.springlearn.Country">
```

---

## id Attribute

Provides a unique identifier for the bean.

Example:

```xml
id="country"
```

---

## class Attribute

Specifies the fully qualified Java class name.

Example:

```xml
class="com.cognizant.springlearn.Country"
```

---

## `<property>` Tag

Injects values into bean properties.

Example:

```xml
<property name="code"
value="IN"/>
```

---

## name Attribute

Represents the Java property name.

---

## value Attribute

Represents the value assigned to the property.

---

# Understanding ApplicationContext

`ApplicationContext` is the central interface of the Spring Framework that manages the lifecycle of Spring beans.

Example:

```java
ApplicationContext context =
new ClassPathXmlApplicationContext("country.xml");
```

It loads the XML configuration file and creates all configured beans.

---

# ClassPathXmlApplicationContext

- Reads XML configuration from the classpath.
- Creates Spring beans.
- Performs Dependency Injection.
- Manages bean lifecycle automatically.

---

# What Happens When context.getBean() is Called?

When the following statement is executed:

```java
Country country =
context.getBean("country", Country.class);
```

Spring performs these actions:

1. Reads the bean definition from `country.xml`.
2. Creates an object of the `Country` class.
3. Calls the default constructor.
4. Injects property values (`code` and `name`).
5. Returns the fully initialized bean object.

---

# Expected Console Output

```text
DEBUG Inside Country Constructor.

DEBUG Inside setCode()

DEBUG Inside setName()

DEBUG Country : Country [code=IN, name=India]
```

---

# Learning Outcome

- Created a Spring XML configuration file.
- Configured Spring beans using XML.
- Understood the purpose of bean, property, id, class, name, and value attributes.
- Learned how Spring IoC Container manages object creation.
- Retrieved Spring beans using `ApplicationContext`.
- Verified bean creation using SLF4J logging.

---

# Result

Successfully implemented Spring Core XML-based bean configuration, loaded the `Country` bean using `ApplicationContext`, and displayed the configured country details. This exercise demonstrated the working of Spring IoC Container, Dependency Injection, XML configuration, and bean lifecycle management.
