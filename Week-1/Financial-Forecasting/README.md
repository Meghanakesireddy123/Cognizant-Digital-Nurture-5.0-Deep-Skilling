# Exercise 7: Financial Forecasting

## Objective

To implement a recursive algorithm that predicts future values based on historical growth rates.

---

## Understanding Recursion

Recursion is a programming technique where a method calls itself until a stopping condition is reached.

Advantages:

* Simplifies repetitive calculations.
* Reduces code complexity.
* Useful for forecasting and mathematical problems.

---

## Recursive Forecast Method

```java id="pfmqji"
public static double predictFutureValue(

        double currentValue,

        double growthRate,

        int years) {

    if(years == 0) {

        return currentValue;
    }

    return predictFutureValue(

            currentValue *
                    (1 + growthRate),

            growthRate,

            years - 1);
}
```

---

## Main Method

```java id="n4v4o5"
public static void main(String[] args) {

    double currentValue = 10000;

    double growthRate = 0.10;

    int years = 5;

    double futureValue =
            predictFutureValue(

                    currentValue,

                    growthRate,

                    years);

    System.out.println(
            "Predicted Future Value: "
                    + futureValue);
}
```

---

## Expected Output

```text id="tbqghl"
Predicted Future Value: 16105.1
```

---

## Time Complexity Analysis

### Recursive Approach

```text id="bdmcbq"
T(n) = T(n-1) + O(1)
```

Time Complexity:

```text id="7i5d4s"
O(n)
```

Space Complexity:

```text id="zkznh9"
O(n)
```

due to recursive call stack.

---

## Optimization

Instead of recursion:

* Use Dynamic Programming.
* Use Iterative Approach.
* Store previously computed values.

Optimized Complexity:

```text id="52h9xu"
Time Complexity : O(n)

Space Complexity : O(1)
```

---

## Result

Successfully implemented recursive financial forecasting and analyzed optimization techniques for improving performance.
