**PL/SQL - Constants and Literals**

A constant holds a value that once declared, does not change in the program. A constant declaration specifies its name, data type, and value, and allocates storage for it. The declaration can also impose the NOT NULL constraint.

**Declaring a Constant**

A constant is declared using the CONSTANT keyword. It requires an initial value and does not allow that value to be changed. For example:
```sql
PI CONSTANT NUMBER := 3.141592654;
```

```sql
DECLARE
   -- constant declaration
   pi constant number := 3.141592654;
   -- other declarations
   radius number(5,2);
   dia number(5,2);
   circumference number(7, 2);
   area number (10, 2);
BEGIN
   -- processing
   radius := 9.5;
   dia := radius * 2;
   circumference := 2.0 * pi * radius;
   area := pi * radius * radius;
   -- output
   dbms_output.put_line('Radius: ' || radius);
   dbms_output.put_line('Diameter: ' || dia);
   dbms_output.put_line('Circumference: ' || circumference);
   dbms_output.put_line('Area: ' || area);
END;
/
```

When the above code is executed at SQL prompt, it produces the following result:
```
Radius: 9.5
Diameter: 19
Circumference: 59.69
Area: 283.53

Pl/SQL procedure successfully completed.
```

**The PL/SQL Literals**

A literal is an explicit numeric, character, string, or Boolean value not represented by an identifier. For example, TRUE, 786, NULL, 'tutorialspoint' are all literals of type Boolean, number, or string. PL/SQL, literals are case-sensitive. PL/SQL supports the following kinds of literals:

* Numeric Literals
* Character Literals
* String Literals
* BOOLEAN Literals
* Date and Time Literals

The following table provides examples from all these categories of literal values.

| Literal Type            | Example:                          |
|-------------------------|-----------------------------------|
| Numeric Literals        | 050 78 -14 0 +32767               |
|                         | 6.6667 0.0 -12.0 3.14159 +7800.00 |
|                         | 6E5 1.0E-8 3.14159e0 -1E38 -9.5e-3|
|Character Literals       |'A' '%' '9' ' ' 'z' '('            |
|String Literals          |'Hello, world!'                    |
|                         |'Tutorials Point'                  |
|                         |'19-NOV-12'                        |
|BOOLEAN Literals         |TRUE, FALSE, and NULL.             |
|Date and Time Literals   |DATE '1978-12-25';                 |
|                         |TIMESTAMP '2012-10-29 12:01:01';   |

To embed single quotes within a string literal, place two single quotes next to each other as shown below:
```sql
DECLARE
   message  varchar2(30):= 'That''s tutorialspoint.com!';
BEGIN
   dbms_output.put_line(message);
END;
/
```

When the above code is executed at SQL prompt, it produces the following result:
```
That's tutorialspoint.com!

PL/SQL procedure successfully completed.
```
