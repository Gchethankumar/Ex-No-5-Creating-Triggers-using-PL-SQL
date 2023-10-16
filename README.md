# Ex-No-5-Creating Triggers using PL/SQL

## AIM: 
To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

## Program:
```
Developed By: Chethan Kumar G
Register number: 212222240022
```
### Create employee table:
```sql
create table EMPLOYEE1(empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
```
### Insert values into employee table:
```sql
insert into EMPLOYEE(empid,empname,dept,salary) values(1,'Chandru','HR',2500000);
insert into EMPLOYEE(empid,empname,dept,salary) values(2,'Chethan','MD',950000);
insert into EMPLOYEE(empid,empname,dept,salary) values(3,'Dileep','HR',800000);
```
### Create salary_log table
```sql
create table salary_log (log_id NUMBER , empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
```
### PLSQL Trigger code
```sql
create or replace trigger log_salary_update
  2      before update on EMPLOYEE1
  3      for each row
  4      declare
  5      v_old_salary number;
  6      v_new_salary number;
  7      begin
  8      v_old_salary := :OLD.salary;
  9      v_new_salary := :NEW.salary;
 10      if v_old_salary <> v_new_salary then
 11      insert into salary_log(empid,empname,old_salary,new_salary,update_date)values(:OLD.empid,:OLD.empname,v_old_salary,v_new_salary,SYSDATE);
 12      end if;
 13      end;
 14      /
```
### Update the salary of an employee:
```sql
update EMPLOYEE1 set salary = 97000 where empid = 2;
```
### Display the salary_log table:
```sql
select * from salary_log;
```
## Output:
![Screenshot 2023-10-16 175717](https://github.com/Gchethankumar/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/118348224/f8d09ac9-43d8-4714-8c68-dc00a8bab0ae)

## Result:
Thus, a trigger using PL/SQL is created successfully.
