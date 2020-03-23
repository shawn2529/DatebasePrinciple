Microsoft Windows [版本 10.0.18363.720]  
(c) 2019 Microsoft Corporation。保留所有权利。  
  
C:\Users\Xiaotong>mysql -uroot -p  
Enter password: **********  
Welcome to the MariaDB monitor.  Commands end with ; or \g.  
Your MariaDB connection id is 84  
Server version: 10.5.1-MariaDB mariadb.org binary distribution  
  
Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.  
  
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.  
  
MariaDB [(none)]> use create;  
Database changed  
MariaDB [create]> show tables;  
+------------------+  
| Tables_in_create |  
+------------------+  
| customers        |  
| orderitems       |  
| orders           |  
| productnotes     |  
| products         |  
| vendors          |  
+------------------+  
6 rows in set (0.001 sec)  
  
MariaDB [create]> select * from customers where cust_name in ("Wascals","E fudd");  
+---------+-----------+------------------+-----------+------------+----------+--------------+--------------+---------------------+  
| cust_id | cust_name | cust_address     | cust_city | cust_state | cust_zip | cust_country | cust_contact | cust_email          |  
+---------+-----------+------------------+-----------+------------+----------+--------------+--------------+---------------------+  
|   10003 | Wascals   | 1 Sunny Place    | Muncie    | IN         | 42222    | USA          | Jim Jones    | rabbit@wascally.com |  
|   10005 | E Fudd    | 4545 53rd Street | Chicago   | IL         | 54545    | USA          | E Fudd       | NULL                |  
+---------+-----------+------------------+-----------+------------+----------+--------------+--------------+---------------------+  
2 rows in set (0.000 sec)  
  
MariaDB [create]> select * from customers where cust_zip like "4____";  
+---------+-------------+------------------+-----------+------------+----------+--------------+--------------+---------------------+  
| cust_id | cust_name   | cust_address     | cust_city | cust_state | cust_zip | cust_country | cust_contact | cust_email          |  
+---------+-------------+------------------+-----------+------------+----------+--------------+--------------+---------------------+  
|   10001 | Coyote Inc. | 200 Maple Lane   | Detroit   | MI         | 44444    | USA          | Y Lee        | ylee@coyote.com     |  
|   10002 | Mouse House | 333 Fromage Lane | Columbus  | OH         | 43333    | USA          | Jerry Mouse  | NULL                |  
|   10003 | Wascals     | 1 Sunny Place    | Muncie    | IN         | 42222    | USA          | Jim Jones    | rabbit@wascally.com |  
+---------+-------------+------------------+-----------+------------+----------+--------------+--------------+---------------------+  
3 rows in set (0.000 sec)  
  
MariaDB [create]> select * from products where prod_name like "B%d" ;  
+---------+---------+-----------+------------+---------------------------------------+  
| prod_id | vend_id | prod_name | prod_price | prod_desc                             |  
+---------+---------+-----------+------------+---------------------------------------+  
| FB      |    1003 | Bird seed |      10.00 | Large bag (suitable for road runners) |  
+---------+---------+-----------+------------+---------------------------------------+  
1 row in set (0.001 sec)  
  
MariaDB [create]> select item_price from orderitems where order_item = 1;  
+------------+  
| item_price |  
+------------+  
|       5.99 |  
|      55.00 |  
|      10.00 |  
|       2.50 |  
|      10.00 |  
+------------+  
5 rows in set (0.000 sec)  
  
MariaDB [create]> select order_num from orders where order_date regexp '10';  
+-----------+  
| order_num |  
+-----------+  
|     20008 |  
|     20009 |  
+-----------+  
2 rows in set (0.001 sec)  
  
MariaDB [create]> select  vend_name from vendors where vend_state is null;  
+----------------+  
| vend_name      |  
+----------------+  
| Jet Set        |  
| Jouets Et Ours |  
+----------------+  
2 rows in set (0.000 sec)  
  
MariaDB [create]> select vend_id,vend_state from vendors order by 2;  
+---------+------------+  
| vend_id | vend_state |  
+---------+------------+  
|    1005 | NULL       |  
|    1006 | NULL       |  
|    1003 | CA         |  
|    1001 | MI         |  
|    1004 | NY         |  
|    1002 | OH         |  
+---------+------------+  
6 rows in set (0.000 sec)  
  
MariaDB [create]> select prod_id,max(item_price),min(item_price),avg(item_price) from orderitems group by prod_id having count(*)>1;  
+---------+-----------------+-----------------+-----------------+  
| prod_id | max(item_price) | min(item_price) | avg(item_price) |  
+---------+-----------------+-----------------+-----------------+  
| FB      |           10.00 |           10.00 |       10.000000 |  
| TNT2    |           10.00 |           10.00 |       10.000000 |  
+---------+-----------------+-----------------+-----------------+  
2 rows in set (0.000 sec)  
  
MariaDB [create]> select vend_name from vendors where vend_country in ("USA") and vend_name in (select vend_name from vendors where vend_city in ("New York"))  
    -> ;  
+--------------+  
| vend_name    |  
+--------------+  
| Furball Inc. |  
+--------------+  
1 row in set (0.001 sec)  
  
MariaDB [create]> select vend_name from vendors where not exists(select * from vendors where vend_country in ("China"));  
+----------------+  
| vend_name      |  
+----------------+  
| Anvils R Us    |  
| LT Supplies    |  
| ACME           |  
| Furball Inc.   |  
| Jet Set        |  
| Jouets Et Ours |  
+----------------+  
6 rows in set (0.000 sec)  
  
MariaDB [create]> alter table productnotes add fulltext index idx_keyword (note_text);  
Query OK, 14 rows affected (0.207 sec)  
Records: 14  Duplicates: 0  Warnings: 0  
  
MariaDB [create]> select count(*) from productnotes where note_text like "%safe%";  
+----------+  
| count(*) |  
+----------+  
|        4 |  
+----------+  
1 row in set (0.001 sec)
