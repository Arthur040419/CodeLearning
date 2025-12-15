```mysql
drop table if exists  `departments` ; 
drop table if exists  `dept_emp` ; 
drop table if exists  titles ;
CREATE TABLE `departments` (
`dept_no` char(4) NOT NULL,
`dept_name` varchar(40) NOT NULL,
PRIMARY KEY (`dept_no`));
CREATE TABLE `dept_emp` (
`emp_no` int(11) NOT NULL,
`dept_no` char(4) NOT NULL,
`from_date` date NOT NULL,
`to_date` date NOT NULL,
PRIMARY KEY (`emp_no`,`dept_no`));
CREATE TABLE titles (
`emp_no` int(11) NOT NULL,
`title` varchar(50) NOT NULL,
`from_date` date NOT NULL,
`to_date` date DEFAULT NULL);
INSERT INTO departments VALUES('d001','Marketing');
INSERT INTO departments VALUES('d002','Finance');
INSERT INTO dept_emp VALUES(10001,'d001','1986-06-26','9999-01-01');
INSERT INTO dept_emp VALUES(10002,'d001','1996-08-03','9999-01-01');
INSERT INTO dept_emp VALUES(10003,'d002','1995-12-03','9999-01-01');
INSERT INTO titles VALUES(10001,'Senior Engineer','1986-06-26','9999-01-01');
INSERT INTO titles VALUES(10002,'Staff','1996-08-03','9999-01-01');
INSERT INTO titles VALUES(10003,'Senior Engineer','1995-12-03','9999-01-01');
```



```mysql
d001|Marketing|Senior Engineer|1
d001|Marketing|Staff|1
d002|Finance|Senior Engineer|1
```

