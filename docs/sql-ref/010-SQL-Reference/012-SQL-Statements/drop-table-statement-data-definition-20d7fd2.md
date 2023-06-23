<!-- loio20d7fd287519101480afbce1b997e4b9 -->

# DROP TABLE Statement \(Data Definition\)

Removes a physical or virtual table from the database.



<a name="loio20d7fd287519101480afbce1b997e4b9__sql_drop_table_1sql_drop_table_syntax"/>

## Syntax

```
DROP TABLE <table_name> [<drop_option>] [ WITH REMOTE ]
```



<a name="loio20d7fd287519101480afbce1b997e4b9__sql_drop_table_1sql_drop_table_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

Drops the specified table with the optional schema name.

```
<table_name> ::= [ [ <database_name>.]<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

*<drop\_option\>*

</b></dt>
<dd>

Specifies the drop option to use.

```
<drop_option> ::= CASCADE | RESTRICT
```

CASCADE drops the table and dependent objects. RESTRICT drops the table only when dependent objects do not exist. If this drop option is used and a dependent object exists, then an error is thrown.

If *<drop\_option\>* is not specified, then a non-cascaded drop is performed which only drops the specified table. Dependent objects of the table are invalidated but not dropped.

The invalidated objects can be re-validated when an object that has same schema and object name is created.



</dd><dt><b>

WITH REMOTE

</b></dt>
<dd>

Drops the virtual table from the local source and the corresponding table on the remote source. This option is only supported for virtual tables. The WITH REMOTE option is supported for remote sources using the following SDA adapters: hanaodbc, iqodbc, aseodbc, tdodbc, voraodbc, odbc \(Oracle, Microsoft SQL Server, IBM Netezza, IBM DB2, BigQuery, PostgreSQL\). It is not supported with an SDI adapter.



</dd>
</dl>



<a name="loio20d7fd287519101480afbce1b997e4b9__sql_drop_table_1sql_drop_table_description"/>

## Description

The DROP TABLE statement removes a physical or virtual table from the database.



<a name="loio20d7fd287519101480afbce1b997e4b9__section_opr_ddt_5cb"/>

## Permissions

This statement requires the DROP object privilege on the table.

Use of the WITH REMOTE option also requires the REMOTE TABLE ADMIN object privilege.

When using the WITH REMOTE option, if the credential type of the remote source is PASSWORD, then only the owner of the remote sources who set the technical user credentials has the authorization to use the option. For all other credential types, authorization is a function of the privileges of the user on the remote source.



<a name="loio20d7fd287519101480afbce1b997e4b9__sql_drop_table_1sql_drop_table_examples"/>

## Example

Drop table A and all its dependent objects.

```
DROP TABLE A;
```

**Related Information**  


[TABLES System View](../../020-System-Views-Reference/021-System-Views/tables-system-view-2101973.md "Provides information about tables in the database.")

[TABLE\_COLUMNS System View](../../020-System-Views-Reference/021-System-Views/table-columns-system-view-2100d33.md "Provides information about available table columns.")

