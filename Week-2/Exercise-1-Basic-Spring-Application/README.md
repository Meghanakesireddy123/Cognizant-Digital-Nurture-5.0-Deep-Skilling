# Exercise 1: Configuring a Basic Spring Application

## Objective

To create a basic Spring Framework application using XML configuration and manage beans using Spring IoC Container.

## Implementation

1. Created Maven Project named LibraryManagement.
2. Added Spring Core dependency in pom.xml.
3. Created BookService class.
4. Created BookRepository class.
5. Configured beans in applicationContext.xml.
6. Loaded Spring Application Context.

## Code Snippet

```java
ApplicationContext context =
new ClassPathXmlApplicationContext("applicationContext.xml");

BookService bookService =
context.getBean("bookService", BookService.class);

bookService.displayService();
```

## Explanation

Spring IoC Container loads bean definitions from applicationContext.xml and creates objects automatically.

## Expected Output

BookService Bean Initialized Successfully

BookRepository Bean Initialized Successfully

Spring Application Context Loaded Successfully

## Result

Successfully configured a Spring application using XML-based bean configuration.

```
```
