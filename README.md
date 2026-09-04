# AWS RDS MySQL – Connection & Basic Commands

## 1. Connect to RDS MySQL

From an Ubuntu/EC2 machine where MySQL client is installed:

```bash
mysql -h <RDS-ENDPOINT> -P 3306 -u <USERNAME> -p
```

Example:

```bash
mysql -h mydb.xxxxxxxxxxxx.us-east-1.rds.amazonaws.com -P 3306 -u admin -p
```

After running the command, MySQL asks for the password:

```text
Enter password:
```

> Do not put the database password directly in the command.

---

## 2. Check available databases

```sql
SHOW DATABASES;
```

Example:

```text
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| new_db             |
+--------------------+
```

---

## 3. Select the application database

```sql
USE new_db;
```

Expected:

```text
Database changed
```

---

## 4. Check current database

```sql
SELECT DATABASE();
```

Expected:

```text
+------------+
| DATABASE() |
+------------+
| new_db     |
+------------+
```

---

## 5. Show tables

```sql
SHOW TABLES;
```

---

## 6. Create a simple table

```sql
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    email VARCHAR(100)
);
```

---

## 7. Check table structure

```sql
DESCRIBE users;
```

or:

```sql
DESC users;
```

---

## 8. Insert data

```sql
INSERT INTO users (name, email)
VALUES ('Vinay', 'vinay@example.com');
```

---

## 9. Read data

```sql
SELECT * FROM users;
```

---

## 10. Exit MySQL

```sql
EXIT;
```

or:

```sql
QUIT;
```

---

# Important DevOps Understanding

For DevOps, remember this flow:

```text
EC2 / Application Server
        |
        | MySQL connection
        ↓
    RDS Endpoint
        |
        ↓
     new_db
        |
        ↓
      users
        |
        ↓
       rows
```

### Important connection information

You need:

* **RDS endpoint** → where the database is
* **Port** → normally `3306` for MySQL
* **Username**
* **Password**
* **Database name**
* **Security Group** → controls whether the application/EC2 can reach RDS

Example:

```bash
mysql -h <RDS-ENDPOINT> -P 3306 -u admin -p
```

Once connected:

```sql
SHOW DATABASES;
USE new_db;
SHOW TABLES;
SELECT * FROM users;
```

**This is enough SQL/MySQL knowledge for your current DevOps learning.**
# rds
