# Hands-On 4: Spring Core – Load Country from Spring Configuration XML

## Objective

The objective of this hands-on exercise is to configure a Spring bean using an XML configuration file, load the bean into the Spring IoC Container, retrieve it using `ApplicationContext`, and display the country details.

---

# Software Requirements

- Java 8 or above
- Eclipse IDE
- Apache Maven
- Spring Core
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

Configured Country:

| Code | Name |
|------|------|
| IN | India |

---

# Step 1: Create country.xml

Place the file inside:

```
src/main/resources
```

### country.xml

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

# Explanation

## Bean Tag

Defines an object managed by the Spring IoC Container.

```xml
<bean id="country"
class="com.cognizant.springlearn.Country">
```

---

## id Attribute

Provides a unique identifier for the bean.

---

## class Attribute

Specifies the Java class used for bean creation.

---

## property Tag

Injects values into bean properties.

Example:

```xml
<property name="code"
value="IN"/>
```

---

## ApplicationContext

ApplicationContext loads the Spring configuration file and manages all Spring beans.

Example:

```java
ApplicationContext context =
new ClassPathXmlApplicationContext("country.xml");
```

---

## ClassPathXmlApplicationContext

Loads XML configuration from the classpath and initializes the Spring IoC Container.

---

## What Happens When getBean() is Invoked?

When the following statement executes:

```java
Country country =
context.getBean("country", Country.class);
```

Spring performs the following steps:

1. Reads the XML configuration.
2. Creates the Country object.
3. Calls the default constructor.
4. Injects the property values.
5. Returns the fully initialized bean.

---

# Expected Output

```text
DEBUG Inside Country Constructor.

DEBUG Inside setCode()

DEBUG Inside setName()

DEBUG Country : Country [code=IN, name=India]
```

---

# Learning Outcome

- Configured Spring beans using XML.
- Loaded Spring configuration using ApplicationContext.
- Understood Spring IoC Container.
- Retrieved beans using getBean().
- Implemented Dependency Injection.
- Verified execution using SLF4J logging.

---

# Result

Successfully configured and loaded a Spring bean using XML configuration. The Country bean was created by the Spring IoC Container, property values were injected successfully, and the configured country details were displayed using Spring Framework.
