---------------------------- Create Table----------------------------------------

CREATE TABLE `amitdb`.`student` (
  `StudentID` INT NOT NULL,
  `FirstName` VARCHAR(45) NOT NULL,
  `LastName` VARCHAR(45) NOT NULL,
  `Age` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`StudentID`));

SELECT * FROM amitdb.student;
