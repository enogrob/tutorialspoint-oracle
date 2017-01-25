**PL/SQL - Operators**

An operator is a symbol that tells the compiler to perform specific mathematical or logical manipulation. PL/SQL language is rich in built-in operators and provides the following types of operators:

* Arithmetic operators
* Relational operators
* Comparison operators
* Logical operators
* String operators

This tutorial will explain the arithmetic, relational, comparison and logical operators one by one. The String operators will be discussed under the chapter: PL/SQL - Strings.

**Arithmetic Operators**

Following table shows all the arithmetic operators supported by PL/SQL. Assume variable A holds 10 and variable B holds 5 then:

Show Examples
```sql
BEGIN
   dbms_output.put_line( 10 + 5);
   dbms_output.put_line( 10 - 5);
   dbms_output.put_line( 10 * 5);
   dbms_output.put_line( 10 / 5);
   dbms_output.put_line( 10 ** 5);
END;
/
```

Operator	Description	Example

`+`	Adds two operands	A + B will give 15.

`-`	Subtracts second operand from the first	A - B will give 5.

`*`	Multiplies both operands	A * B will give 50.

`/`	Divides numerator by de-numerator	A / B will give 2.

`**`	Exponentiation operator, raises one operand to the power of other	A ** B will give 100000.

**Relational Operators**

Relational operators compare two expressions or values and return a Boolean result. Following table shows all the relational operators supported by PL/SQL. Assume variable A holds 10 and variable B holds 20, then:

Show Examples
```sql
DECLARE
   a number (2) := 21;
   b number (2) := 10;
BEGIN
   IF (a = b) then
      dbms_output.put_line('Line 1 - a is equal to b');
   ELSE
      dbms_output.put_line('Line 1 - a is not equal to b');
   END IF;

   IF (a < b) then
      dbms_output.put_line('Line 2 - a is less than b');
   ELSE
      dbms_output.put_line('Line 2 - a is not less than b');
   END IF;

   IF ( a > b ) THEN
      dbms_output.put_line('Line 3 - a is greater than b');
   ELSE
      dbms_output.put_line('Line 3 - a is not greater than b');
   END IF;

   -- Lets change value of a and b
   a := 5;
   b := 20;
   IF ( a <= b ) THEN
      dbms_output.put_line('Line 4 - a is either equal or less than b');
   END IF;

   IF ( b >= a ) THEN
      dbms_output.put_line('Line 5 - b is either equal or greater than a');
   END IF;

   IF ( a <> b ) THEN
      dbms_output.put_line('Line 6 - a is not equal to b');
   ELSE
      dbms_output.put_line('Line 6 - a is equal to b');
   END IF;

END;
/
```

Operator	Description	Example

`=`	Checks if the values of two operands are equal or not, if yes then condition becomes true.	(A = B) is not true.

`!=` `<>` `~=`	Checks if the values of two operands are equal or not, if values are not equal then condition becomes true.	(A != B) is true.

`>`	Checks if the value of left operand is greater than the value of right operand, if yes then condition becomes true.	(A > B) is not true.

`<`	Checks if the value of left operand is less than the value of right operand, if yes then condition becomes true.	(A < B) is true.

`>=`	Checks if the value of left operand is greater than or equal to the value of right operand, if yes then condition becomes true.	(A >= B) is not true.

`<=`	Checks if the value of left operand is less than or equal to the value of right operand, if yes then condition becomes true.	(A <= B) is true.

**Comparison Operators**

Comparison operators are used for comparing one expression to another. The result is always either TRUE, FALSE OR NULL.

Show Examples

LIKE Operator:

```sql
DECLARE
PROCEDURE compare (value  varchar2,  pattern varchar2 ) is
BEGIN
   IF value LIKE pattern THEN
      dbms_output.put_line ('True');
   ELSE
      dbms_output.put_line ('False');
   END IF;
END;

BEGIN
   compare('Zara Ali', 'Z%A_i');
   compare('Nuha Ali', 'Z%A_i');
END;
/
```

BETWEEN Operator:

