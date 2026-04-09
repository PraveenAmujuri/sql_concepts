# SQL Concepts and Execution

This repository contains my understanding of SQL concepts along with example queries and their execution results.

---

## SQL Commands Used

### 1. CREATE TABLE

```sql
CREATE TABLE users_demo (
    id INT AUTO_INCREMENT PRIMARY KEY,
    userId VARCHAR(255) UNIQUE,
    password VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    last_login TIMESTAMP NULL
);
```

### Output

![Table Structure](images/table_structure.png)

---

### 2. INSERT (Add User)

```sql
INSERT INTO users_demo (userId, password)
VALUES ('test@gmail.com', 'hashed_password');
```

### Output

![Insert Data](images/insert_data.png)

---

### 3. SELECT (Fetch Data)

```sql
SELECT * FROM users_demo;
```

### Output

![Select Result](images/select_query_result.png)

---

### 4. UPDATE (Last Login)

```sql
UPDATE users_demo
SET last_login = NOW()
WHERE userId = 'test@gmail.com';
```

### Output

![Update Result](images/update_last_login.png)

---

### 5. INNER JOIN

```sql
SELECT u.userId, l.login_time
FROM users_demo u
INNER JOIN logins l
ON u.id = l.user_id;
```

### Output

![Join Result](images/join_query_result.png)

---

### 6. GROUP BY

```sql
SELECT u.userId, COUNT(l.id) AS total_logins
FROM users_demo u
INNER JOIN logins l ON u.id = l.user_id
GROUP BY u.userId;
```

### Output

![Group By Result](images/groupby_result.png)

---

### 7. HAVING

```sql
SELECT u.userId, COUNT(l.id) AS total_logins
FROM users_demo u
INNER JOIN logins l ON u.id = l.user_id
GROUP BY u.userId
HAVING COUNT(l.id) > 1;
```

### Output

![Having Result](images/having_result.png)
