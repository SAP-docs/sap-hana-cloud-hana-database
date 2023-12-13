<!-- loiod2a0406155f24a49aa6c549e0c428bd7 -->

# CREATE VIRTUAL TABLE Statement \(Data Definition\)

Creates a virtual table at a remote source.



## Syntax

Syntax 1 - Create a virtual table.

```
CREATE VIRTUAL TABLE <virtual_table_name> 
    AT <remote_location_clause> [ <remote_property_clause> ]
```

Syntax 2 - Create a remote table while creating a virtual table.

```
CREATE VIRTUAL TABLE <virtual_table_name> <table_contents_source> 
    AT <remote_location_clause> WITH REMOTE 
```



## Syntax Elements


<dl>
<dt><b>

*<virtual\_table\_name\>*

</b></dt>
<dd>

Specifies a unique name for the virtual table.

```
<virtual_table_name> ::= [ <schema_name>.]<identifier>
```



</dd><dt><b>

*<table\_contents\_source\>*

</b></dt>
<dd>

Specifies the source from which the table definition is derived.

```
<table_contents_source> ::= ( <table_element> [, <table_element> [, ... ] ] )
```


<dl>
<dt><b>

*<table\_element\>*

</b></dt>
<dd>

Defines the table columns with associated column or table constraints.

```
<table_element> ::=
 <column_definition> [ <column_constraint> ]
```



</dd><dt><b>

*<column\_definition\>*

</b></dt>
<dd>

Defines a table column.

```
<column_definition> ::= <column_name> <data_type> [ <default_value_clause> ]
```


<dl>
<dt><b>

*<column\_name\>*

</b></dt>
<dd>

Specifies the column name.

```
<column_name> ::= <identifier>
```



</dd><dt><b>

*<data\_type\>*

</b></dt>
<dd>

Specifies the column data types.

```
<data_type> ::=
 DATE 
 | TIME 
 | SECONDDATE 
 | TIMESTAMP 
 | TINYINT 
 | SMALLINT 
 | INTEGER 
 | BIGINT 
 | SMALLDECIMAL 
 | REAL 
 | DOUBLE  
 | VARCHAR [ (<unsigned_integer>) ]
 | NVARCHAR [ (<unsigned_integer>) ] 
 | VARBINARY [ (<unsigned_integer>) ] 
 | DECIMAL [ (<unsigned_integer> [, <unsigned_integer> ]) ] 
 | FLOAT [ (<unsigned_integer>) ] 
 | BOOLEAN
```



</dd><dt><b>

*<default\_value\_clause\>*

</b></dt>
<dd>

Specifies a value to be assigned to the column if an INSERT statement does not provide a value for the column.

```
<default_value_clause> ::= DEFAULT <default_value_exp>

<default_value_exp> ::= 
 NULL 
 | <string_literal>
 | <signed_numeric_literal> <unsigned_numeric_literal> 
 | <datetime_value_function>

<datetime_value_function> ::= 
 CURRENT_DATE 
 | CURRENT_TIME 
 | CURRENT_TIMESTAMP 
 | CURRENT_UTCDATE 
 | CURRENT_UTCTIME 
 | CURRENT_UTCTIMESTAMP
```



</dd>
</dl>



</dd><dt><b>

*<column\_constraint\>*

</b></dt>
<dd>

Specifies the column constraint rules.

```
<column_constraint> ::= NULL | NOT NULL | <unique_specification>
```


<dl>
<dt><b>

NULL

</b></dt>
<dd>

Allows NULL values in the column. If NULL is specified it is not considered a constraint, it represents that a column that may contain a null value. The default is NULL.



</dd><dt><b>

NOT NULL

</b></dt>
<dd>

Prohibits NULL values in the column.



</dd><dt><b>

*<unique\_specification\>*

</b></dt>
<dd>

Specifies unique constraints.

```
<unique_specification> ::= UNIQUE | PRIMARY KEY
```


<dl>
<dt><b>

UNIQUE

</b></dt>
<dd>

Specifies a column as a unique key. A composite unique key enables the specification of multiple columns as a unique key. With a unique constraint, multiple rows cannot have the same value in the same column.

A UNIQUE column can contain multiple NULL values.



</dd><dt><b>

PRIMARY KEY

