# Hands-on 1: Spring Web Project using Maven

## Project Overview

This is a Spring Boot Web Application created using Spring Initializr and Maven.

**Project Details:**
- **Group ID:** com.cognizant
- **Artifact ID:** spring-learn
- **Version:** 0.0.1-SNAPSHOT
- **Spring Boot Version:** 3.2.3
- **Java Version:** 17

---

## Project Structure

```
spring-learn/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/cognizant/
│   │   │       └── SpringLearnApplication.java
│   │   └── resources/
│   │       └── application.properties
│   └── test/
│       └── java/
│           └── com/cognizant/
│               └── SpringLearnApplicationTests.java
├── target/                          (Generated after build)
├── pom.xml
├── mvnw                            (Maven Wrapper for Unix/Linux)
├── mvnw.cmd                        (Maven Wrapper for Windows)
├── .gitignore
└── README.md
```

---

## Folder Descriptions

### **src/main/java**
- **Purpose:** Contains all application source code
- **Package Structure:** `com.cognizant` (based on Group ID)
- **Contents:** Java classes for business logic, controllers, services, etc.

**Example:**
```java
src/main/java/com/cognizant/SpringLearnApplication.java
```

---

### **src/main/resources**
- **Purpose:** Contains application configuration files and static resources
- **Contents:**
  - `application.properties` - Application configuration
  - `static/` folder - Static files (HTML, CSS, JavaScript, images)
  - `templates/` folder - Thymeleaf templates (for web pages)

**Key Configuration in application.properties:**
```properties
server.port=8080
spring.application.name=spring-learn
logging.level.root=INFO
```

---

### **src/test/java**
- **Purpose:** Contains all test code (Unit tests, Integration tests)
- **Package Structure:** Mirrors the main package structure
- **Testing Frameworks:** JUnit 5, Spring Boot Test, Mockito (when needed)

**Example:**
```java
src/test/java/com/cognizant/SpringLearnApplicationTests.java
```

---

## Understanding SpringLearnApplication.java

### **Main Class Breakdown:**

```java
package com.cognizant;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class SpringLearnApplication {

    public static void main(String[] args) {
        System.out.println("========== Spring Learn Application Starting ==========");
        System.out.println("[INFO] Initializing Spring Boot Application Context...");
        System.out.println("[INFO] Loading Configuration from application.properties...");
        
        SpringApplication.run(SpringLearnApplication.class, args);
        
        System.out.println("========== Spring Learn Application Started Successfully ==========");
        System.out.println("[INFO] Application is ready to serve requests on port 8080");
        System.out.println("[INFO] Access the application at: http://localhost:8080");
    }
}
```

### **Key Components:**

#### **1. Package Declaration**
```java
package com.cognizant;
```
- Declares the package name based on the Group ID
- Follows Java naming conventions

#### **2. Imports**
```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
```
- `SpringApplication` - Handles Spring Boot application startup
- `@SpringBootApplication` - Meta-annotation for application setup

#### **3. @SpringBootApplication Annotation**
```java
@SpringBootApplication
public class SpringLearnApplication {
```

**What it does:**
- Combines three annotations into one:
  - `@Configuration` - Marks class as a configuration source
  - `@EnableAutoConfiguration` - Auto-configures Spring based on classpath
  - `@ComponentScan` - Scans for Spring components (@Component, @Service, @Controller, @Repository)

**Benefits:**
- Reduces boilerplate code
- Enables Spring Boot auto-configuration
- Automatically detects and registers beans
- Configures embedded Tomcat server

#### **4. Main Method**
```java
public static void main(String[] args) {
    System.out.println("========== Spring Learn Application Starting ==========");
    System.out.println("[INFO] Initializing Spring Boot Application Context...");
    System.out.println("[INFO] Loading Configuration from application.properties...");
    
    SpringApplication.run(SpringLearnApplication.class, args);
    
    System.out.println("========== Spring Learn Application Started Successfully ==========");
    System.out.println("[INFO] Application is ready to serve requests on port 8080");
    System.out.println("[INFO] Access the application at: http://localhost:8080");
}
```

**Execution Flow:**
1. **Print startup message** - Logs that application is starting
2. **System.out.println() calls** - Display informational messages
3. **SpringApplication.run()** - Bootstraps the Spring application:
   - Creates ApplicationContext
   - Scans for components
   - Loads configuration
   - Starts embedded Tomcat server
4. **Print success message** - Indicates application started successfully

