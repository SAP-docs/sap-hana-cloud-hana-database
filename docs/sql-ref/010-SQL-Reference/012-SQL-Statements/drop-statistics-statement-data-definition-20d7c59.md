<!-- loio20d7c595751910148307bf3bf4c745e6 -->

# DROP STATISTICS Statement \(Data Definition\)

Drops user-defined data statistic objects that the query optimizer uses to make decisions for query plans.



<a name="loio20d7c595751910148307bf3bf4c745e6__sql_drop_statistics_1sql_drop_statistics_syntax"/>

## Syntax

```
DROP STATISTICS { <data_statistics_name>[.<data_statistics_name>[,...] ]
   | ON <data_sources> [ [HAVING] <match_properties> ] };
```



<a name="loio20d7c595751910148307bf3bf4c745e6__sql_drop_statistics_1sql_drop_statistics_syntax_element"/>

## Syntax Element


<dl>
<dt><b>

*<data\_statistics\_name\>*

</b></dt>
<dd>

Specifies the name of the data statistics object.

```
<data_statistics_name> ::= [<schema_name>.]<identifier>

<schema_name> ::= <identifier>
```



</dd><dt><b>

*<data\_sources\>*

</b></dt>
<dd>

Specifies the data source\(s\) of the data statistics objects.

```
<data_sources> ::= 
<table_name> [ ( <column_name>[, <column_name>[,...] ] ) [ <match_type> ]
```


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

Specifies the table name you want to create statistics on.

```
<table_name> ::= [ [ <database_name>.]<schema_name>.]<identifier>
```

For linked databases, *<database\_name\>* is the name of the remote source. For all other cases, *<database\_name\>* is the name of the database where the table is located.



</dd><dt><b>

*<column\_name\>*

</b></dt>
<dd>

Specifies the column for which the data statistics are defined.

```
<column_name> ::= <identifier>
```

If no *<column\_name\>* is specified, then all statistics for the table that match the specified properties are altered, including table-wide statistics \(RECORD COUNT\).



</dd><dt><b>

*<match\_type\>*

</b></dt>
<dd>

Controls which data statistics objects to match to *<data\_sources\>*.

```
<match_type> ::= EXACT | CASCADE 
```

If *<match\_type\>* is not specified, then any data statistics object\(s\) that reference all or some of the columns, but no other columns specified in *<data\_sources\>* are refreshed.

Specify EXACT to refresh data statistics objects that precisely match *<data\_sources\>* \(including column order\).

Specify CASCADE to refresh data statistics objects that reference at least one column in *<data\_sources\>*.

Use this table to understand how matching is performed based on *<match\_type\>* when *<data\_sources\>* is T\(A, B, C\):


<table>
<tr>
<th valign="top">

Match type

</th>
<th valign="top">

Example matches

</th>
<th valign="top">

Example non-matches

</th>
</tr>
<tr>
<td valign="top">

\(not specified\)

</td>
<td valign="top">

T\(A,C\)

T\(C\)

T\(B,A\)

</td>
<td valign="top">

T\(A,X\) - because T\(X\) is not a column in *<data\_sources\>*.

</td>
</tr>
<tr>
<td valign="top">

EXACT

</td>
<td valign="top">

T\(A,B,C\)

</td>
<td valign="top">

T\(B,A,C\) - because the column order is different than the column order of *<data\_sources\>*.

T\(A\)- because it does not contain the exact same columns and column order of *<data\_sources\>*.

T\(X,A,B,C\) - because T.\(X\) is not a column in *<data\_sources\>*.

</td>
</tr>
<tr>
<td valign="top">

CASCADE

</td>
<td valign="top">

T\(A,C\)

T\(C\)

T\(B,A\)

T\(A,B,C\)

T\(A,X\)

T\(B,C\)

T\(A\)

T\(C,B,A,X\)

</td>
<td valign="top">

T\(X\) - because it does not contain any columns that match the columns in *<data\_sources\>*.

</td>
</tr>
</table>



</dd>
</dl>



</dd><dt><b>

