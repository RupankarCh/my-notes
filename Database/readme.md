# SQL: 
Structured, table-based, fixed schema (Highly reliable & consistent)

SQL Errors in Web Applications
SQL errors in web applications occur when there is an issue with the SQL query execution. These errors can range from syntax errors, which prevent a query from executing, to logic errors, which might cause incorrect results or unexpected behavior. SQL errors, when improperly handled, can expose critical information to attackers, which can be exploited for malicious purposes, such as SQL Injection (SQLi), unauthorized access, or data leaks.

Malicious inputs can trigger database errors that reveal information about the database structure, helping attackers craft more targeted attacks.
o Example:
SELECT * FROM users WHERE user_id = 1 AND password = 'password';

If the password is wrong and an attacker manipulates the input to cause an error, the error message could reveal the underlying database structure or column names.

Improper handling of SQL error messages may lead to information disclosure.
-Database Type
-Database Query Structure 
-Query Execution Flow
-Predictable Error

Error-based In-band SQL Injection – The attacker triggers an error in the database, and the error message contains valuable information about the structure of the database, which can be
used for further attacks.
1. Error-based In-band SQLi:
o An attacker might input something like ' OR 1=1 -- in a login form.
o Query:
SELECT * FROM users WHERE username = '' OR 1=1 --' AND password = 'password';
o The -- is a comment in SQL, so everything after it is ignored. This query returns all users, allowing
the attacker to bypass authentication.
o Error Example: A malformed input might result in an error message like:
SQL Error: Unknown column 'username' in 'where clause'
The attacker can use this error to infer the structure of the database and adjust the attack.

ERROR 1064 (42000): presence of a WHERE clause in the query.

Mitigation:
- Disable Detailed Error Messages Disclosure to client :
Error Handling: Avoid exposing detailed database errors to users, as they can provide clues to attackers about the database structure.Error Handling Ensure that detailed database errors are not exposed to end-users. Display generic error messages that do not reveal the underlying database structure or query details. This can help prevent attackers from gaining useful information about the system.
- Use Custom Error Pages that do not reveal info about DB
- Use Error Handling to capture errors

# NoSQL: 
Flexible, non-table, dynamic schema (Very fast & scalable)