</b></dt>
<dd>

Specifies a primary key constraint, which is a combination of a NOT NULL constraint and a UNIQUE constraint.



</dd>
</dl>



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<remote\_location\_clause\>*

</b></dt>
<dd>

Identifies a remote object \(table or view\) at an existing remote source.

```
<remote_location_clause> ::= 
"<remote_source_name>"."<database_name>"."<schema_name>"."<identifier>"

```

For SAP HANA, SAP IQ, SAP MaxDB, Terradata, and IBM DB2 remote sources, you can use NULL for *<database\_name\>*.



</dd><dt><b>

*<remote\_property\_clause\>*

</b></dt>
<dd>

Specifies the parameters and their values to be set for the virtual table as XML.

```
<remote_property_clause> ::= 
 [REMOTE PROPERTY 'dataprovisioning_parameters'=<dataprov_params_value>]

<dataprov_params_value> ::= <string_literal>
```

The REMOTE PROPERTY clause allows you to specify data provisioning parameters for the virtual table that is being created. The parameters list is sent to the adapter as a parameter for the remote object metadata request.



</dd><dt><b>

WITH REMOTE

</b></dt>
<dd>

Creates a table on the remote source using the *<table\_contents\_source\>* definition and a corresponding virtual table on the local source. The WITH REMOTE option is supported for remote sources using the following SDA adapters: hanaodbc, iqodbc, aseodbc, tdodbc, voraodbc, odbc \(Oracle, Microsoft SQL Server, IBM Netezza, IBM DB2, BigQuery\). It is also supported for SAP HANA Cloud data lake. It is not supported with an SDI adapter.



</dd>
</dl>



## Description

The CREATE VIRTUAL TABLE provides a way to access an existing table or a view on a remote source from an SAP HANA instance. The list of remote columns is automatically imported into the virtual table.

Use the DROP TABLE *<table\_name\>* to drop a virtual table.

> ### Note:  
> The relationship between a virtual table and the remote object it points to can be considered as relatively shallow. In other words, while the virtual table can access and retrieve data from the remote object, it does not inherently reflect the complex relationships that the remote object may have with other entities. For instance, associations the remote object maintains with other remote objects are not automatically mirrored in the virtual table.



<a name="loiod2a0406155f24a49aa6c549e0c428bd7__section_opr_ddt_5cb"/>

## Permissions

Syntax 1 - This syntax requires the CREATE VIRTUAL TABLE object privilege.

Syntax 2 - This syntax requires the CREATE VIRTUAL TABLE and REMOTE TABLE ADMIN object privileges. If the credential type of the remote source is PASSWORD, then only the owner of the remote sources who set the technical user credentials has the authorization to use the WITH REMOTE clause. To remove this restriction, use the ALTER REMOTE SOURCE statement to set the property CAP\_REMOTE\_TABLE\_ADMIN\_TECHUSER\_NO\_OWNERSHIP to true. For all other credential types, authorization is a function of the privileges of the user on the remote source.



## Examples

Create virtual table `VT` on existing remote source `S`. The originating table is `tableA`, which is within the schema `SYSTEM` on `HA1`.

```
CREATE VIRTUAL TABLE VT AT "S"."HA1"."SYSTEM"."tableA";
```

Create a virtual table where the following string is sent to the adapter as a parameter for the metadata request: `<Parameter name="objects">1,10,1000,300</Parameter><Parameter name="stateHierarchy">USA</Parameter><Parameter name="date”>2014-06-01</Parameter>`

```
CREATE VIRTUAL TABLE …. 
   REMOTE PROPERTY 'dataprovisioning_parameters'='<Parameter name="objects">1,10,1000,300</Parameter>
   <Parameter name="stateHierarchy">USA</Parameter><Parameter name="date">2014-06-01</Parameter>';
```

Create table A1 on remote source Remote1 and create a corresponding virtual table virtual\_A1 in the local source.

```
CREATE VIRTUAL TABLE virtual_A1 (a int, b int) at "Remote1"."HA1"."SYSTEM"."A1" WITH REMOTE;
```

**Related Information**  


[Introduction to SQL](../introduction-to-sql-209f502.md "This chapter describes the SAP HANA database implementation of Structured Query Language (SQL).")

