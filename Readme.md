
Question 1:
mysql> select first_name, last_name from student;
+------------+-----------+
| first_name | last_name |
+------------+-----------+
| Eric       | Ephram    |
| Greg       | Gould     |
| Adam       | Ant       |
| Howard     | Hess      |
| Charles    | Caldwell  |
| James      | Joyce     |
| Doug       | Dumas     |
| Kevin      | Kraft     |
| Frank      | Fountain  |
| Brian      | Biggs     |
+------------+-----------+
10 rows in set (0.00 sec)

Question 2:
mysql> select * from student where years_of_experience < 8;
+------------+------------+-----------+---------------------+------------+
| student_id | first_name | last_name | years_of_experience | start_date |
+------------+------------+-----------+---------------------+------------+
|          1 | Eric       | Ephram    |                   2 | 2016-03-31 |
|          2 | Greg       | Gould     |                   6 | 2016-09-30 |
|          3 | Adam       | Ant       |                   5 | 2016-06-02 |
|          4 | Howard     | Hess      |                   1 | 2016-02-28 |
|          5 | Charles    | Caldwell  |                   7 | 2016-05-07 |
|          8 | Kevin      | Kraft     |                   3 | 2016-04-15 |
|         10 | Brian      | Biggs     |                   4 | 2015-12-25 |
+------------+------------+-----------+---------------------+------------+
7 rows in set (0.00 sec)

Question 3:
mysql> select last_name, start_date, student_id from student
    -> Order By last_name;
+-----------+------------+------------+
| last_name | start_date | student_id |
+-----------+------------+------------+
| Ant       | 2016-06-02 |          3 |
| Biggs     | 2015-12-25 |         10 |
| Caldwell  | 2016-05-07 |          5 |
| Dumas     | 2016-07-04 |          7 |
| Ephram    | 2016-03-31 |          1 |
| Fountain  | 2016-01-31 |          9 |
| Gould     | 2016-09-30 |          2 |
| Hess      | 2016-02-28 |          4 |
| Joyce     | 2016-08-27 |          6 |
| Kraft     | 2016-04-15 |          8 |
+-----------+------------+------------+
10 rows in set (0.00 sec)

Question 4:
mysql> select * from student where first_name in ('Adam', 'James', 'Frank');
+------------+------------+-----------+---------------------+------------+
| student_id | first_name | last_name | years_of_experience | start_date |
+------------+------------+-----------+---------------------+------------+
|          3 | Adam       | Ant       |                   5 | 2016-06-02 |
|          6 | James      | Joyce     |                   9 | 2016-08-27 |
|          9 | Frank      | Fountain  |                   8 | 2016-01-31 |
+------------+------------+-----------+---------------------+------------+
3 rows in set (0.00 sec)

Question 5:
mysql> select last_name, first_name, start_date from student
    -> where start_date between '2016-01-01' and '2016-06-30'
    -> order by start_date desc;
+-----------+------------+------------+
| last_name | first_name | start_date |
+-----------+------------+------------+
| Ant       | Adam       | 2016-06-02 |
| Caldwell  | Charles    | 2016-05-07 |
| Kraft     | Kevin      | 2016-04-15 |
| Ephram    | Eric       | 2016-03-31 |
| Hess      | Howard     | 2016-02-28 |
| Fountain  | Frank      | 2016-01-31 |
+-----------+------------+------------+
6 rows in set (0.00 sec)

Medium Challenge

mysql> explain assignment;
+----------------+------------------+------+-----+---------+----------------+
| Field          | Type             | Null | Key | Default | Extra          |
+----------------+------------------+------+-----+---------+----------------+
| assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| student_id     | int(11)          | NO   |     | NULL    |                |
| assignment_nbr | int(11)          | NO   |     | NULL    |                |
| class_id       | int(11)          | YES  |     | NULL    |                |
| grade_id       | int(11) unsigned | NO   | MUL | NULL    |                |
+----------------+------------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

ysql> select * from assignment;
+---------------+------------+----------------+----------+----------+
| assignment_id | student_id | assignment_nbr | class_id | grade_id |
+---------------+------------+----------------+----------+----------+
|             1 |          4 |              6 |     NULL |        1 |
|             2 |          7 |              6 |     NULL |        3 |
|             3 |         10 |              6 |     NULL |        4 |
|             4 |          5 |              6 |     NULL |        3 |
|             5 |          1 |              6 |     NULL |        5 |
|             6 |          6 |              6 |     NULL |        2 |
|             7 |          8 |              6 |     NULL |        3 |
+---------------+------------+----------------+----------+----------+
7 rows in set (0.00 sec)

mysql> explain grade;
+----------+------------------+------+-----+---------+----------------+
| Field    | Type             | Null | Key | Default | Extra          |
+----------+------------------+------+-----+---------+----------------+
| grade    | varchar(30)      | YES  |     | NULL    |                |
| grade_id | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
+----------+------------------+------+-----+---------+----------------+
2 rows in set (0.00 sec)

mysql> select * from grade;
+-----------------------------+----------+
| grade                       | grade_id |
+-----------------------------+----------+
| Incomplete                  |        1 |
| Complete and unsatisfactory |        2 |
| Complete and satisfactory   |        3 |
| Exceeds expectations        |        4 |
| Not graded                  |        5 |
+-----------------------------+----------+
5 rows in set (0.00 sec)

Hard Challenge

mysql> describe assignment
    -> ;
+----------------+------------------+------+-----+---------+----------------+
| Field          | Type             | Null | Key | Default | Extra          |
+----------------+------------------+------+-----+---------+----------------+
| assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| student_id     | int(11)          | NO   | MUL | NULL    |                |
| assignment_nbr | int(11)          | NO   |     | NULL    |                |
| class_id       | int(11)          | YES  |     | NULL    |                |
| grade_id       | int(11) unsigned | NO   | MUL | NULL    |                |
+----------------+------------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)
