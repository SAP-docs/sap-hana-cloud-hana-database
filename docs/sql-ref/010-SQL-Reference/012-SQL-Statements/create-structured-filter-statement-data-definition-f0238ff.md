<!-- loiof0238ff8445342a8a9a2f9c3dd36631e -->

# CREATE STRUCTURED FILTER Statement \(Data Definition\)

Create a structured filter to manage binding between a database object \(SQL or parameterized SQL view\) and static / dynamic filter condition under it.



## Syntax

```
CREATE STRUCTURED FILTER <filter_name> FOR SELECT ON <object_name_list> <filter_condition>
```



## Syntax Elements


<dl>
<dt><b>

*<filter\_name\>*

</b></dt>
<dd>

Specifies the name of the structured filter.

```
<filter_name> ::= [ <schema_name>.]<identifier>
```



</dd><dt><b>

*<object\_name\_list\>*

</b></dt>
<dd>

Specifies the list of objects defined for the structured filter.

```
<object_name_list> ::= <object_name> [ , <object_name>...]

<object_name> :: = [ <schema>.]<identifier>
```



</dd><dt><b>

*<filter\_condition\>*

</b></dt>
<dd>

Specifies the conditions of the structured filter.

```
<filter_condition> ::= 
   { <static_filter_condition> | <dynamic_filter_condition> }
```


<dl>
<dt><b>

*<static\_filter\_condition\>*

</b></dt>
<dd>

Specifies the WHERE clause of the condition.

```
<static_filter_condition> ::= WHERE condition
```



</dd><dt><b>

*<dynamic\_filter\_condition\>*

</b></dt>
<dd>

Specifies the CONDITION PROVIDER of the condition.

```
<dynamic_filter_condition> ::= CONDITION PROVIDER [ <schema_name>.]<identifier>
```



</dd>
</dl>



</dd>
</dl>



## Description

Once an object has a structured filter enabled, subsequent queries on the object are immediately impacted and governed by the structured filter \(if any\).

A structured filter can only be defined on an object with structured filter explicitly enabled.



<a name="loiof0238ff8445342a8a9a2f9c3dd36631e__section_ny1_w1n_zcb"/>

## Permissions

Requires one of the following:

-   You own the underlying objects of the structured filter.
-   You have the ALTER object-level privilege on the underlying objects of the structured filter.



<a name="loiof0238ff8445342a8a9a2f9c3dd36631e__section_i4j_dj4_21c"/>

## Examples

The following example applies to a SQL view:

```
--- Setup for the following example ---
CREATE TABLE T1 (year_key nvarchar(10), year_sidE nvarchar(10), customer_sid nvarchar(10), sales int);

CREATE VIEW "DYNAMIC_T1_VIEW" AS (SELECT * FROM T1) WITH STRUCTURED FILTER CHECK;
 
CREATE COLUMN TABLE T2 ("filter_string" varchar(5000), "userName" varchar(256));

CREATE PROCEDURE PROC_DYNAMIC_T2_VIEW (OUT VAL VARCHAR(5000))
                        LANGUAGE SQLSCRIPT SQL SECURITY DEFINER READS SQL DATA AS
                        BEGIN
                            DECLARE v_Val VARCHAR(5000);
                            DECLARE CURSOR c_GetOneOperand FOR
                                SELECT "filter_string" FROM T2 WHERE "userName" = SESSION_USER;
                            OPEN c_GetOneOperand;
                            FETCH c_GetOneOperand INTO v_Val;
                            IF c_GetOneOperand::NOTFOUND THEN
                                VAL  = NULL;
                            ELSE
                                VAL  = v_Val;
                            END IF;
                            CLOSE c_GetOneOperand;
                        END;
```

This syntax creates structured filter SF\_T2\_VIEW that references the DYNAMIC\_T1\_VIEW view and uses a dynamic filter condition.

```
CREATE STRUCTURED FILTER SF_T2_VIEW FOR SELECT ON DYNAMIC_T1_VIEW CONDITION PROVIDER PROC_DYNAMIC_T2_VIEW;
```

This example applies to a parameterized SQL view:

```
--- Setup for the following example ---
CREATE SCHEMA SC1;

CREATE OR REPLACE VIEW SC1.MYVIEW(IN OUTVAL INT default 1) AS 
   SELECT 1 + :OUTVAL AS PARAMCOL, 1 AS FIXEDCOL FROM DUMMY WITH STRUCTURED FILTER CHECK;

```

This syntax creates a structured filter using the column PARAMCOL where it is \> 0:

```
CREATE STRUCTURED FILTER SC1.MY_SF FOR SELECT ON SC1.MYVIEW WHERE "PARAMCOL" > 0;
```

**Related Information**  


[ALTER STRUCTURED FILTER Statement \(Data Definition\)](alter-structured-filter-statement-data-definition-07b14e0.md "Alter an existing a structured filter.")

[DROP STRUCUTRED FILTER Statement \(Data Definition\)](drop-strucutred-filter-statement-data-definition-897bc02.md "Drop an existing structured filter.")