```sql
DECLARE
   x number(2) := 10;
BEGIN
   IF (x between 5 and 20) THEN
      dbms_output.put_line('True');
   ELSE
      dbms_output.put_line('False');
   END IF;

   IF (x BETWEEN 5 AND 10) THEN
      dbms_output.put_line('True');
   ELSE
      dbms_output.put_line('False');
   END IF;

   IF (x BETWEEN 11 AND 20) THEN
      dbms_output.put_line('True');
   ELSE
      dbms_output.put_line('False');
   END IF;
END;
/
```

IN and IS NULL Operators:

```sql
DECLARE
   letter varchar2(1) := 'm';
BEGIN
   IF (letter in ('a', 'b', 'c')) THEN
      dbms_output.put_line('True');
   ELSE
      dbms_output.put_line('False');
   END IF;

   IF (letter in ('m', 'n', 'o')) THEN
       dbms_output.put_line('True');
   ELSE
      dbms_output.put_line('False');
   END IF;

   IF (letter is null) THEN
    dbms_output.put_line('True');
   ELSE
      dbms_output.put_line('False');
   END IF;
END;
/
```

Operator	Description	Example

`LIKE`	The LIKE operator compares a character, string, or CLOB value to a pattern and returns TRUE if the value matches the pattern and FALSE if it does not.	If 'Zara Ali' like 'Z% A_i' returns a Boolean true, whereas, 'Nuha Ali' like 'Z% A_i' returns a Boolean false.

BETWEEN	The BETWEEN operator tests whether a value lies in a specified range. x BETWEEN a AND b means that x >= a and x <= b.	If x = 10 then, x between 5 and 20 returns true, x between 5 and 10 returns true, but x between 11 and 20 returns false.

`IN`	The IN operator tests set membership. x IN (set) means that x is equal to any member of set.	If x = 'm' then, x in ('a', 'b', 'c') returns boolean false but x in ('m', 'n', 'o') returns Boolean true.

`IS NULL`	The IS NULL operator returns the BOOLEAN value TRUE if its operand is NULL or FALSE if it is not NULL. Comparisons involving NULL values always yield NULL.	If x = 'm', then 'x is null' returns Boolean false.

**Logical Operators**

Following table shows the Logical operators supported by PL/SQL. All these operators work on Boolean operands and produces Boolean results. Assume variable A holds true and variable B holds false, then:

Show Examples
``` sql
DECLARE
   a boolean := true;
   b boolean := false;
BEGIN
   IF (a AND b) THEN
      dbms_output.put_line('Line 1 - Condition is true');
   END IF;
   IF (a OR b) THEN
      dbms_output.put_line('Line 2 - Condition is true');
   END IF;
   IF (NOT a) THEN
      dbms_output.put_line('Line 3 - a is not true');
   ELSE
      dbms_output.put_line('Line 3 - a is true');
   END IF;
   IF (NOT b) THEN
      dbms_output.put_line('Line 4 - b is not true');
   ELSE
      dbms_output.put_line('Line 4 - b is true');
   END IF;
END;
/
```

Operator	Description	Example

`and`	Called logical AND operator. If both the operands are true then condition becomes true.	(A and B) is false.

`or`	Called logical OR Operator. If any of the two operands is true then condition becomes true.	(A or B) is true.

not	Called logical NOT Operator. Used to reverse the logical state of its operand. If a condition is true then Logical NOT operator will make it false.	not (A and B) is true.

**PL/SQL Operator Precedence**

Operator precedence determines the grouping of terms in an expression. This affects how an expression is evaluated. Certain operators have higher precedence than others; for example, the multiplication operator has higher precedence than the addition operator:

For example x = 7 + 3 * 2; here, x is assigned 13, not 20 because operator * has higher precedence than +, so it first gets multiplied with 3*2 and then adds into 7.

Here, operators with the highest precedence appear at the top of the table, those with the lowest appear at the bottom. Within an expression, higher precedence operators will be evaluated first.

Show Examples

=, <, >, <=, >=, <>, !=, ~=, ^=,

IS NULL, LIKE, BETWEEN, IN

Operator	Operation

`**`	exponentiation

`+, -`	identity, negation

`*, /`	multiplication, division

`+, -, ||`	addition, subtraction, concatenation

comparison

`NOT`	logical negation

`AND`	conjunction

`OR`	inclusion
