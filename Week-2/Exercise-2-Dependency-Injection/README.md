# Exercise 2: Implementing Dependency Injection

## Objective

To implement Dependency Injection between BookService and BookRepository using Spring Framework Setter Injection.

## BookRepository.java

```java
package com.library.repository;

public class BookRepository {

    public String getBookDetails() {
        return "Book Details Retrieved Successfully";
    }
}
```

## BookService.java

```java
package com.library.service;

import com.library.repository.BookRepository;

public class BookService {

    private BookRepository bookRepository;

    public void setBookRepository(BookRepository bookRepository) {
        this.bookRepository = bookRepository;
    }

    public void displayBookDetails() {

        String result =
                bookRepository.getBookDetails();

        System.out.println(
                "BookService is calling Repository");

        System.out.println(result);
    }
}
```

## applicationContext.xml

```xml
<beans xmlns="http://www.springframework.org/schema/beans">

    <bean id="bookRepository"
          class="com.library.repository.BookRepository"/>

    <bean id="bookService"
          class="com.library.service.BookService">

        <property name="bookRepository"
                  ref="bookRepository"/>

    </bean>

</beans>
```

## MainApp.java

```java
package com.library;

import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

import com.library.service.BookService;

public class MainApp {

    public static void main(String[] args) {

        ApplicationContext context =
                new ClassPathXmlApplicationContext(
                        "applicationContext.xml");

        BookService service =
                context.getBean(
                        "bookService",
                        BookService.class);

        service.displayBookDetails();
    }
}
```

## Explanation

The BookRepository bean is injected into BookService using Setter Injection. Spring IoC Container manages bean creation and dependency wiring automatically.

## Expected Output

```text
BookService is calling Repository

Book Details Retrieved Successfully
```

## Result

Successfully implemented Dependency Injection using Spring Setter Injection and verified communication between Service and Repository layers.
