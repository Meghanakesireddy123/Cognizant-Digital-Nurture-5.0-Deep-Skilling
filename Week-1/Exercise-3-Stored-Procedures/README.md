# Exercise 3: Stored Procedures

## Objective

To implement stored procedures for banking operations such as interest calculation, employee bonus processing, and fund transfer management.

---

# Scenario 1: Process Monthly Interest

## Requirement

Apply 1% interest to all savings accounts.

## Stored Procedure

```sql
CREATE OR REPLACE PROCEDURE
ProcessMonthlyInterest

IS

BEGIN

UPDATE accounts

SET balance =
    balance +
    (balance * 0.01)

WHERE account_type =
      'SAVINGS';

COMMIT;

DBMS_OUTPUT.PUT_LINE(
'Monthly interest processed');

END;
/
```

## Execute

```sql
EXEC ProcessMonthlyInterest;
```

## Expected Output

```text id="bdw7kl"
Monthly interest processed
```

---

# Scenario 2: Update Employee Bonus

## Requirement

Increase salary of employees in a department using a bonus percentage parameter.

## Stored Procedure

```sql
CREATE OR REPLACE PROCEDURE
UpdateEmployeeBonus(

department_name IN VARCHAR2,

bonus_percentage IN NUMBER)

IS

BEGIN

UPDATE employees

SET salary =
    salary +
    (salary *
    bonus_percentage / 100)

WHERE department =
      department_name;

COMMIT;

DBMS_OUTPUT.PUT_LINE(
'Employee bonus updated');

END;
/
```

## Execute

```sql
EXEC UpdateEmployeeBonus('IT',10);
```

## Expected Output

```text id="r44eh7"
Employee bonus updated
```

---

# Scenario 3: Transfer Funds

## Requirement

Transfer money between two accounts after validating sufficient balance.

## Stored Procedure

```sql
CREATE OR REPLACE PROCEDURE
TransferFunds(

source_account IN NUMBER,

target_account IN NUMBER,

transfer_amount IN NUMBER)

IS

current_balance NUMBER;

BEGIN

SELECT balance

INTO current_balance

FROM accounts

WHERE account_id =
      source_account;

IF current_balance >=
   transfer_amount THEN

UPDATE accounts

SET balance =
    balance -
    transfer_amount

WHERE account_id =
      source_account;

UPDATE accounts

SET balance =
    balance +
    transfer_amount

WHERE account_id =
      target_account;

COMMIT;

DBMS_OUTPUT.PUT_LINE(
'Fund transfer successful');

ELSE

DBMS_OUTPUT.PUT_LINE(
'Insufficient balance');

END IF;

END;
/
```

## Execute

```sql
EXEC TransferFunds(101,102,5000);
```

## Expected Output

```text id="8v41eo"
Fund transfer successful
```

---

## Result

Successfully implemented stored procedures for interest calculation, employee bonus processing, and secure fund transfers.
