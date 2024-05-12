Consider the CUSTOMERS table having the following records – 
 
+----+----------+-----+-----------+----------+ 
| ID | NAME     | AGE | ADDRESS   | SALARY   | 
+----+----------+-----+-----------+----------+ 
|  1 | Ramesh   |  32 | Ahmedabad |  2000.00 | 
|  2 | Khilan   |  25 | Delhi     |  1500.00 | 
|  3 | kaushik  |  23 | Kota      |  2000.00 | 
|  4 | Chaitali |  25 | Mumbai    |  6500.00 | 
|  5 | Hardik   |  27 | Bhopal    |  8500.00 | 
|  6 | Komal    |  22 | MP        |  4500.00 | 
|  7 | Muffy    |  24 | Indore    | 10000.00 | 
+----+----------+-----+-----------+----------+  
SQL> DELETE FROM CUSTOMERS  WHERE AGE = 25; 
SQL> ROLLBACK; 
SQL> select * from customers 
+----+----------+-----+-----------+----------+ 
| ID | NAME     | AGE | ADDRESS   | SALARY   | 
+----+----------+-----+-----------+----------+ 
|  1 | Ramesh   |  32 | Ahmedabad |  2000.00 | 
|  2 | Khilan   |  25 | Delhi     |  1500.00 | 
|  3 | kaushik  |  23 | Kota      |  2000.00 | 
|  4 | Chaitali |  25 | Mumbai    |  6500.00 | 
|  5 | Hardik   |  27 | Bhopal    |  8500.00 | 
|  6 | Komal    |  22 | MP        |  4500.00 | 
|  7 | Muffy    |  24 | Indore    | 10000.00 | 
+----+----------+-----+-----------+----------+ 
SQL> DELETE FROM CUSTOMERS   WHERE AGE = 25; 
SQL> COMMIT; 
SQL> select * from customers 
+----+----------+-----+-----------+----------+ 
| ID | NAME     | AGE | ADDRESS   | SALARY   | 
+----+----------+-----+-----------+----------+ 
|  1 | Ramesh   |  32 | Ahmedabad |  2000.00 | 
|  3 | kaushik  |  23 | Kota      |  2000.00 | 
|  5 | Hardik   |  27 | Bhopal    |  8500.00 | 
|  6 | Komal    |  22 | MP        |  4500.00 | 
|  7 | Muffy    |  24 | Indore    | 10000.00 | 
+----+----------+-----+-----------+----------+ 
SQL> SAVEPOINT SP1; 
Savepoint created. 
SQL> DELETE FROM CUSTOMERS WHERE ID=1; 
1 row deleted. 
SQL> SAVEPOINT SP2; 
Savepoint created. 
SQL> DELETE FROM CUSTOMERS WHERE ID=2; 
1 row deleted. 
SQL> SAVEPOINT SP3; 
Savepoint created. 
SQL> DELETE FROM CUSTOMERS WHERE ID=3; 
1 row deleted. 
SQL> ROLLBACK TO SP2; 
Rollback complete. 
SQL> SELECT * FROM CUSTOMERS; 
+----+----------+-----+-----------+----+ 
| ID | NAME     | AGE | ADDRESS   | SALARY   | 
+----+----------+-----+-----------+----------+ 
|  2 | Khilan   |  25 | Delhi     |  1500.00 | 
|  3 | kaushik  |  23 | Kota      |  2000.00 | 
|  4 | Chaitali |  25 | Mumbai    |  6500.00 | 
|  5 | Hardik   |  27 | Bhopal    |  8500.00 | 
|  6 | Komal    |  22 | MP        |  4500.00 | 
|  7 | Muffy    |  24 | Indore    | 10000.00 | 
+----+----------+-----+-----------+----------+ 6 rows selected.  
  
