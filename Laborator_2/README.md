# EXERCITIUL 1


MariaDB [c13_13_db]> SELECT *
    -> FROM employees
    -> WHERE last_name LIKE '%a%o%';

# EXERCITIUL 2

MariaDB [c13_13_db]> SELECT *
    -> FROM employees
    -> WHERE first_name LIKE '%ll%';

# EXERCITIUL 3

MariaDB [c13_13_db]> SELECT
    -> last_name,
    -> first_name,
    -> CONCAT(first_name, ' ', last_name) AS full_name,
    -> LENGTH(CONCAT(first_name, ' ', last_name)) AS name_length
    -> FROM employees;

# EXERCITIUL 4

MariaDB [c13_13_db]> SELECT
    -> last_name,
    -> salary,
    -> CASE
    -> WHEN salary < 5000 THEN 'mic'
    -> WHEN salary BETWEEN 5000 AND 7000 THEN 'mediu'
    -> ELSE 'mare rau, bastan'
    -> END
    -> AS tip_salariu
    -> FROM employees;

# EXERCITIUL 5

MariaDB [c13_13_db]> SELECT
    -> MIN(salary) AS salariu_minim,
    -> MAX(salary) AS salariu_maxim,
    -> AVG(salary) AS media_salariala
    -> FROM employees;

# EXERCITIUL 6

MariaDB [c13_13_db]> SELECT
    -> last_name,
    -> salary,
    -> salary * 1.23456 AS salariu_marit_nerotunjit,
    -> ROUND(salary * 1.23456, 2) AS salariu_marit_rotunjit
    -> FROM employees
    -> WHERE manager_id IS NOT NULL;


# EXTRA - EXERCITII
1)
  MariaDB [c13_13_db]> SELECT 
      -> d.department_name,
      -> l.city
      -> FROM
      -> departments d
      -> JOIN locations l ON d.location_id = l.location_id
      -> WHERE
      -> d.department_name LIKE '%pp%'
      -> AND SUBSTRING(l.city, 3, 1) = 'u'
      -> AND SUBSTRING(l.city, 5, 1) = 'h';

MariaDB [(none)]> SELECT
    -> first_name,
    -> last_name,
    -> LOWER(CONCAT(LEFT(first_name, 1), '.', LOWER(last_name), '@', LOWER(SUBSTRING(job_id, 1,LOCATE('_', job_id)-1)), '.tuiasi.ro')) AS email
    -> FROM
    -> employees;

