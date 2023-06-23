<!-- loio20f83c8c75191014b215d6c8c427c91b -->

# LOAD Statement \(Data Manipulation\)

Explicitly loads column store table data into memory instead of upon first access.



<a name="loio20f83c8c75191014b215d6c8c427c91b__sql_load_1sql_load_syntax"/>

## Syntax

```
LOAD <table_name>
   { DELTA
     | ALL
     | (<column_name>, ...)
   }
```



<a name="loio20f83c8c75191014b215d6c8c427c91b__sql_unload_1sql_load_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

Specifies the name of the table to be loaded into memory, with optional schema name.

```
<table_name> ::= [<schema_name>.]<identifier>
 
<schema_name> ::= <unicode_name>
```



</dd><dt><b>

DELTA

</b></dt>
<dd>

Specifies that the delta part of a column store table is loaded into memory. As the column store is read, optimized, and compressed, deltas are used to optimize insert or update operations.



</dd><dt><b>

ALL

</b></dt>
<dd>

Specifies that all current data of the column store table, including its delta, is loaded into memory.



</dd><dt><b>

*<column\_name\>*

</b></dt>
<dd>

Specifies the name of the column to be loaded into memory.

```
<column_name> ::= <identifier>
```



</dd>
</dl>



<a name="loio20f83c8c75191014b215d6c8c427c91b__sql_load_1sql_load_description"/>

## Description

The LOAD statement explicitly loads column store table data into memory instead of upon first access.

The use of this statement requires the UPDATE privilege.



<a name="loio20f83c8c75191014b215d6c8c427c91b__sql_load_1sql_load_examples"/>

## Examples

Create column table A.

```
CREATE COLUMN TABLE A (A INT, B INT);
```

Load table A into memory.

```
LOAD A all;
```

Load the columns A and B of table A into memory.

```
LOAD A (A,B);
```

Query the load status of table A using the m\_cs\_tables monitoring view.

```
SELECT loaded FROM m_cs_tables WHERE table_name = 'A';
```

**Related Information**  


[M\_CS\_TABLES System View](../../020-System-Views-Reference/022-Monitoring-Views/m-cs-tables-system-view-20ad60f.md "Provides runtime data for column tables.")

