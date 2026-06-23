# Exercise 4: Creating and Configuring a Maven Project

## Objective

To create a Maven project and configure Spring dependencies with Java 1.8 support.

## Complete pom.xml

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0">

    <modelVersion>4.0.0</modelVersion>

    <groupId>com.library</groupId>
    <artifactId>LibraryManagement</artifactId>
    <version>1.0</version>

    <packaging>jar</packaging>

    <dependencies>

        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>5.3.30</version>
        </dependency>

        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-aop</artifactId>
            <version>5.3.30</version>
        </dependency>

        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>5.3.30</version>
        </dependency>

    </dependencies>

    <build>

        <plugins>

            <plugin>

                <groupId>org.apache.maven.plugins</groupId>

                <artifactId>maven-compiler-plugin</artifactId>

                <version>3.11.0</version>

                <configuration>

                    <source>1.8</source>

                    <target>1.8</target>

                </configuration>

            </plugin>

        </plugins>

    </build>

</project>
```

## Maven Commands Used

```bash
mvn clean

mvn compile

mvn package

mvn install
```

## Project Structure

```text
LibraryManagement

src/main/java

src/main/resources

src/test/java

pom.xml
```

## Explanation

* Spring Context provides IoC and Dependency Injection support.
* Spring AOP provides Aspect-Oriented Programming capabilities.
* Spring WebMVC supports web application development.
* Maven Compiler Plugin compiles source code using Java 1.8.

## Expected Output

```text
[INFO] BUILD SUCCESS

[INFO] Compiling source files

[INFO] Dependencies downloaded successfully

[INFO] Project packaged successfully
```

## Result

Successfully created and configured a Maven project with Spring Context, Spring AOP, Spring WebMVC, and Java 1.8 compiler settings.
