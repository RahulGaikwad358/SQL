# SQL
SQL QUERY


// Practice Sql Query

CREATE DATABASE ORG;
SHOW DATABASES;
USE ORG;

CREATE TABLE Worker (
worker_id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
FIRST_NAME VARCHAR(25),
LAST_NAME VARCHAR(25),
SALARY INT(25),
JOINING_DATE DATETIME,
DEPARTMENT CHAR(25));
INSERT INTO Worker 
(worker_id,FIRST_NAME,LAST_NAME,SALARY,JOINING_DATE,DEPARTMENT) VALUES
(001,'MONIKA','ARORA',100000,'14-02-20 09.00.00', 'HR'),
(002,'NIHARIKA','VERMA',80000,'14-06-11 09.00.00','ADMIN'),
(003,'VISHAL','SINGHAL',300000,'14-02-20 09.00.00','HR'),
(004,'AMITABH','SINGH',500000,'14-02-20 09.00.00','ADMIN'),
(005,'VIVEK','BHATI',500000,'14-06-11 09.00.00','ADMIN'),
(006,'VIPUL','DIWAN',200000,'14-06-11 09.00.00','ACCOUNT'),
(007,'SATISH','KUMAR',75000,'14-01-20 09.00.00','ACCOUNT'),
(008,'GEETIKA','CHAUHAN',90000,'14-04-11 09.00.00','ADMIN');

CREATE TABLE Bonus (
WORKER_REF_ID INT,
BONUS_AMOUNT INT(10),
BONUS_DATE DATETIME,
FOREIGN KEY (WORKER_REF_ID)
REFERENCES WORKER(WORKER_ID)
ON DELETE CASCADE
);

INSERT INTO Bonus
(WORKER_REF_ID, BONUS_AMOUNT,BONUS_DATE) VALUES
(001,5000,'16-02-20'),
(002,3000,'16-06-11'),
(003,4000,'16-02-20'),
(001,4500,'16-02-20'),
(002,3500,'16-04-11');

CREATE TABLE titless (
WORKER_REF_ID INT,
WORKER_TITLE VARCHAR(25),
AFFECTED_FROM DATETIME,
FOREIGN KEY (WORKER_REF_ID)
REFERENCES WORKER(WORKER_ID)
ON DELETE CASCADE
);

INSERT INTO titless
(WORKER_REF_ID,WORKER_TITLE,AFFECTED_FROM) VALUES
(001,'MANAGER','2016-02-20 00:00:00'),
(002,'EXECUTIVE','2016-06-11 00;00;00'),
(008,'EXECUTIVE','2016-06-11 00;00;00'),
(005,'MANAGER','2016-06-11 00;00;00'),
(004,'ASST.MANAGER','2016-06-11 00;00;00'),
(007,'EXECUTIVE','2016-06-11 00;00;00'),
(006,'LEAD','2016-06-11 00;00;00'),
(003,'LEAD','2016-06-11 00;00;00');

-- SELECT * FROM WORKER WHERE MOD(WORKER_ID,2) != 0;
-- SELECT * FROM WORKER WHERE MOD(WORKER_ID,2) = 0;

-- CREATE TABLE WORKER_CLONE LIKE WORKER;
-- INSERT INTO WORKER_CLONE SELECT * FROM WORKER
-- SELECT * FROM WORKER_CLONE;
-- SELECT WORKER.* FROM WORKER INNER JOIN WORKER_CLONE USING(WORKER_ID)
-- SELECT * FROM WORKER LEFT JOIN WORKER_CLONE USING(WORKER_ID) WHERE WORKER_CLONE .WORKER_ID IS NULL;
-- SELECT CURDATE()
 -- SELECT * FROM WORKER ORDER BY SALARY  LIMIT 5;