**Output when running:**
```
========== Spring Learn Application Starting ==========
[INFO] Initializing Spring Boot Application Context...
[INFO] Loading Configuration from application.properties...

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::                (v3.2.3)

2024-07-08 14:23:45.123  INFO 1234 --- [           main] c.c.SpringLearnApplication              : Starting SpringLearnApplication
2024-07-08 14:23:46.456  INFO 1234 --- [           main] c.c.SpringLearnApplication              : No active profile set, falling back to 1 default profile: "default"
2024-07-08 14:23:47.789  INFO 1234 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port(s): 8080 (http)
2024-07-08 14:23:48.901  INFO 1234 --- [           main] o.apache.catalina.core.StandardEngine   : Starting Servlet engine: [Apache Tomcat/10.1.x]
2024-07-08 14:23:49.234  INFO 1234 --- [           main] c.c.SpringLearnApplication              : Started SpringLearnApplication in 3.567 seconds

========== Spring Learn Application Started Successfully ==========
[INFO] Application is ready to serve requests on port 8080
[INFO] Access the application at: http://localhost:8080
```

---

## Understanding pom.xml

### **What is pom.xml?**
- **POM = Project Object Model**
- **Purpose:** Maven configuration file for:
  - Project metadata
  - Dependency management
  - Build configuration
  - Plugin management
- **Format:** XML

### **Complete pom.xml Breakdown:**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
         https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
```

**XML Declaration:**
- `<?xml version="1.0" encoding="UTF-8"?>` - XML version and encoding
- `xmlns` - XML namespace for Maven
- `modelVersion` - POM model version (always 4.0.0 for Maven 2+)

---

### **1. Parent POM**

```xml
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>3.2.3</version>
    <relativePath/> <!-- lookup parent from repository -->
</parent>
```

**Purpose:**
- Inherits configurations from Spring Boot parent POM
- Provides default dependency versions
- Configures Maven plugins
- Sets Java version, encoding, etc.

**Benefits:**
- No need to specify versions for Spring Boot dependencies
- Consistent configurations across Spring projects
- Auto-manages plugin versions

---

### **2. Project Metadata**

```xml
<groupId>com.cognizant</groupId>
<artifactId>spring-learn</artifactId>
<version>0.0.1-SNAPSHOT</version>
<name>spring-learn</name>
<description>Spring Boot Web Application - Hands-on 1</description>
```

**Explanation:**

| Tag | Purpose | Value |
|-----|---------|-------|
| `<groupId>` | Organization identifier | com.cognizant |
| `<artifactId>` | Project name | spring-learn |
| `<version>` | Project version | 0.0.1-SNAPSHOT |
| `<name>` | Project display name | spring-learn |
| `<description>` | Project description | Spring Boot Web Application |

**Maven Coordinates:**
- These three form the **Maven coordinates**: `com.cognizant:spring-learn:0.0.1-SNAPSHOT`
- Used to identify and reference the project

**SNAPSHOT Version:**
- `SNAPSHOT` indicates development version
- Not a stable release
- Changes frequently during development
- Production releases remove SNAPSHOT

---

### **3. Properties**

```xml
<properties>
    <java.version>17</java.version>
</properties>
```

**Purpose:**
- Defines variables used throughout pom.xml
- Syntax: `${property-name}`
- `java.version` - Specifies Java version for compilation

**Usage:**
- Can be referenced in other sections
- Example: `<source>${java.version}</source>`

---

### **4. Dependencies**

```xml
<dependencies>
    <!-- Spring Boot Web Starter -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    
    <!-- Spring Boot DevTools -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-devtools</artifactId>
        <scope>runtime</scope>
        <optional>true</optional>
    </dependency>
    
    <!-- Spring Boot Test Starter -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>
</dependencies>
```

**Dependency Details:**

#### **Spring Boot Web Starter**
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

**Includes:**
- Spring Web MVC framework
- Apache Tomcat embedded server
- Jackson JSON processor
- Validation (Hibernate Validator)
- Logging (SLF4J, Logback)

**Purpose:**
- Foundation for building web applications
- Contains all necessary Spring Web dependencies

#### **Spring Boot DevTools**
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
    <scope>runtime</scope>
    <optional>true</optional>
</dependency>
```

**Attributes:**
- `<scope>runtime</scope>` - Only available at runtime, not compiled into JAR
- `<optional>true</optional>` - Not passed to dependent projects

**Features:**
- Hot reload - Restarts application on file changes
- Live reload - Refreshes browser automatically
- Fast startup - Only restarts changed components

#### **Spring Boot Test Starter**
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
</dependency>
```

**Includes:**
- JUnit 5 framework
- Spring Test
- AssertJ
- Mockito
- JSONPath

**Scope:**
- `<scope>test</scope>` - Only available for testing
- Not included in production JAR

---

### **5. Build Configuration**

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
    </plugins>
</build>
```

**Spring Boot Maven Plugin:**

**Purpose:**
- Creates executable JAR file
- Repackages JAR with all dependencies
- Provides Maven goals for Spring Boot

**Provided Goals:**
- `spring-boot:run` - Run application directly from Maven
- `spring-boot:build-image` - Create Docker image
- `spring-boot:help` - Display plugin help

**Executable JAR:**
- Includes Tomcat server
- Includes all dependencies
- Can be run: `java -jar spring-learn-0.0.1-SNAPSHOT.jar`

