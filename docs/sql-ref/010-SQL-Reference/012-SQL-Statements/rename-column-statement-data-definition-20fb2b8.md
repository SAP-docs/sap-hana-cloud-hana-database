<!-- loio20fb2b8b7519101499d2c6bd37c81b32 -->

# RENAME COLUMN Statement \(Data Definition\)

Changes the name of a column.



<a name="loio20fb2b8b7519101499d2c6bd37c81b32__sql_rename_column_1sql_rename_column_syntax"/>

## Syntax

```
RENAME COLUMN <table_name>.<old_column_name> TO <new_column_name>
```



<a name="loio20fb2b8b7519101499d2c6bd37c81b32__sql_rename_column_1sql_rename_column_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

Specifies the name of the table where the column is to be renamed.

```
<table_name> ::= <identifier>
```



</dd><dt><b>

*<old\_column\_name\>*

</b></dt>
<dd>

Specifies the old column name.

```
<old_column_name> ::= <identifier>
```



</dd><dt><b>

*<new\_column\_name\>*

</b></dt>
<dd>

Specifies the new column name.

```
<new_column_name> ::= <identifier>
```



</dd>
</dl>



<a name="loio20fb2b8b7519101499d2c6bd37c81b32__sql_rename_column_1sql_rename_column_description"/>

## Description

Changes the name of a column.



<a name="loio20fb2b8b7519101499d2c6bd37c81b32__sql_rename_column_1sql_rename_column_examples"/>

## Example

Create table tab with two columns named A and B.

```
CREATE ROW TABLE tab (A INT PRIMARY KEY, B INT);
```

Display the column names for table tab stored in the SAP HANA database.

```
SELECT COLUMN_NAME, POSITION FROM TABLE_COLUMNS WHERE SCHEMA_NAME = CURRENT_SCHEMA AND TABLE_NAME = 'tab' ORDER BY POSITION;
```

Rename column A to C.

```
RENAME COLUMN tab.A TO C;
```

Display the column names for table tab after the renaming.

```
SELECT COLUMN_NAME, POSITION FROM TABLE_COLUMNS WHERE SCHEMA_NAME = CURRENT_SCHEMA AND TABLE_NAME = 'tab' ORDER BY POSITION;
```

**Related Information**  


[Introduction to SQL](../introduction-to-sql-209f502.md "This chapter describes the SAP HANA database implementation of Structured Query Language (SQL).")

