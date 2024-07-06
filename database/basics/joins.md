Certainly! Here's a concise note on MS SQL JOINs:

---

## MS SQL JOINs

### INNER JOIN

- Returns records with matching values in both tables.
- You can simply write `JOIN`

```sql
SELECT a.*, b.*
FROM tableA a
INNER JOIN tableB b
ON a.common_column = b.common_column;
```

### LEFT JOIN (LEFT OUTER JOIN)

- Returns all records from the left table, and matched records from the right table. Unmatched records from the right table are NULL.

```sql
SELECT a.*, b.*
FROM tableA a
LEFT JOIN tableB b
ON a.common_column = b.common_column;
```

#### Tables

**Table A: employees**

| employee_id | employee_name |
| ----------- | ------------- |
| 1           | Alice         |
| 2           | Bob           |
| 3           | Charlie       |

**Table B: departments**

| employee_id | department_name |
| ----------- | --------------- |
| 1           | HR              |
| 2           | IT              |
| 4           | Marketing       |

#### LEFT JOIN

```sql
SELECT a.employee_id, a.employee_name, b.department_name
FROM employees a
LEFT JOIN departments b
ON a.employee_id = b.employee_id;
```

### Result

| employee_id | employee_name | department_name |
| ----------- | ------------- | --------------- |
| 1           | Alice         | HR              |
| 2           | Bob           | IT              |
| 3           | Charlie       | NULL            |

### RIGHT JOIN (RIGHT OUTER JOIN)

- Returns all records from the right table, and matched records from the left table. Unmatched records from the left table are NULL.

```sql
SELECT a.*, b.*
FROM tableA a
RIGHT JOIN tableB b
ON a.common_column = b.common_column;
```

### FULL JOIN (FULL OUTER JOIN)

- Returns all records when there is a match in either left or right table. Unmatched records from both sides are NULL.

```sql
SELECT a.*, b.*
FROM tableA a
FULL JOIN tableB b
ON a.common_column = b.common_column;
```

### CROSS JOIN

- Returns the Cartesian product of both tables (all possible combinations).

```sql
SELECT a.*, b.*
FROM tableA a
CROSS JOIN tableB b;
```

### SELF JOIN

- Joins a table with itself.

```sql
SELECT a.*, b.*
FROM tableA a
INNER JOIN tableA b
ON a.common_column = b.common_column;
```

---

This note covers the basics of each type of JOIN in MS SQL.
