# StudentManager-Java-SQL-CRUD-Application
A student record management system demonstrating core Java OOP and SQL/JDBC concepts. Includes a web-based UI prototype and a full Java console application with database persistence.



#  StudentManager — Java + SQL CRUD Application

A student record management system demonstrating core **Java OOP** and **SQL/JDBC** concepts. Includes a web-based UI prototype and a full Java console application with database persistence.



---

##  Preview

![StudentManager Screenshot](preview.png)

---

##  What I Built

A complete **CRUD** (Create, Read, Update, Delete) application for managing university student records:

- Add new students with name, program, semester, and GPA
- Search and filter students in real time
- Sort by any column (ID, name, grade, semester)
- Delete records with confirmation
- Export all data as a `.csv` file
- **Live SQL preview panel** — shows the exact query executed for each action

---

##  What I Learned

### Java
- **Object-Oriented Programming (OOP)** — designing a `Student` class with encapsulation (`private` fields, getters/setters)
- **Collections** — using `ArrayList<Student>` for in-memory data management
- **Sorting** — implementing `Comparator<Student>` for multi-column sort
- **JDBC (Java Database Connectivity)** — connecting to MariaDB, executing `PreparedStatement` queries, handling `ResultSet`
- **Exception Handling** — `try-catch` blocks for `SQLException` and input validation
- **Scanner** — reading user input from the console for a CLI interface

### SQL
- **CRUD queries** — `SELECT`, `INSERT INTO`, `UPDATE`, `DELETE`
- **Parameterized queries** with `PreparedStatement` to prevent SQL injection
- **`WHERE` clauses** with `LIKE` for search functionality
- **`ORDER BY`** for dynamic sorting
- **Schema design** — creating a normalized `students` table with appropriate data types

### Database Schema

```sql
CREATE TABLE students (
    id        INT PRIMARY KEY AUTO_INCREMENT,
    name      VARCHAR(100) NOT NULL,
    program   VARCHAR(150),
    semester  INT,
    grade     DECIMAL(3, 1),
    email     VARCHAR(150),
    status    VARCHAR(20) DEFAULT 'Active',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

##  Tech Stack

| Technology | Purpose |
|---|---|
| Java 17 | Core application logic |
| JDBC | Database connectivity |
| MariaDB / MySQL | Data persistence |
| HTML + CSS + JS | Web UI prototype |
| GitHub Pages | Demo hosting |

---

##  Project Structure

```
student-manager/
├── src/
│   ├── Main.java               # Entry point — CLI menu loop
│   ├── Student.java            # Model class (OOP)
│   ├── StudentManager.java     # Business logic (add, delete, search, sort)
│   └── DatabaseConnection.java # JDBC connection handler
├── sql/
│   └── schema.sql              # Database setup script
├── index.html                  # Web UI prototype
├── README.md                   # This file
└── preview.png                 # Screenshot
```

---

##  How to Run (Java Console App)

### Prerequisites
- Java 17+
- MariaDB or MySQL running locally
- JDBC driver (MariaDB Connector/J)

### Setup

```bash
# 1. Clone the repository
git clone https://github.com/darisvatic/student-manager.git
cd student-manager

# 2. Create the database
mysql -u root -p < sql/schema.sql

# 3. Edit DatabaseConnection.java with your credentials
# URL: jdbc:mariadb://localhost:3306/students_db
# USER: your_username
# PASS: your_password

# 4. Compile
javac -cp .:mariadb-java-client.jar src/*.java

# 5. Run
java -cp .:mariadb-java-client.jar Main
```

### Web UI Prototype

No setup needed — just open `index.html` in a browser to explore the UI with simulated data.

---

##  Example Queries Used

```sql
-- Search students by name
SELECT * FROM students WHERE name LIKE '%Schmidt%' ORDER BY id ASC;

-- Add a new student
INSERT INTO students (name, program, semester, grade, email)
VALUES ('Daris Vatic', 'Computer Science (B.Sc.)', 2, 1.7, 'darisvatic01@gmail.com');

-- Delete a student by ID
DELETE FROM students WHERE id = 1005;

-- Export overview
SELECT id, name, grade FROM students ORDER BY grade ASC;
```

---

## Planned Features

- [ ] Spring Boot REST API backend
- [ ] Grade statistics dashboard (average, distribution)
- [ ] Course enrollment management (`enrollments` table, JOIN queries)
- [ ] User authentication with hashed passwords
- [ ] Unit tests with JUnit 5

