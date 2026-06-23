# Exercise 2: Implementing the Factory Method Pattern

## Objective

To create different document types using the Factory Method Design Pattern.

---

## Project Name

FactoryMethodPatternExample

---

## Document.java

```java
package com.factory;

public interface Document {

    void open();
}
```

---

## WordDocument.java

```java
package com.factory;

public class WordDocument implements Document {

    @Override
    public void open() {

        System.out.println(
                "Opening Word Document");
    }
}
```

---

## PdfDocument.java

```java
package com.factory;

public class PdfDocument implements Document {

    @Override
    public void open() {

        System.out.println(
                "Opening PDF Document");
    }
}
```

---

## ExcelDocument.java

```java
package com.factory;

public class ExcelDocument implements Document {

    @Override
    public void open() {

        System.out.println(
                "Opening Excel Document");
    }
}
```

---

## DocumentFactory.java

```java
package com.factory;

public abstract class DocumentFactory {

    public abstract Document createDocument();

    public void openDocument() {

        Document document =
                createDocument();

        document.open();
    }
}
```

---

## WordFactory.java

```java
package com.factory;

public class WordFactory
        extends DocumentFactory {

    @Override
    public Document createDocument() {

        return new WordDocument();
    }
}
```

---

## PdfFactory.java

```java
package com.factory;

public class PdfFactory
        extends DocumentFactory {

    @Override
    public Document createDocument() {

        return new PdfDocument();
    }
}
```

---

## ExcelFactory.java

```java
package com.factory;

public class ExcelFactory
        extends DocumentFactory {

    @Override
    public Document createDocument() {

        return new ExcelDocument();
    }
}
```

---

## FactoryTest.java

```java
package com.factory;

public class FactoryTest {

    public static void main(String[] args) {

        DocumentFactory wordFactory =
                new WordFactory();

        DocumentFactory pdfFactory =
                new PdfFactory();

        DocumentFactory excelFactory =
                new ExcelFactory();

        wordFactory.openDocument();

        pdfFactory.openDocument();

        excelFactory.openDocument();
    }
}
```

---

## Explanation

1. Document interface acts as a common type.
2. WordDocument, PdfDocument and ExcelDocument implement Document.
3. DocumentFactory defines the Factory Method.
4. Concrete factories create specific document objects.
5. Client code uses factories instead of directly creating objects.

---

## Expected Output

```text
Opening Word Document

Opening PDF Document

Opening Excel Document
```

---

## Result

Successfully implemented Factory Method Design Pattern to create multiple document types while maintaining loose coupling and scalability.
