<!-- loio07b14e01c65a4e7b89b779defb12c97c -->

# ALTER STRUCTURED FILTER Statement \(Data Definition\)

Alter an existing a structured filter.



## Syntax

```
ALTER STRUCTURED FILTER <filter_name> FOR SELECT ON <object_name_list> <filter_condition>
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



<a name="loio07b14e01c65a4e7b89b779defb12c97c__section_ny1_w1n_zcb"/>

## Permissions

Requires one of the following:

-   You own the underlying objects of the structured filter.
-   You have the ALTER object-level privilege on the underlying objects of the structured filter.



<a name="loio07b14e01c65a4e7b89b779defb12c97c__section_wbd_hw4_21c"/>

## Examples

```
--- Setup for the following example ---
CREATE TABLE T1 (year_key nvarchar(10), year_sidE nvarchar(10), customer_sid nvarchar(10), sales int);

INSERT INTO T1 VALUES ('2007', '2007', 'CUSTOMER_A', 1000);

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

CREATE STRUCTURED FILTER SF_T2_VIEW FOR SELECT ON DYNAMIC_T1_VIEW CONDITION PROVIDER PROC_DYNAMIC_T2_VIEW;
```

This example replaces the dynamic filter condition on the structured filter SF\_T2\_VIEW with a static filter condition.

```
ALTER STRUCTURED FILTER SF_T2_VIEW FOR SELECT ON DYNAMIC_T1_VIEW WHERE year_key = '2007';
```

**Related Information**  


[CREATE STRUCTURED FILTER Statement \(Data Definition\)](create-structured-filter-statement-data-definition-f0238ff.md "Create a structured filter to manage binding between a database object (SQL or parameterized SQL view) and static / dynamic filter condition under it.")

[DROP STRUCUTRED FILTER Statement \(Data Definition\)](drop-strucutred-filter-statement-data-definition-897bc02.md "Drop an existing structured filter.")

