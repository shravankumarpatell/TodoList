# Todo List Application

A simple, full-stack Task Management application built with **Java Spring Boot** and **Thymeleaf**. This application allows users to create, manage, and track the completion status of their daily tasks.

## 🚀 Features

* **View Tasks:** Display a list of all current tasks.
* **Add Task:** Create new tasks instantly.
* **Toggle Status:** Mark tasks as "Completed" or "Pending" with a single click.
* **Delete Task:** Remove unwanted tasks from the list.
* **Persistent Storage:** All data is stored securely in a MySQL database.

## 🛠️ Tech Stack

* **Backend:** Java 23, Spring Boot 3.3.5
* **Frontend:** Thymeleaf (Server-side templating), HTML, CSS
* **Database:** MySQL
* **ORM:** Spring Data JPA (Hibernate)
* **Build Tool:** Maven

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
1.  **Java JDK 23** (or JDK 17/21 if you downgrade the `pom.xml` version).
2.  **Maven** (or use the included `mvnw` wrapper).
3.  **MySQL Server** (running locally or remotely).

## ⚙️ Configuration

### 1. Database Setup
Open your MySQL terminal or workbench and create a new database:
```sql
CREATE DATABASE todo_db;
```

### 2. Application Properties
Navigate to `src/main/resources/application.properties` and update your MySQL credentials:

```properties
spring.application.name=todoapp

# Database Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/todo_db
spring.datasource.username=root
spring.datasource.password=YOUR_PASSWORD_HERE
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# Hibernate Configuration
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

## 🏃‍♂️ How to Run

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/shravankumarpatell/TodoList.git
    cd todo-list-app
    ```

2.  **Build the Project:**
    ```bash
    ./mvnw clean install
    ```

3.  **Run the Application:**
    ```bash
    ./mvnw spring-boot:run
    ```

4.  **Access the App:**
    Open your browser and visit: `http://localhost:8080`

## ⚠️ Troubleshooting

**Error: `java.lang.ExceptionInInitializerError ... TypeTag :: UNKNOWN`**
* **Cause:** This occurs if you are using Java 23 or 25 with an older version of Lombok.
* **Fix:** Open `pom.xml` and add the specific Lombok version in the properties section:
    ```xml
    <properties>
        <java.version>23</java.version>
        <lombok.version>1.18.36</lombok.version> 
    </properties>
    ```

## 📂 Project Structure

```text
src
├── main
│   ├── java
│   │   └── com.app.todoapp
│   │       ├── controller  # Handles web requests (TaskController)
│   │       ├── models      # JPA Entities (Task)
│   │       ├── repository  # Database communication (TaskRepository)
│   │       ├── services    # Business Logic (TaskService)
│   │       └── TodoappApplication.java
│   └── resources
│       ├── templates       # HTML files (tasks.html)
│       └── application.properties
└── test
```