**PL/SQL - Data Types**

PL/SQL variables, constants and parameters must have a valid data type, which specifies a storage format, constraints, and valid range of values. This tutorial will take you through SCALAR and LOB data types available in PL/SQL and other two data types will be covered in other chapters.

Category	   Description
Scalar	     Single values with no internal components, such as a NUMBER, DATE, or BOOLEAN.
Large Object (LOB)	Pointers to large objects that are stored separately from other data items, such as text, graphic images, video clips, and sound waveforms.
Composite	   Data items that have internal components that can be accessed individually. For example, collections and records.
Reference	   Pointers to other data items.

**PL/SQL Scalar Data Types and Subtypes**

PL/SQL Scalar Data Types and Subtypes come under the following categories:
```
Date Type Description
Numeric   Numeric values on which arithmetic operations are performed.
Character Alphanumeric values that represent single characters or strings of characters.
Boolean   Logical values on which logical operations are performed.
Datetime  Dates and times.
```

`PL/SQL` provides subtypes of data types. For example, the data type NUMBER has a subtype called INTEGER. You can use subtypes in your PL/SQL program to make the data types compatible with data types in other programs while embedding PL/SQL code in another program, such as a Java program.

**PL/SQL Numeric Data Types and Subtypes**

Following is the detail of PL/SQL pre-defined numeric data types and their sub-types:
```
Data Type             Description
PLS_INTEGER           Signed integer in range -2,147,483,648 through 2,147,483,647, represented in 32 bits
BINARY_INTEGER        Signed integer in range -2,147,483,648 through 2,147,483,647, represented in 32 bits
BINARY_FLOAT          Single-precision IEEE 754-format floating-point number
BINARY_DOUBLE         Double-precision IEEE 754-format floating-point number

NUMBER(prec, scale)   Fixed-point or floating-point number with absolute value in range 1E-130 to (but not including) 1.0E126. A NUMBER variable can also represent 0.
DEC(prec, scale)      ANSI specific fixed-point type with maximum precision of 38 decimal digits.
DECIMAL(prec, scale)	IBM specific fixed-point type with maximum precision of 38 decimal digits.
NUMERIC(pre, secale)	Floating type with maximum precision of 38 decimal digits.
DOUBLE PRECISION      ANSI specific floating-point type with maximum precision of 126 binary digits (approximately 38 decimal digits)
FLOAT	                ANSI and IBM specific floating-point type with maximum precision of 126 binary digits (approximately 38 decimal digits)
INT	                  ANSI specific integer type with maximum precision of 38 decimal digits
INTEGER	              ANSI and IBM specific integer type with maximum precision of 38 decimal digits
SMALLINT              ANSI and IBM specific integer type with maximum precision of 38 decimal digits
REAL                  Floating-point type with maximum precision of 63 binary digits (approximately 18 decimal digits)
```

Following is a valid declaration:
```SQL
DECLARE
   num1 INTEGER;
   num2 REAL;
   num3 DOUBLE PRECISION;
BEGIN
   null;
END;
/
```

When the above code is compiled and executed, it produces the following result:
```
PL/SQL procedure successfully completed
```

**PL/SQL Character Data Types and Subtypes**

Following is the detail of PL/SQL pre-defined character data types and their sub-types:
```
Data Type	Description
CHAR      Fixed-length character string with maximum size of 32,767 bytes
VARCHAR2	Variable-length character string with maximum size of 32,767 bytes
RAW	      Variable-length binary or byte string with maximum size of 32,767 bytes, not interpreted by PL/SQL
NCHAR	    Fixed-length national character string with maximum size of 32,767 bytes
NVARCHAR2	Variable-length national character string with maximum size of 32,767 bytes
LONG      Variable-length character string with maximum size of 32,760 bytes
LONG RAW	Variable-length binary or byte string with maximum size of 32,760 bytes, not interpreted by PL/SQL
ROWID     Physical row identifier, the address of a row in an ordinary table
UROWID    Universal row identifier (physical, logical, or foreign row identifier)
```

