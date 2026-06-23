# Hands-On 4: Difference Between JPA, Hibernate and Spring Data JPA

## Objective

To understand the differences between JPA, Hibernate and Spring Data JPA.

## JPA (Java Persistence API)

- JPA is a specification for Object Relational Mapping (ORM).
- It provides standard annotations such as @Entity, @Table and @Id.
- JPA itself does not provide implementation.

Example:

```java
@Entity
public class Employee {

    @Id
    private int id;
}
```

## Hibernate

- Hibernate is an ORM framework.
- Hibernate implements JPA.
- Hibernate automatically converts Java objects into database records.

Example:

```java
Session session = factory.openSession();

Transaction tx = session.beginTransaction();

session.save(employee);

tx.commit();

session.close();
```

## Spring Data JPA

- Spring Data JPA is built on top of JPA.
- Reduces boilerplate code.
- Provides automatic CRUD operations.

Example:

```java
@Repository
public interface EmployeeRepository
extends JpaRepository<Employee,Integer> {

}
```

Service Example:

```java
@Transactional
public void addEmployee(Employee employee) {
    employeeRepository.save(employee);
}
```

## Comparison Table

| Feature | JPA | Hibernate | Spring Data JPA |
|----------|----------|----------|----------|
| Type | Specification | Framework | Abstraction Layer |
| Implementation | No | Yes | No |
| CRUD Operations | Manual | Semi-Automatic | Automatic |
| Boilerplate Code | High | Medium | Low |

## Expected Output

Understanding the relationship between:

- JPA
- Hibernate
- Spring Data JPA

## Executed Output

Successfully compared JPA, Hibernate and Spring Data JPA.

JPA → Specification

Hibernate → Implementation

Spring Data JPA → Simplified abstraction layer

## Result

Successfully studied and compared JPA, Hibernate and Spring Data JPA concepts.
