<!-- loio20fae6d975191014849d91781fd50986 -->

# REFRESH STATISTICS Statement \(Data Definition\)

Specifies a column that is part of the data sources.



<a name="loio20fae6d975191014849d91781fd50986__sql_refresh_statistics_1sql_refresh_statistics_syntax"/>

## Syntax

```
REFRESH STATISTICS { <data_statistics_name>[,<data_statistics_name>[,...] ]
   | ON <data_sources> [ [HAVING] <match_properties> ] };
```



<a name="loio20fae6d975191014849d91781fd50986__sql_refresh_statistics_1sql_refresh_statistics_syntax_element"/>

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

Specifies the table on which the data statistics are defined.

```
<table_name> ::= [ [ <database_name>.]<schema_name>.]<identifier>
```

For linked database, *<database\_name\>* is the name of the remote source. For all other cases, *<database\_name\>* is the name of the database where the table is located.



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



<a name="loio20fae6d975191014849d91781fd50986__sql_refresh_statistics_1sql_refresh_statistics_description"/>

## Description

The REFRESH STATISTICS statement rebuilds data statistics objects that approximate the specified *<data\_sources\>*, and only affects ENABLED data statistics objects.

If you employ a manual delta merge strategy instead of an automatic delta merge strategy, consider refreshing your data statistics objects more frequently to avoid stale statistics.

For descriptions of the supported data statistic types \(*<data\_statistics\_type\>*\), see the CREATE STATISTICS statement .



<a name="loio20fae6d975191014849d91781fd50986__section_opr_ddt_5cb"/>

## Permissions

One of the following is true:

-   You own the object you are refreshing statistics on.
-   You have the ALTER privilege on the object you are refreshing statistics on.
-   For linked database, you have the LINKED DATABASE object level privilege on the remote source, regardless of who owns the remote source.



<a name="loio20fae6d975191014849d91781fd50986__sql_refresh_statistics_1sql_refresh_statistics_example"/>

## Example

The following example refreshes the HISTOGRAM on column T\(X\), where T is a virtual table:

```
REFRESH STATISTICS ON MYSCHEMA.T(X) TYPE HISTOGRAM;
```

The following example refreshes any SKETCH with *<data\_sources\>* containing one or more of columns T\(X\), T\(Y\), or T\(Z\) \(only\) in any order:

```
REFRESH STATISTICS ON MYSCHEMA.T(X, Y, Z) TYPE SKETCH;
```

The following example refreshes the database statistics object named HISTOGRAM\_T\_X:

```
REFRESH STATISTICS MYSCHEMA.HISTOGRAM_T_X;
```

The following example refreshes any data statistic object with *<data\_sources\>* defined as `T(A, B)`. HISTOGRAMS on T\(A\) and on T\(B\) would not be affected.

```
REFRESH STATISTICS ON MYSCHEMA.T(A, B) EXACT;
```

The following example refreshes any data statistic object that has at least one of the table columns. For example, SKETCH on T\(A.X\) will be refreshed.

```
REFRESH STATISTICS ON MYSCHEMA.T(A, B, C) CASCADE TYPE ALL;
```

The following example refreshes the HISTOGRAM MYSCHEMA.MYHISTOGRAM on table column MYSCHEMA.T\(A\):

```
REFRESH STATISTICS MYSCHEMA.MYHISTOGRAM ON MYSCHEMA.T(A) TYPE HISTOGRAM REFRESH TYPE MANUAL;
```

The following example refreshes the record count on table T:

```
REFRESH STATISTICS ON T TYPE RECORD COUNT;
```

**Related Information**  


[CREATE STATISTICS Statement \(Data Definition\)](create-statistics-statement-data-definition-20d5252.md "Creates data statistic objects that allow the query optimizer to make better decisions for query plans.")

[ALTER STATISTICS Statement \(Data Definition\)](alter-statistics-statement-data-definition-c656476.md "Alters the properties of a data statistics object.")

[DROP STATISTICS Statement \(Data Definition\)](drop-statistics-statement-data-definition-20d7c59.md "Drops user-defined data statistic objects that the query optimizer uses to make decisions for query plans.")

[M\_DATA\_STATISTICS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-data-statistics-system-view-4f74378.md "Lists data statistics generated when you query column and row store object.")

[M\_SYSTEM\_DATA\_STATISTICS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-system-data-statistics-system-view-b354762.md "Lists data statistics generated by the server when you query a column and row store object.")

[DATA\_STATISTICS System View](../../020-System-Views-Reference/021-System-Views/data-statistics-system-view-20a1f10.md "Provides an overview of data statistics objects.")

