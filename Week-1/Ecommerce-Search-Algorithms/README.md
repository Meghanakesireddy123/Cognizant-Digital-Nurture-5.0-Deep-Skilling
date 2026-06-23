# Exercise 3: E-commerce Platform Search Function

## Objective

To implement Linear Search and Binary Search algorithms for product searching and analyze their performance using Big O notation.

---

## Understanding Asymptotic Notation

Big O Notation is used to measure algorithm efficiency as input size increases.

### Search Complexity

| Algorithm     | Best Case | Average Case | Worst Case |
| ------------- | --------- | ------------ | ---------- |
| Linear Search | O(1)      | O(n)         | O(n)       |
| Binary Search | O(1)      | O(log n)     | O(log n)   |

---

## Product Class

```java id="kw3l4y"
class Product {

    int productId;
    String productName;
    String category;

    Product(int productId,
            String productName,
            String category) {

        this.productId = productId;
        this.productName = productName;
        this.category = category;
    }

    @Override
    public String toString() {

        return productId + " "
                + productName + " "
                + category;
    }
}
```

---

## Linear Search Implementation

```java id="g8s0tp"
public static Product linearSearch(
        Product[] products,
        int targetId) {

    for(Product product : products) {

        if(product.productId == targetId) {
            return product;
        }
    }

    return null;
}
```

---

## Binary Search Implementation

```java id="if8fwv"
public static Product binarySearch(
        Product[] products,
        int targetId) {

    int left = 0;
    int right = products.length - 1;

    while(left <= right) {

        int mid =
                left + (right - left) / 2;

        if(products[mid].productId
                == targetId) {

            return products[mid];
        }

        if(products[mid].productId
                < targetId) {

            left = mid + 1;
        } else {

            right = mid - 1;
        }
    }

    return null;
}
```

---

## Main Method

```java id="8svtq8"
public static void main(String[] args) {

    Product[] products = {

        new Product(101,
                "Laptop",
                "Electronics"),

        new Product(102,
                "Mobile",
                "Electronics"),

        new Product(103,
                "Shoes",
                "Fashion")
    };

    Product result =
            linearSearch(products,102);

    System.out.println(result);

    Product result2 =
            binarySearch(products,103);

    System.out.println(result2);
}
```

---

## Expected Output

```text id="ptqz6o"
102 Mobile Electronics

103 Shoes Fashion
```

---

## Analysis

### Linear Search

* Searches elements one by one.
* Time Complexity: O(n)

### Binary Search

* Requires sorted array.
* Divides search space into halves.
* Time Complexity: O(log n)

### Suitable Algorithm

Binary Search is more suitable for e-commerce platforms because it provides faster search performance for large product catalogs.

---

## Result

Successfully implemented and analyzed Linear Search and Binary Search algorithms for product searching.
