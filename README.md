# SQL Database Exercises

A collection of solved SQL exercises focused on database manipulation, queries, and advanced database concepts. These exercises demonstrate various SQL operations including DDL, DML, joins, subqueries, and recursive queries.

## 📋 Contents

This repository contains SQL exercise solutions organized by topic:

- **cv05_ads_vyriesene_ulohy.sql** - Basic SQL operations (CREATE, INSERT, UPDATE, DELETE, SELECT)
- **cv06_ads_vyriesene_ulohy.sql** - Advanced queries with JOINs, subqueries, and recursive CTEs
- **cv09_ads_vyriesene_ulohy.sql** - Additional query exercises
- **cv10_ads_vyriesene_ulohy.sql** - Further SQL practice problems

## 🎯 Topics Covered

### Basic Operations
- Table creation and manipulation (CREATE, ALTER)
- Data insertion (INSERT)
- Data modification (UPDATE)
- Data deletion (DELETE)
- Basic queries (SELECT with WHERE conditions)

### Advanced Queries
- **JOINs**: INNER JOIN, LEFT OUTER JOIN, NATURAL JOIN
- **Subqueries**: Nested SELECT statements
- **Aggregate Functions**: Date functions, string concatenation
- **Recursive Queries**: WITH clause and Common Table Expressions (CTEs)
- **Conditional Logic**: DECODE, CASE statements
- **Date Operations**: EXTRACT, MONTHS_BETWEEN, SYSDATE

## 🗃️ Database Schema

The exercises work with the HR schema which includes:
- `employees` - Employee information
- `departments` - Department details
- `jobs` - Job titles and salary ranges
- `locations` - Office locations
- `countries` - Country information

## 🚀 Usage

### Prerequisites
- Oracle Database (or compatible SQL database)
- SQL client (SQL*Plus, SQL Developer, or similar)
- Access to HR sample schema

### Running the Scripts

1. Connect to your Oracle database:
```sql
sqlplus username/password@database
```

2. Execute a script:
```sql
@cv05_ads_vyriesene_ulohy.sql
```

Or copy and paste individual queries into your SQL client.

## 📖 Example Queries

### Creating and Populating a Table
```sql
CREATE TABLE zamestnanci AS SELECT * FROM hr.employees;
ALTER TABLE zamestnanci ADD CONSTRAINT employees_pk PRIMARY KEY (employee_id);
```

### Complex JOIN Query
```sql
SELECT first_name, last_name, job_title, department_name
FROM hr.employees
JOIN hr.departments ON hr.employees.department_id = hr.departments.department_id
JOIN hr.jobs ON hr.employees.job_id = hr.jobs.job_id;
```

### Recursive CTE
```sql
WITH empl(employee_id, first_name, last_name, manager_id) AS (
   SELECT employee_id, first_name, last_name, manager_id
   FROM HR.employees WHERE manager_id IS NULL
   UNION ALL
   SELECT child.employee_id, child.first_name, child.last_name, child.manager_id
   FROM HR.employees child JOIN empl parent ON parent.employee_id = child.manager_id
)
SELECT first_name, last_name FROM empl;
```

## 🛠️ Technologies

- **SQL** - Structured Query Language
- **Oracle Database** - Primary target database system
- **PL/SQL** - Procedural Language extensions

## 📝 Notes

- All queries are tested on Oracle Database
- Some syntax may need adjustment for other SQL databases (MySQL, PostgreSQL, etc.)
- Comments in Slovak language are preserved from original exercises

## 👤 Author

**EgoHackZero**

## 📄 License

Copyright (c) 2025 EgoHackZero. All rights reserved.

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

This is a personal learning repository. Feel free to fork and use for your own learning purposes.

## ⭐ Acknowledgments

- Exercises based on ADS (Advanced Database Systems) course materials
- HR schema provided by Oracle Database sample schemas
