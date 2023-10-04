# Ex-No-5-Creating-Triggers-using-PL-SQL
# AIM: 
To create a Trigger using PL/SQL.
# Steps:

    1.Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);

    2.Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);

    3.Create a trigger named as log_salary-update.

    4.Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.

   5. End the trigger.

    6.Update the salary of an employee in employee table.

    7.Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.

   8. Display the employee table, salary_log table.

# Program:

CREATE TABLE employed( empid NUMBER, empname VARCHAR2(10), dept VARCHAR2(10), salary NUMBER );

CREATE TABLE sal_log ( log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER, empname VARCHAR2(10), old_salary NUMBER, new_salary NUMBER, update_date DATE );

-- Insert the values in the employee table insert into employed values(1,'Shakthi','IT',1000000); insert into employed values(2,'Suju','SALES',500000)
# Create employee table
<br>
<img width="248" alt="271347434-2a3c06db-cad0-45ac-b88f-a90d2bb184ce" src="https://github.com/thrikesh/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119576222/243ffb4b-1eb9-4526-9a99-ab3b8e295985">


# Create salary_log table
<br>
<img width="353" alt="271347554-1e6f4538-b166-40e8-beed-e366c40d9655" src="https://github.com/thrikesh/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119576222/60eab22c-6158-4653-8077-8d54575be17a">


image
# PLSQL Trigger code

-- Create the trigger CREATE OR REPLACE TRIGGER log_sal_update BEFORE UPDATE ON employed FOR EACH ROW BEGIN

IF :OLD.salary != :NEW.salary THEN INSERT INTO sal_log (empid, empname, old_salary, new_salary, update_date) VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE); END IF; END; /

-- Insert the values in the employee table insert into employed values(1,'Shakthi','IT',1000000); insert into employed values(2,'Suju','SALES',500000);

-- Update the salary of an employee UPDATE employed SET salary = 60000 WHERE empid = 1; -- Display the employee table SELECT * FROM employed;

-- Display the salary_log table SELECT * FROM sal_log;
# Output:
<br>
<img width="308" alt="271347898-179db77c-09e3-4228-ba15-c3da3def7a2e" src="https://github.com/thrikesh/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119576222/5312477f-2438-4c4c-8228-0a0a86a21724">
<br>
<img width="460" alt="271348015-3b6cae3e-afba-4618-bf65-99e80fb07e54" src="https://github.com/thrikesh/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119576222/ce45e494-bc23-46a7-93cd-d39037ce77ab">




# Result:
The program has been implemented successfully