---

## Dependency Hierarchy

### **Understanding Transitive Dependencies**

When you add `spring-boot-starter-web`, Maven automatically includes all its dependencies:

```
spring-learn-0.0.1-SNAPSHOT
├── spring-boot-starter-web (3.2.3)
│   ├── spring-boot-starter (3.2.3)
│   │   ├── spring-boot (3.2.3)
│   │   │   ├── spring-core (6.1.x)
│   │   │   │   └── spring-jcl (6.1.x)
│   │   │   └── spring-context (6.1.x)
│   │   ├── spring-boot-autoconfigure (3.2.3)
│   │   ├── spring-boot-starter-logging (3.2.3)
│   │   │   ├── logback-classic (1.4.x)
│   │   │   ├── slf4j-api (2.0.x)
│   │   │   └── log4j-to-slf4j (2.20.x)
│   │   ├── jakarta.annotation-api (2.1.x)
│   │   ├── snakeyaml (2.2)
│   │   └── yaml configuration support
│   ├── spring-boot-starter-tomcat (3.2.3)
│   │   ├── tomcat-embed-core (10.1.x)
│   │   ├── tomcat-embed-el (10.1.x)
│   │   └── tomcat-embed-websocket (10.1.x)
│   ├── spring-webmvc (6.1.x)
│   │   ├── spring-aop (6.1.x)
│   │   ├── spring-beans (6.1.x)
│   │   ├── spring-context (6.1.x)
│   │   └── spring-expression (6.1.x)
│   ├── spring-web (6.1.x)
│   │   ├── spring-beans (6.1.x)
│   │   └── spring-core (6.1.x)
│   └── jackson-databind (2.15.x)
│       ├── jackson-core (2.15.x)
│       └── jackson-annotations (2.15.x)
├── spring-boot-devtools (3.2.3)
│   ├── spring-boot (3.2.3)
│   └── spring-core (6.1.x)
└── spring-boot-starter-test (3.2.3)
    ├── spring-boot-test (3.2.3)
    ├── spring-boot-test-autoconfigure (3.2.3)
    ├── spring-test (6.1.x)
    ├── junit-jupiter (5.9.x)
    │   ├── junit-api (5.9.x)
    │   ├── junit-engine (5.9.x)
    │   └── junit-params (5.9.x)
    ├── mockito-core (5.2.x)
    ├── mockito-junit-jupiter (5.2.x)
    ├── assertj-core (3.24.x)
    ├── hamcrest (2.2.x)
    ├── jsonpath (2.8.x)
    └── xmlunit-core (2.8.x)
```

### **How to View Dependency Hierarchy in Eclipse**

1. **Right-click on pom.xml** in Project Explorer
2. Select: **Open With** → **Maven POM Editor**
3. At the bottom of the editor, click: **Dependency Hierarchy** tab
4. Expand nodes to see all transitive dependencies
5. Look for **Conflicts** tab to see dependency version conflicts

---

## Building the Project

### **Using Maven Command Line**

```bash
# Navigate to project directory
cd path/to/spring-learn

# Build the project
mvn clean package -Dhttp.proxyHost=proxy.cognizant.com -Dhttp.proxyPort=6050 -Dhttps.proxyHost=proxy.cognizant.com -Dhttps.proxyPort=6050 -Dhttp.proxyUser=123456
```

**Command Breakdown:**
- `mvn clean` - Removes target directory (previous builds)
- `mvn package` - Compiles code and creates JAR file
- `-D` flag - Defines Maven properties
- Proxy settings - For corporate network access

**Output:**
```
[INFO] Building jar: /path/to/spring-learn/target/spring-learn-0.0.1-SNAPSHOT.jar
[INFO] BUILD SUCCESS
```

---

## Running the Application

### **Method 1: From Eclipse**

1. Right-click: `SpringLearnApplication.java`
2. Select: **Run As** → **Java Application**
3. Application starts and logs appear in console

### **Method 2: Using Maven**

```bash
mvn spring-boot:run
```

### **Method 3: Using JAR File**

```bash
java -jar target/spring-learn-0.0.1-SNAPSHOT.jar
```

---

## Key Takeaways

✅ **Spring Boot simplifies Spring application setup**
✅ **@SpringBootApplication enables auto-configuration**
✅ **pom.xml manages dependencies and build configuration**
✅ **Maven handles compilation, testing, and packaging**
✅ **Embedded Tomcat requires no separate server installation**
✅ **Spring Boot DevTools enables hot reload for fast development**

---

## Next Steps

1. ✅ Understand project structure
2. ✅ Learn about Spring Boot application class
3. ✅ Review pom.xml configuration
4. ✅ Run the application successfully
5. ⏭️ Create REST Controllers (Hands-on 2)
6. ⏭️ Add business logic and services
7. ⏭️ Work with databases and JPA

---

**Congratulations! You now understand the complete Spring Boot project structure!** 🎉
