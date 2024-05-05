---------------------------- Create Table----------------------------------------

CREATE TABLE amitdb.student (
  StudentID INT NOT NULL,
  FirstName VARCHAR(45) NOT NULL,
  LastName VARCHAR(45) NOT NULL,
  Age VARCHAR(45) NOT NULL,
  PRIMARY KEY (StudentID));

SELECT * FROM amitdb.student;

-----------------------------INSERT TABLE---------------------------------------

INSERT INTO amitdb.student (StudentID, FirstName, LastName, Age) VALUES ('1', 'Neha', 'Dalvi', '23');
INSERT INTO amitdb.student (StudentID, FirstName, LastName, Age) VALUES ('2', 'Karan', 'Gosavi', '24');
INSERT INTO amitdb.student (StudentID, FirstName, LastName, Age) VALUES ('3', 'Rohit', 'Pathan', '23');
INSERT INTO amitdb.student (StudentID, FirstName, LastName, Age) VALUES ('4', 'Raj', 'Satpute', '24');
INSERT INTO amitdb.student (StudentID, FirstName, LastName, Age) VALUES ('5', 'Aman', 'Mogal', '24');

SELECT * FROM amitdb.student;


--------------------------------Stored table----------------------------------------

CREATE PROCEDURE get_student_info()
BEGIN
SELECT * FROM amitdb.student;
END

USE amitdb;
DROP procedure IF EXISTS get_student_info;
DELIMITER $$
USE amitdb$$
CREATE PROCEDURE get_student_info()
BEGIN
SELECT * FROM amitdb.student;
END$$
DELIMITER ;

SELECT * FROM amitdb.student;
call get_student1_info();


------------------------------IN--------------------------------

CREATE DEFINER=root@localhost PROCEDURE get_student_info(in age int)
BEGIN
SELECT * FROM amitdb.student where student.age=age;
END

USE amitdb;
DROP procedure IF EXISTS get_student_info;
USE amitdb;
DROP procedure IF EXISTS amitdb.get_student_info;
;
DELIMITER $$
USE amitdb$$
CREATE DEFINER=root@localhost PROCEDURE get_student_info(in age int)
BEGIN
SELECT * FROM amitdb.student where student.age=age;
END$$
DELIMITER ;
;

SELECT * FROM amitdb.student;
call get_student_info(24)


-----------------------------------OUT------------------------------------

CREATE DEFINER=root@localhost PROCEDURE get_student_info(out records int)
BEGIN
SELECT count(*) INTO records FROM amitdb.student where student.age=25;
END

USE amitdb;
DROP procedure IF EXISTS get_student_info;
USE amitdb;
DROP procedure IF EXISTS amitdb.get_student_info;
;
DELIMITER $$
USE amitdb$$
CREATE DEFINER=root@localhost PROCEDURE get_student_info(out records int)
BEGIN
SELECT count(*) INTO records FROM amitdb.student where student.age=24;
END$$
DELIMITER ;
;

SELECT * FROM amitdb.student;
call get_student_info(@records);
select @records as Toatalrecords;



----------------------------INOUT----------------------------------------

CREATE DEFINER=root@localhost PROCEDURE get_student_info(inout records int, in age int)
BEGIN
SELECT count(*) INTO records FROM amitdb.student where student.age= age;
END

USE amitdb;
DROP procedure IF EXISTS get_student_info;
USE amitdb;
DROP procedure IF EXISTS amitdb.get_student_info;
;
DELIMITER $$
USE amitdb$$
CREATE DEFINER=root@localhost PROCEDURE get_student_info(inout records int, in age int)
BEGIN
SELECT count(*) INTO records FROM amitdb.student where student.age= age;
END$$
DELIMITER ;
;

SELECT * FROM amitdb.student;
call get_student_info(@records,24);
select @records as Toatalrecords;