--  SELECT * FROM WORKER ORDER BY SALARY DESC  LIMIT 4,1;
-- SELECT SALARY FROM WORKER W1
-- WHERE 4 = (
-- SELECT COUNT(DISTINCT (W2.SALARY))
-- FROM WORKER W2
-- WHERE W2. SALARY >= W1.SALARY 

-- SELECT * FROM WORKER W1 ,WORKER W2 WHERE W1.SALARY = W2.SALARY AND W1.WORKER_ID != W2.WORKER_ID;

-- SELECT FIRST_NAME AS WORKER_NAME FROM WORKER

-- Q.2 WRITE  ans sql query to fetch first_name from worker table in upper case
 -- SELECT UPPER(FIRST_NAME) FROM WORKER
 
 -- Q.3 WRITE ANS SQL QUERY TO FETCH UNIQUE VALUES OF DEPARTMENT FROM WORKER TABLE 
 -- SELECT DISTINCT DEPARTMENT FROM WORKER 

-- Q.4 WIRTE AN SQL QUERY TO PRINT THE FIRSR THREE CHARACTERS OF FIRST_NAME FROM WORKER TABLE
-- SELECT SUBSTRING(FIRST_NAME, 1,3) FROM WORKER
	
-- Q 4 WRITE AN SQL QUERY TO FIND POSITION OF THE ALPHABET ('b') IN THE FIRST NAME COLUMN PF AMITABH FROM WORKER
-- SELECT INSTR(FIRST_NAME, 'B') FROM WORKER WHERE FIRST_NAME = 'AMITABH'

-- Q 5 WRITE AN SQL QUERY TO PRINT THE FIRST_NAME FROM WORKER TABLE AFTER REOVIING WHITE SPACES FROM THE RIGHT SIDE
-- SELECT RTRIM(FIRST_NAME) FROM WORKER

-- Q 5 WRITE AN SQL QUERY TO PRINT THE FIRST_NAME FROM WORKER TABLE AFTER REOVIING WHITE SPACES FROM THE LEFT SIDE
-- SELECT LTRIM(FIRST_NAME) FROM WORKER

-- Q.6  WRITE AN SQL QUERY THAT FETCHES THE UNIQUE VALUES OF DEPARTMENT FROMM WORKER TABLE AND PRINT ITS LENGTH
-- SELECT DISTINCT DEPARTMENT, LENGTH(DEPARTMENT) FROM WORKER

-- Q.8 WRITE AN SQL QUERY TO PRINT THE FIRST_NAME FROM WORKER TABLE AFTER REPLACING 'a' WITH 'A'
-- SELECT REPLACE(FIRST_NAME, 'a', 'A') FROM WORKER

-- 		Q.10 WRITE AN SQL QUERY TO PRINT THE FIRST_NAME AND LAST_NAME FROM WORKER TABLE INT A SING COLUMN COMPLETE NAME
-- SELECT CONCAT(FIRST_NAME,' ',LAST_NAME) AS COMPLETE_NAME FROM WORKER

-- Q.11 WRITE AN SQL QUERY TO PRINT ALL WOKER DETAILS FROM THE WORKER TABLE ORDER BYS FIRST_NAME ASCENDING
-- SELECT * FROM WORKER ORDER BY FIRST_NAME 

-- Q.12 WRITE AN SQL QUERY TO PRINT ALL WORKER DETAILS FROM THE WORKER TABLE ORDER BY FIRST_NAME ASCENDING AND DEPAETMENT DESENDING
-- SELECT * FROM WORKER ORDER BY FIRST_NAME , DEPARTMENT DESC

-- Q.13 WRITE AN SQL QUERY TO PRINT ALL DETAILS FOR WORKERS WITH THE FIRST_NAME AS "VIPUL " AND "SATISH" FROM  WORKER TABLE
-- SELECT * FROM WORKER WHERE FIRST_NAME IN ('VIPUL','SATISH')  

-- Q.14 WRITE AN SQL QUERY  TO , PPRINT DETAILS OF WORKERS EXCLUDING FIRST_NAME 'VIPUL' AND 'SATISH' FROM WORKER TABLE
-- SELECT * FROM WORKER WHERE FIRST_NAME NOT IN ('VIPUL','SATISH')


-- Q.15 WRITE AN SQL QUERY TO PRINT DETAILS OF WORKERS WITH DEPARTMENT NAME AS'ADMIN'
-- SELECT * FROM WORKER WHERE DEPARTMENT LIKE 'ADMIN'

-- Q.16 WRITE AN SQL QUERY TO PRINT DETAILS OF THE WORKERS WHOSE FIRST_NAME CONTAINS 'a'
-- SELECT * FROM WORKER WHERE FIRST_NAME LIKE '%a%'

-- Q,17 WRITE AN SQL QUERY TO PRINT DETAILS OF THE WORKER WHERE FIRST NAME ENDS WITH 'A'
-- SELECT * FROM WORKER WHERE FIRST_NAME LIKE '%a'

-- Q.18 WRITE AN SQL QUERY TO PRINT DETAILS OF THE WORKER WHOSE FIRST_NAME ENDS WITH 'A' AND CONTAINS SIX ALPHABETS
-- SELECT * FROM WORKER WHERE FIRST_NAME LIKE '_____a'

-- Q.19 WRITE AN AQL QUERY TO PRINT DETAILS OF  THE WORKERS WHOSE SALARY LIES BETWEEN 100000 AND 500000
-- SELECT * FROM WORKER WHERE SALARY BETWEEN  100000 AND 500000

-- Q.20 WRITE AN SQL QUERY  WHO JOINED IN FEB '2014'
-- SELECT * FROM WORKER WHERE YEAR(JOINING_DATE) = 2014 AND MONTH(JOINING_DATE) = 02

-- Q.21 WRITE AN SQL QUERY TO FETCH THE COUNT OF EMPLOYEES WORKING IN THE DEPARTMENT 'ADMIN'
-- SELECT DEPARTMENT , COUNT(*) FROM WORKER WHERE DEPARTMENT = 'ADIMN'

-- Q. 22 WRITE AN SQL QUERY TO FETCH WORKER FULL NAME WITH SALARIES >=  50000 AND <= 100000
-- SELECT CONCAT(FIRST_NAME,' ',LAST_NAME) FROM WORKER WHERE SALARY BETWEEN 50000 AND 

-- Q.23 WRITE AN SQL QUERY TO FETCH THE NO OF WORKERS FOR EACH DEPARTMENT IN THE DESCENDING ORDER
-- SELECT DEPARTMENT, COUNT(WORKER_ID) FROM WORKER GROUP BY DEPARTMENT ORDER BY COUNT(WORKER_ID) DESC

-- Q.24 WRITE AN SQL QUERY TO PRINT DETAILS OF THE WORKERS WHO ARE ALSO MANAGERS 
-- SELECT W * FROM WORKER AS W INNER JOIN titless AS T ON W.WORKER_ID = T.WORKER_REF_ID WHERE T.WORKER_TITLE = 'MANAGER'

-- Q.25 WRITE AN SQL QUERY TO FETCH NUMBER (MORE THAN 1) OFSAME  TITLES IN THE ORG
 -- 33GTSELECT WORKER_TITLE, COUNT(*) FROM titless GROUP BY WORKER_TITLE HAVING COUNT(*) > 1
 
 -- Q.26 WRITE AN SQL QUERY TO SHOW ONLY ODD ROWS FROM TABLE
 -- SELECT * FROM WORKER WHERE MOD(WORKER_ID, 2) != 0;
 
 -- Q.27  WRITE AN SQL QUERY TO SHOW EVEN ROWS FROM TABLE 
--  * FROM WORKER WHERE MOD(WORKER_ID, 2) = 0;

-- Q.28 WRITE AN SQL QUERY TO CLONE A NEW TABLE FROM ANOTHER TABLE
-- CREATE TABLE WORKER_CLONE  LIKE WORKER
-- INSERT INTO WORKER_CLONE SELECT * FROM WORKER

-- Q.29 WRITE AN SQL QUERY TO FETCH INTERSECTING RECORDS OF TWO TABLE 
 -- SELECT  WORKER. * FROM WORKER INNER JOIN WORKER_CLONE USING(WORKER_ID);
 
 -- Q.30 WRITE AN SQL QUERY TO SHOW RECORDS FROM ONE TABLE THAT ANOTHER TABLE DOES NOT HAVE 
 -- SELECT WORKER.* FROM WORKER LEFT JOIN WORKER_CLONE USING(WORKER_ID) WHERE WORKER_CLONE.WORKER_ID IS NULL;
 
 --  Q.31 WRITE AN SQL QUERY TO SHOW CURRENT  DATE AND TIME 
 -- SELECT CURDATE();
 -- SELECT NOW(); 
 
 -- Q.32 WRITE AN SQL QUERY TO SHOW THE TOP N (SAY 5) RECORDS OF A TABLE ORDER BY DESCENDING ORDER
 -- SELECT * FROM WORKER ORDER BY SALARY DESC LIMIT 5;
 
 -- Q.33 WRITE AN SQL QUERY TO DETERMINE THE NTH (SAY N=5) HIGEST SALARY FROM TABLE
--  SELECT * FROM WORKER ORDER BY SALARY DESC LIMIT 4,1 
