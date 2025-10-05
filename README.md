# Elevate_Labs_Task8
Procedures, Functions

1. Difference between Procedure and Function

Definition:
A procedure is a block of SQL statements that performs a task, while a function returns a value.

Explanation:

A procedure may or may not return a value.

A function must return a value using RETURN.

Functions can be used in SQL queries; procedures cannot.

Example:

CREATE PROCEDURE getEmployees AS SELECT * FROM employees;
CREATE FUNCTION getCount() RETURNS INT AS BEGIN RETURN (SELECT COUNT(*) FROM employees); END;


In short:
Procedures perform actions; functions return results.

2. What is IN/OUT Parameter?

Definition:
They define how data is passed to and from procedures or functions.

Explanation:

IN: Passes a value into the procedure (read-only).

OUT: Returns a value back to the caller.

INOUT: Used for both input and output.

Example:

CREATE PROCEDURE getBonus(IN emp_id INT, OUT bonus DECIMAL(10,2))


In short:
IN = input only, OUT = output only, INOUT = both.

3. Can functions return tables?

Answer:
Yes. A table-valued function (TVF) can return an entire table instead of a single value.

Example:

CREATE FUNCTION getHighSalaryEmployees()
RETURNS TABLE
AS RETURN (SELECT * FROM employees WHERE salary > 50000);


In short:
Yes — TVFs return result sets like a table.

4. What is RETURN used for?

Definition:
It specifies the value that a function sends back to the caller.

Explanation:
In stored functions, RETURN ends execution and returns a value.

Example:

CREATE FUNCTION addTwoNumbers(a INT, b INT)
RETURNS INT AS BEGIN RETURN a + b; END;


In short:
RETURN sends back a value from a function.

5. How to call stored procedures?

Answer:
Use the EXEC or CALL command.

Example:

EXEC getEmployees;
-- or
CALL getEmployees();


In short:
Use EXEC or CALL to run a stored procedure.

6. What is the benefit of stored routines?

Explanation:

Improve performance (precompiled and reusable).

Maintain security (limit direct table access).

Enhance modularity and reusability.

In short:
Stored routines make code faster, reusable, and secure.

7. Can procedures have loops?

Answer:
Yes, stored procedures can use loops like WHILE, FOR, or LOOP.

Example:

WHILE counter < 10
BEGIN
  SET counter = counter + 1;
END


In short:
Yes — procedures can contain looping logic.

8. Difference between Scalar and Table-Valued Functions
Type	Returns	Usage
Scalar	Single value	Used in SELECT/WHERE
Table-Valued	Table	Used as table in FROM clause

Example:

Scalar: SELECT dbo.getSalary(101)

TVF: SELECT * FROM dbo.getHighSalaryEmployees()

In short:
Scalar = one value; Table-valued = multiple rows.

9. What is a Trigger?

Definition:
A trigger is a stored procedure that runs automatically when an event occurs (INSERT, UPDATE, DELETE).

Example:

CREATE TRIGGER trg_Audit
AFTER INSERT ON employees
FOR EACH ROW
INSERT INTO audit_log VALUES ('Employee added');


In short:
Trigger = automatic action when data changes.

10. How to debug stored procedures?

Explanation:

Use PRINT or SELECT statements to show variable values.

Use SQL Server Management Studio (SSMS) or Oracle/PLSQL debugger tools.

Step through code to find logic errors.

In short:
Debug using print statements or built-in SQL debugging tools.
