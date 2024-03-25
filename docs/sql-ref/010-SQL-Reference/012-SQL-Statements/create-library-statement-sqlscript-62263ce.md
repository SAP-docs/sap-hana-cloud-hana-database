<!-- loio62263ce35ac74488a397553fcb25a7d6 -->

# CREATE LIBRARY Statement \(SQLScript\)

Creates a SQLScript user-defined library.



<a name="loio62263ce35ac74488a397553fcb25a7d6__section_wtr_2lf_scb"/>

## Syntax

```
CREATE [ OR REPLACE ] LIBRARY [ <schema_name>.]<library_name>
 [ LANGUAGE { SQLSCRIPT | SQLSCRIPT TEST } ] 
 AS BEGIN
   <sqlscript_user_defined_library_spec> 
 END;
```



<a name="loio62263ce35ac74488a397553fcb25a7d6__section_hcs_2lf_scb"/>

## Syntax Elements


<dl>
<dt><b>

OR REPLACE

</b></dt>
<dd>

Specifying OR REPLACE replaces the existing library, if one exists, with the new definition.



</dd><dt><b>

*<library\_name\>*

</b></dt>
<dd>

Specifies a name for the new SQLScript user-defined library.



</dd><dt><b>

LANGUAGE

</b></dt>
<dd>

Specifies the type of library:


<dl>
<dt><b>

SQLSCRIPT

</b></dt>
<dd>

Specifies that the library will be a SQLScript library.



</dd><dt><b>

SQLSCRIPT TEST

</b></dt>
<dd>

Specifies that the library will be a SQLScript end-user test framework.



</dd>
</dl>



</dd><dt><b>

*<sqlscript\_user\_defined\_library\_spec\>*

</b></dt>
<dd>

Specifies the body of the new SQLScript user-defined library.

See the *SAP HANA Cloud, SAP HANA Database SQLScript Reference* for the syntax allowed in a SQLScript library.



</dd>
</dl>



<a name="loio62263ce35ac74488a397553fcb25a7d6__section_cks_2lf_scb"/>

## Description

Use this statement to define a SQLScript library in an SAP HANA database.

A SQLScript user-defined library is a library written in the SQLScript language that can be called by other procedures or functions. A SQLScript library can only be used by SQLScript procedures or functions; it is not available for use in other SQL statements.



## Examples

The following example statements create a table, a SQLScript user-defined library that operates on the table, and a procedure that calls the new library.

```
CREATE TABLE data_table(col1 INT);
 DO BEGIN
  DECLARE idx INT = 0;
  FOR idx IN 1..200 DO
    INSERT INTO data_table VALUES (:idx);
  END FOR;
 END;

CREATE OR REPLACE LIBRARY mylib AS BEGIN
  PUBLIC VARIABLE maxval CONSTANT INT = 100;
  PUBLIC FUNCTION bound_with_maxval(i INT) RETURNS x INT AS BEGIN
    x = CASE WHEN :i > :maxval THEN :maxval ELSE :i END;
  END;
  PUBLIC PROCEDURE get_data(IN size INT, OUT result table(col1 INT)) AS BEGIN
    RESULT = SELECT TOP :size col1 FROM data_table;
  END;
END;

CREATE PROCEDURE myproc (IN inval INT) AS BEGIN
  USING mylib AS mylib;
  DECLARE var1 INT = mylib:bound_with_maxval(:inval);
  IF :var1 > mylib:maxval THEN
    SELECT 'unexpected' FROM dummy;
  ELSE
    DECLARE tv table (col1 INT);
    CALL mylib:get_data(:var1, tv);
    SELECT COUNT(*) FROM :tv;
  END IF;
END;

CALL myproc(10);  - returns the value 10
CALL myproc(150);  – returns the value 100
```

**Related Information**  


[User-Defined Libraries](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/7cd14f1931404738a05c5e93e22564af.html "") :arrow_upper_right:

[SAP HANA Cloud, SAP HANA SQLScript Reference](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/28f2d64d4fab4e789ee0070be418419d.html "This reference describes how to use the SQL extension SAP HANA SQLScript to embed data-intensive application logic into SAP HANA.") :arrow_upper_right:

[DROP LIBRARY Statement \(SQLScript\)](drop-library-statement-sqlscript-d416079.md "Drops a SQLScript user-defined library.")

[ALTER LIBRARY Statement \(SQLScript\)](alter-library-statement-sqlscript-d0b979c.md "Alters a SQLScript user-defined library.")

[LIBRARIES System View](../../020-System-Views-Reference/021-System-Views/libraries-system-view-7e48a10.md "Provides information about available public language libraries.")

[LIBRARY\_MEMBERS System View](../../020-System-Views-Reference/021-System-Views/library-members-system-view-215c8db.md "Provides member information for SQLScript user-defined libraries.")

[End-User Test Framework in SQLScript](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/1386a5eb77444ca8ba3a050c4043f1f8.html "") :arrow_upper_right:

