# Exercise 1: Control Structures

## Objective

To use PL/SQL control structures such as loops, conditions, and cursors to perform banking operations efficiently.

---

# Scenario 1: Apply Discount to Loan Interest Rates

## Requirement

Apply a 1% discount on loan interest rates for customers above 60 years of age.

## PL/SQL Block

```sql
DECLARE

CURSOR customer_cursor IS

SELECT customer_id,
       age
FROM customers;

BEGIN

FOR customer_record IN customer_cursor LOOP

    IF customer_record.age > 60 THEN

        UPDATE loans

        SET interest_rate =
            interest_rate - 1

        WHERE customer_id =
              customer_record.customer_id;

    END IF;

END LOOP;

COMMIT;

DBMS_OUTPUT.PUT_LINE(
'Loan discount applied successfully');

END;
/
```

## Expected Output

```text id="cvtcmn"
Loan discount applied successfully
```

---

# Scenario 2: Promote Customers to VIP Status

## Requirement

Mark customers as VIP if their balance exceeds $10,000.

## PL/SQL Block

```sql
DECLARE

CURSOR vip_cursor IS

SELECT customer_id,
       balance
FROM customers;

BEGIN

FOR customer_record IN vip_cursor LOOP

    IF customer_record.balance > 10000 THEN

        UPDATE customers

        SET isvip = 'TRUE'

        WHERE customer_id =
              customer_record.customer_id;

    END IF;

END LOOP;

COMMIT;

DBMS_OUTPUT.PUT_LINE(
'VIP customers updated successfully');

END;
/
```

## Expected Output

```text id="7b8lzn"
VIP customers updated successfully
```

---

# Scenario 3: Loan Due Reminder

## Requirement

Send reminders to customers whose loans are due within the next 30 days.

## PL/SQL Block

```sql
DECLARE

CURSOR loan_cursor IS

SELECT customer_name,
       due_date

FROM loans

WHERE due_date BETWEEN
      SYSDATE
      AND
      SYSDATE + 30;

BEGIN

FOR loan_record IN loan_cursor LOOP

DBMS_OUTPUT.PUT_LINE(

'Reminder : Loan due for '
|| loan_record.customer_name
|| ' on '
|| loan_record.due_date);

END LOOP;

END;
/
```

## Expected Output

```text id="fdyv24"
Reminder : Loan due for John on 15-JUL-2026

Reminder : Loan due for Smith on 20-JUL-2026
```

---

## Result

Successfully implemented PL/SQL control structures using loops, cursors, and conditional statements for banking operations.
