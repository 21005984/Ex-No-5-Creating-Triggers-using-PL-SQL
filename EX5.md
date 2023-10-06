# Ex. No: 5 Creating Triggers using PL/SQL

### AIM: To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:
### Create worker table
~~~
CREATE TABLE worker
(
empid NUMBER,
empname VARCHAR2(10)
dept VARCHAR2(10),
salary NUMBER
);
~~~
### Create vj_log table
~~~
CREATE TABLE vj_log
(
log_id NUMBER GENERATED ALWAYS AS IDENTITY,
empid NUMBER,
empname VARCHAR2(10),
old_salary NUMBER,
new_salary NUMBER,
update_date DATE
);
~~~
### PLSQL Trigger code
~~~
CREATE OR REPLACE TRIGGER logging_insurence_update
BEFORE UPDATE ON worker
FOR EACH ROW
BEGIN
IF :OLD.salary != :NEW.salary THEN
INSERT INTO vj_log (empid, empname, old_salary, new_salary, update_date)
VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
END IF;
END;
/
~~~
# Inserting data into workertable
~~~
insert into worker values(1,'diya','sales',10000);
insert into worker values(2,'vidya','manager',20000);
insert into worker values(3,'nithya','hr',30000);
~~~
# update the salary of the worker
~~~
UPDATE worker
set salary = 12000
where empid=3;
~~~
# # Display the worker table
~~~
select * from worker;
~~~
# Display the vj_log table
~~~
select * from vj_log;
~~~

### Output:
# create table for worker
![image](https://github.com/21005984/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94748389/6fa050b2-18a7-4ff1-9c39-d13346848f51)

# create table for vj_log

![image](https://github.com/21005984/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94748389/8fb16f3b-3a78-4f33-8e6f-7d474b61ecd9)
# insert the data into the worker table
![image](https://github.com/21005984/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94748389/7bb0393c-a96c-482b-8793-5684f7092771)

# create a trigger named logging_insurance_update

![image](https://github.com/21005984/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94748389/ecdaf0c4-bef0-4249-b994-6f4203f12ea9)

## Display the worker table

![image](https://github.com/21005984/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94748389/3c97e284-6fce-4c42-ba7c-68a6975d6007)

## update the worker table

![image](https://github.com/21005984/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94748389/9cbfef1e-4c1c-4377-bc44-caf3a73b3398)


## display the vj_log

![image](https://github.com/21005984/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94748389/60c2185e-9c4d-4823-b461-4809abdc4d94)

### Result:
The program has been implemented successfully.