**PL/SQL Boolean Data Types**

The BOOLEAN data type stores logical values that are used in logical operations. The logical values are the Boolean values TRUE and FALSE and the value NULL.

However, SQL has no data type equivalent to BOOLEAN. Therefore, Boolean values cannot be used in:

* SQL statements
* Built-in SQL functions (such as TO_CHAR)
* PL/SQL functions invoked from SQL statements

**PL/SQL Datetime and Interval Types**

The DATE datatype to store fixed-length datetimes, which include the time of day in seconds since midnight. Valid dates range from January 1, 4712 BC to December 31, 9999 AD.

The default date format is set by the Oracle initialization parameter NLS_DATE_FORMAT. For example, the default might be 'DD-MON-YY', which includes a two-digit number for the day of the month, an abbreviation of the month name, and the last two digits of the year, for example, 01-OCT-12.

Each DATE includes the century, year, month, day, hour, minute, and second. The following table shows the valid values for each field:
```
Field Name      Valid Datetime Values	Valid Interval Values
YEAR            -4712 to 9999 (excluding year 0)	Any nonzero integer
MONTH	          01 to 12	0 to 11
DAY	            01 to 31 (limited by the values of MONTH and YEAR, according to the rules of the calendar for the locale)	Any nonzero integer
HOUR            00 to 23	0 to 23
MINUTE          00 to 59	0 to 59
SECOND          00 to 59.9(n), where 9(n) is the precision of time fractional seconds	0 to 59.9(n), where 9(n) is the precision of interval fractional seconds
TIMEZONE_HOUR   -12 to 14 (range accommodates daylight savings time changes)	Not applicable
TIMEZONE_MINUTE 00 to 59	Not applicable
TIMEZONE_REGION	Found in the dynamic performance view V$TIMEZONE_NAMES	Not applicable
TIMEZONE_ABBR	  Found in the dynamic performance view V$TIMEZONE_NAMES	Not applicable
```

**PL/SQL Large Object (LOB) Data Types**

Large object (LOB) data types refer large to data items such as text, graphic images, video clips, and sound waveforms. LOB data types allow efficient, random, piecewise access to this data. Following are the predefined PL/SQL LOB data types:
```
Data Type	Description	Size**
BFILE     Used to store large binary objects in operating system files outside the database.	System-dependent. Cannot exceed 4 gigabytes (GB).
BLOB      Used to store large binary objects in the database.	8 to 128 terabytes (TB)
CLOB      Used to store large blocks of character data in the database.	8 to 128 TB
NCLOB     Used to store large blocks of NCHAR data in the database.	8 to 128 TB
```

**PL/SQL User-Defined Subtypes**

A subtype is a subset of another data type, which is called its base type. A subtype has the same valid operations as its base type, but only a subset of its valid values.

PL/SQL predefines several subtypes in package STANDARD. For example, PL/SQL predefines the subtypes CHARACTER and INTEGER as follows:
```
SUBTYPE CHARACTER IS CHAR;
SUBTYPE INTEGER IS NUMBER(38,0);
```

You can define and use your own subtypes. The following program illustrates defining and using a user-defined subtype:
```SQL
DECLARE
   SUBTYPE name IS char(20);
   SUBTYPE message IS varchar2(100);
   salutation name;
   greetings message;
BEGIN
   salutation := 'Reader ';
   greetings := 'Welcome to the World of PL/SQL';
   dbms_output.put_line('Hello ' || salutation || greetings);
END;
/
```

When the above code is executed at SQL prompt, it produces the following result:
```
Hello Reader Welcome to the World of PL/SQL
PL/SQL procedure successfully completed.
```

**NULLs in PL/SQL**

PL/SQL NULL values represent missing or unknown data and they are not an integer, a character, or any other specific data type. Note that NULL is not the same as an empty data string or the null character value '\0'. A null can be assigned but it cannot be equated with anything, including itself.
