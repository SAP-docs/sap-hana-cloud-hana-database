<!-- loio20fbadb2751910148b24d8d93aff01d4 -->

# RENAME TABLE Statement \(Data Definition\)

Changes the schema and/or the name of a table.



<a name="loio20fbadb2751910148b24d8d93aff01d4__sql_rename_table_1sql_rename_table_syntax"/>

## Syntax

```
RENAME TABLE <current_table_name> TO <new_table_name>
```



<a name="loio20fbadb2751910148b24d8d93aff01d4__sql_rename_table_1sql_rename_table_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<current\_table\_name\>*

</b></dt>
<dd>

Specifies the current name of the table, with optional schema name.

```
<current_table_name> ::= [<schema_name>.]<identifier>
```



</dd><dt><b>

*<new\_table\_name\>*

</b></dt>
<dd>

Specifies a new table name and/or schema for *<current\_table\_name\>*.

```
<new_table_name> ::= [<schema_name>.]<identifier> 
```

If a table with the same name as *<new\_table\_name\>* already exists in *<schema\_name\>*, or if *<schema\_name\>* doesn't exist, an error is returned.



</dd>
</dl>



<a name="loio20fbadb2751910148b24d8d93aff01d4__sql_rename_table_1sql_rename_table_description"/>

## Description

The RENAME TABLE statement changes the schema and/or the name of a table.

> ### Note:  
> If the table is referenced in an audit policy, a new audit policy must be created and the old one deleted, or the existing audit policy must be updated for the renamed table. It is recommended not to mix objects from different schemas in the same audit policy.
> 
> > ### Note:  
> > Renaming column tables with the NO LOGGING option enabled is currently not supported.



<a name="loio20fbadb2751910148b24d8d93aff01d4__sql_rename_table_1sql_rename_table_examples"/>

## Example

**Example 1 - Renaming a table in the current schema**

Create table A in the current schema.

```
CREATE COLUMN TABLE A (A INT PRIMARY KEY, B INT);
```

Show a list of table names in the current schema.

```
SELECT TABLE_NAME FROM TABLES WHERE SCHEMA_NAME = CURRENT_SCHEMA ORDER BY TABLE_NAME;
```


<table>
<tr>
<th valign="top">

TABLE\_NAME



</th>
</tr>
<tr>
<td valign="top">

A



</td>
</tr>
<tr>
<td valign="top">

...



</td>
</tr>
</table>

Rename table A to a new name B.

```
RENAME TABLE A TO B;
```

Show a list of table names in current schema after the renaming process.

```
SELECT TABLE_NAME FROM TABLES WHERE SCHEMA_NAME = CURRENT_SCHEMA ORDER BY TABLE_NAME;
```


<table>
<tr>
<th valign="top">

TABLE\_NAME



</th>
</tr>
<tr>
<td valign="top">

B



</td>
</tr>
<tr>
<td valign="top">

...



</td>
</tr>
</table>

**Example 2 - Renaming a table in another schema**

Create schema mySchema and then create a table A in the new schema.

```
CREATE SCHEMA mySchema;
 CREATE COLUMN TABLE mySchema.A (A INT PRIMARY KEY, B INT);
```

Show the list of table names in schema mySchema.

```
SELECT TABLE_NAME FROM TABLES WHERE SCHEMA_NAME = 'MYSCHEMA' ORDER BY TABLE_NAME;
```


<table>
<tr>
<th valign="top">

TABLE\_NAME



</th>
</tr>
<tr>
<td valign="top">

A



</td>
</tr>
</table>

Rename table A in mySchema to B.

```
RENAME TABLE mySchema.A TO B;
```

Show a list of table names in schema mySchema after the renaming process.

```
SELECT TABLE_NAME FROM TABLES WHERE SCHEMA_NAME = 'MYSCHEMA' ORDER BY TABLE_NAME;
```


<table>
<tr>
<th valign="top">

TABLE\_NAME



</th>
</tr>
<tr>
<td valign="top">

B



</td>
</tr>
</table>

**Example 3 - Change the schema of the table**

Create schema mySchema2.

```
CREATE SCHEMA mySchema2;
```

Change the schema of table B from mySchema to mySchema2.

```
RENAME TABLE mySchema.B TO mySchema2.B;
```

Show a list of table names in the schema mySchema2.

```
SELECT TABLE_NAME FROM TABLES WHERE SCHEMA_NAME = 'MYSCHEMA2' ORDER BY TABLE_NAME;
```


<table>
<tr>
<th valign="top">

TABLE\_NAME



</th>
</tr>
<tr>
<td valign="top">

B



</td>
</tr>
</table>

