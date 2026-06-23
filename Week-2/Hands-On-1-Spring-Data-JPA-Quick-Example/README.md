# Hands-On 1: Spring Data JPA Quick Example

## Objective

To develop a Spring Boot application using Spring Data JPA and Hibernate that retrieves country details from a MySQL database.

## Software Prerequisites

- MySQL Server 8.0
- MySQL Workbench 8
- Eclipse IDE
- Maven 3.6.2
- Spring Boot

## Project Configuration

Group Id: com.cognizant

Artifact Id: orm-learn

Dependencies:

- Spring Boot DevTools
- Spring Data JPA
- MySQL Driver

## Database Setup

### Create Schema

```sql
create schema ormlearn;
```

### Create Country Table

```sql
create table country(
co_code varchar(2) primary key,
co_name varchar(50)
);
```

### Insert Records

```sql
insert into country values('IN','India');
insert into country values('US','United States of America');
```

## Entity Class

```java
@Entity
@Table(name="country")
public class Country {

    @Id
    @Column(name="co_code")
    private String code;

    @Column(name="co_name")
    private String name;
}
```

## Repository Layer

```java
@Repository
public interface CountryRepository
extends JpaRepository<Country,String> {

}
```

## Service Layer

```java
@Service
public class CountryService {

    @Autowired
    private CountryRepository countryRepository;

    @Transactional
    public List<Country> getAllCountries() {
        return countryRepository.findAll();
    }
}
```

## Expected Output

Country [code=IN, name=India]

Country [code=US, name=United States of America]

## Executed Output

INFO : Inside main

countries=[
Country [code=IN, name=India],
Country [code=US, name=United States of America]
]

Hibernate: select * from country

## Result

Successfully implemented Spring Data JPA application and retrieved country records from MySQL database using Hibernate.