*<match\_properties\>*

</b></dt>
<dd>

Specifies properties to use for matching when selecting data statistics.

```
<match_properties> ::= <match_property>[...] 

<match_property> ::=
 TYPE <data_statistics_type>  | REFRESH TYPE <refresh_type_filter>
```

If TYPE is not specified, then all data statistics objects of any type on the specified data sources are refreshed \(ALL\). For descriptions of the supported data statistics types see the *CREATE STATISTICS Statement* topic.


<dl>
<dt><b>

*<data\_statistics\_type\>*

</b></dt>
<dd>

Specifies the type of data statistics objects to match when selecting the data statistics.

```
<data_statistics_type> := TYPE <type_name>

<type_name> ::= 
 HISTOGRAM 
 | SIMPLE 
 | TOPK
 | SKETCH 
 | SAMPLE
 | RECORD COUNT
 | ALL
```



</dd><dt><b>

*<refresh\_type\_filter\>*

</b></dt>
<dd>

Specifies the refresh strategy to match in the data statistics objects when selecting the data statistics to refresh. ALL is the default.

```
<refresh_type_filter> ::= AUTO | MANUAL | ALL 
```



</dd>
</dl>



</dd>
</dl>



<a name="loio20d7c595751910148307bf3bf4c745e6__sql_drop_statistics_1sql_drop_statistics_description"/>

## Description

You can specify multiple filtering clauses to refine the list of data statistics objects to drop.

Refer to the CREATE STATISTICS statement for complete descriptions of the data statistic types \(*<data\_statistics\_type\>* amd *<refresh\_type\>*\).



<a name="loio20d7c595751910148307bf3bf4c745e6__section_opr_ddt_5cb"/>

## Permissions

One of the following is true:

-   You own the object you are dropping statistics from.
-   You have the ALTER privilege on the object you are dropping statistics from.
-   For linked database, you have the LINKED DATABASE object level privilege on the remote source, regardless of who owns the remote source.



<a name="loio20d7c595751910148307bf3bf4c745e6__sql_drop_statistics_1sql_drop_statistics_example"/>

## Example

Drop the HISTOGRAM on column T.X, where T is a virtual table:

```
DROP STATISTICS ON MYSCHEMA.T(X) TYPE HISTOGRAM;
```

Drop a data statistics object with the name HISTOGRAM\_T\_X:

```
DROP STATISTICS MYSCHEMA.HISTOGRAM_T_X;
```

Drop any data statistic object with *<data\_sources\>* defined as `T(A,B)`:

```
DROP STATISTICS ON MYSCHEMA.T(A,B) EXACT;
```

Drop any data statistic object that has table columns T.A, T.B, or T.C listed in *<data\_sources\>*m. For example, SKETCH and SAMPLE defined on T\(A, B\).

```
DROP STATISTICS ON MYSHEMA.T(A,B,C) CASCADE TYPE ALL;
```

Drop the HISTOGRAMS on table columns T.A, T.B, and T.C:

```
DROP STATISTICS ON MYSCHEMA.T(A,B,C) TYPE HISTOGRAM;
```

Drop the record count on table T:

```
DROP STATISTICS ON MYSCHEMA.T TYPE RECORD COUNT;
```

**Related Information**  


[CREATE STATISTICS Statement \(Data Definition\)](create-statistics-statement-data-definition-20d5252.md "Creates data statistic objects that allow the query optimizer to make better decisions for query plans.")

[ALTER STATISTICS Statement \(Data Definition\)](alter-statistics-statement-data-definition-c656476.md "Alters the properties of a data statistics object.")

[REFRESH STATISTICS Statement \(Data Definition\)](refresh-statistics-statement-data-definition-20fae6d.md "Specifies a column that is part of the data sources.")

[M\_DATA\_STATISTICS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-data-statistics-system-view-4f74378.md "Lists data statistics generated when you query column and row store object.")

[M\_SYSTEM\_DATA\_STATISTICS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-system-data-statistics-system-view-b354762.md "Lists data statistics generated by the server when you query a column and row store object.")

