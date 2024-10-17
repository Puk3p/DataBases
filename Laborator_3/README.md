# EXERCITIUL 1

```
MariaDB [c13_13_db]> CREATE TABLE users (
    -> ID INT PRIMARY KEY,
    -> name VARCHAR(20) NOT NULL);
```
```
MariaDB [c13_13_db]> INSERT INTO users (ID, name) VALUES (101, 'Mihai'), (102, 'Andreea'), (103, 'PaulCTNS');
```

```
MariaDB [c13_13_db]> ALTER TABLE users
    -> ADD COLUMN email VARCHAR(3) NOT NULL;
```
```
MariaDB [c13_13_db]> CREATE TABLE details (
    -> ID INT PRIMARY KEY,
    -> nickname VARCHAR(10) NOT NULL UNIQUE,
    -> details VARCHAR(30),
    -> FOREIGN KEY (ID) REFERENCES users(ID));
```
```
MariaDB [c13_13_db]> INSERT INTO details (ID, nickname, details) VALUES (101, 'Mihai', 'Detalii Mihai');

MariaDB [c13_13_db]> INSERT INTO details (ID, nickname, details) VALUES (102, 'Andreea', 'Detalii Andreea');
```

# EXERCITIUL 3

```
MariaDB [c13_13_db]> SET autocommit=0;
```
```
MariaDB [c13_13_db]> CREATE TABLE users1 (
    -> ID INT PRIMARY KEY,
    -> name VARCHAR(20) NOT NULL,
    -> email VARCHAR(30) NOT NULL ) ENGINE=InnoDB;
```
MariaDB [c13_13_db]> CREATE TABLE details1(
    -> ID INT PRIMARY KEY,
    -> nickname VARCHAR(10) NOT NULL UNIQUE,
    -> details VARCHAR(30),
    -> FOREIGN KEY (ID) REFERENCES users1(ID)) ENGINE=InnoDB;
```
```
MariaDB [c13_13_db]> INSERT INTO users1 (ID, name, email) VALUES (101, 'Mihai', 'mihai@mail.com'), (102, 'Andreea', 'andreea@gmail.com');
```
```
MariaDB [c13_13_db]> INSERT INTO details1 (ID, nickname, details1) VALUES (101,
'Mihai', 'Detalii Luigii'), (102, 'Andreea', 'Detalii Andreea');
```
```
MariaDB [c13_13_db]> START TRANSACTION;
MariaDB [c13_13_db]> UPDATE users1 SET email = 'mihai_new@mail.com' WHERE ID = 101;
```
```
MariaDB [c13_13_db]> INSERT INTO users1 (ID, name, email) VALUES (103, 'Miiiihai', 'mihaaaai@mail.com');
Query OK, 1 row affected (0.001 sec)

MariaDB [c13_13_db]> INSERT INTO details1 (ID, nickname, details1) VALUES (103, 'Miron', 'Detalii Miron');

MariaDB [c13_13_db]> SELECT * FROM users1;
+-----+----------+--------------------+
| ID  | name     | email              |
+-----+----------+--------------------+
| 101 | Mihai    | mihai_new@mail.com |
| 102 | Andreea  | andreea@gmail.com  |
| 103 | Miiiihai | mihaaaai@mail.com  |
+-----+----------+--------------------+

MariaDB [c13_13_db]> SELECT * FROM details1;
+-----+----------+-----------------+
| ID  | nickname | details1        |
+-----+----------+-----------------+
| 101 | Mihai    | Detalii Luigii  |
| 102 | Andreea  | Detalii Andreea |
| 103 | Miron    | Detalii Miron   |
+-----+----------+-----------------+
```
