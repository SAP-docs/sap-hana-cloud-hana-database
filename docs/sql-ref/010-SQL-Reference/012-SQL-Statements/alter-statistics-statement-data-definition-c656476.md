<!-- loioc6564762f4b846e5a76fcfb3fd7a1a88 -->

# ALTER STATISTICS Statement \(Data Definition\)

Alters the properties of a data statistics object.





<a name="loioc6564762f4b846e5a76fcfb3fd7a1a88__sql_drop_statistics_1sql_drop_statistics_syntax"/>

## Syntax

```
ALTER STATISTICS { <data_statistics_name> [,...] | ON <data_sources> [ [ HAVING ] <match_properties> ] }
 [ SET <set_data_statistics_properties> ]
 [ <add_drop_data_statistics_properties> ]
 [ <initial_refresh> ]
```



<a name="loioc6564762f4b846e5a76fcfb3fd7a1a88__sql_drop_statistics_1sql_drop_statistics_syntax_element"/>

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

For RECORD COUNT data statistics objects, you cannot specify columns as part of *<data\_sources\>*.


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



</dd><dt><b>

*<set\_data\_statistics\_properties\>*

</b></dt>
<dd>

Specifies the properties of the data statistics objects to modify.

```
<data_statistics_properties> ::= 
 <data_statistics_property>[, <data_statistics_property>[,...] ]
   
<data_statistics_property> ::= 
 REFRESH TYPE <refresh_type>
 | ENABLE <on_off>
 | BUCKETS <unsigned_integer>
 | QERROR <numeric_literal>
 | QTHETA <unsigned_integer>
 | { MEMORY <memory_bytes> | MEMORY PERCENT <memory_percentage> }
 | ACCURACY <numeric_literal>
 | PREFIXBITS <unsigned_integer>
 | PERSISTENT <on_off>
 | CONSTRAINT <constraint_param>
```


<dl>
<dt><b>

REFRESH TYPE *<refresh\_type\>*

</b></dt>
<dd>

Specifies the strategy for the data statistics object.

```
<refresh_type> ::= { AUTO | MANUAL | DEFAULT }
```

AUTO specifies that the data statistics object is refreshed automatically when underlying data changes. AUTO is only supported on column store.

MANUAL specifies that the database statistics object is not refreshed until a rebuild is explicitly requested by a REFRESH STATISTICS statement.

DEFAULT specifies that the database server decides the best refresh strategy based on the data source. For example, for data statistics objects on column store data sources, the database server applies AUTO for the default.

REFRESH TYPE only affects data statistics objects that are enabled.



</dd><dt><b>

ENABLE *<on\_off\>*

</b></dt>
<dd>

Controls whether the optimizer uses the data statistics object.

```
<on_off> ::= { ON | OFF }
```

ENABLE ON enables the optimizer to see the data statistics object. The data statistics object must be populated with data for the optimizer to use it.

ENABLE OFF disables the use of the data statistics object by the optimizer and prevents the ability to refresh the data statistics object. Data statistics objects that are not enabled can still be dropped. To make a data statistics object with ENABLE OFF accessible to the optimizer, execute an ALTER STATISTICS...ENABLE ON statement.



</dd><dt><b>

BUCKETS *<unsigned\_integer\>*

</b></dt>
<dd>

The BUCKETS property is only for use with TYPE HISTOGRAM or TOPK. For HISTOGRAM, BUCKETS specifies the maximum number of data buckets in the HISTOGRAM. For TOPK, BUCKETS specifies the K value.

The default is automatically determined by the data statistics building algorithm in use.

If a very small number of buckets is specified for a QOPTIMAL HISTOGRAM, then the algorithm may fail to build a valid HISTOGRAM either during the first build or during a subsequent refresh executed for the HISTOGRAM.



</dd><dt><b>

QERROR *<numeric\_literal\>*

</b></dt>
<dd>

Specifies the Q error to use for the q-optimal HISTOGRAM. You can specify this parameter when TYPE is HISTOGRAM and CONSTRAINT is QOPTIMAL. The default is automatically determined by the HISTOGRAM algorithm in use.



</dd><dt><b>

QTHETA *<unsigned\_integer\>*

</b></dt>
<dd>

Specifies a lower bound on the frequencies for which a q error constraint is applied for a q-optimal HISTOGRAM. You can specify this parameter when TYPE is HISTOGRAM and CONSTRAINT is QOPTIMAL. The default is automatically determined by the HISTOGRAM algorithm in use.



</dd><dt><b>

MEMORY *<memory\_bytes\>*

</b></dt>
<dd>

Specifies the maximum amount of memory, in bytes, to use for QOPTIMAL HISTOGRAMS.

```
<memory_bytes> ::= <unsigned_integer>
```

The MEMORY parameter limits the memory for QOPTIMAL HISTOGRAMS. MEMORY applies only to the QOPTIMAL HISTOGRAM algorithm. Small values for MEMORY may cause the QOPTIMAL HISTOGRAM algorithm to pick a small number of buckets, which can lead to failures building or refreshing the HISTOGRAM.



</dd><dt><b>

MEMORY PERCENT *<memory\_percentage\>*

</b></dt>
<dd>

Specifies the maximum amount of memory to use for the data statistics object, expressed as a percentage of the space used by the data source.

```
<memory_percentage> ::= <unsigned_integer>
```

HISTOGRAMS can use a large amount of memory for some data sources. *<memory\_percentage\>* represents the maximum amount of memory that can be used for the data statistics object. For example, if a data source is a table column that uses 100 MB of memory, and *<memory\_percentage\>* is 5, then the data statistics object for this column can use, at most, 5 MB for its in-memory representation.

The default is automatically determined by the HISTOGRAM algorithm in use. Small values for MEMORY PERCENT may cause the QOPTIMAL HISTOGRAM algorithm to pick a small number of buckets, which can lead to failures building or refreshing the HISTOGRAM.



</dd><dt><b>

PERSISTENT *<on\_off\>*

</b></dt>
<dd>

Specifies whether data statistics object data persists in the storage of the table, and only applies to QOPTIMAL HISTOGRAMS on column store tables. The default is PERSISTENT ON.

```
<on_off> ::= { ON | OFF }
```

Other statistics types are always persistent.



</dd><dt><b>

ACCURACY *<numeric\_literal\>*

</b></dt>
<dd>

Controls the time and space requirements to use for the SKETCH algorithms. This parameter can only be specified when TYPE is SKETCH and must be a number between 0 and 1, with larger values causing decreased time and space requirements but poorer SKETCH resolution. The default is 0.1.



</dd><dt><b>

PREFIX BITS *<unsigned\_integer\>*

</b></dt>
<dd>

This parameter, ranging from 0 to 63, determines the number of bits used by SKETCH algorithms when constructing SKETCH statistics. While PREFIX BITS can be set within this range, increasing it significantly beyond the default value of 8 can greatly increase memory usage and risk memory allocation failures. Therefore, it is strongly advised to use the default value of 8 to ensure efficient memory use and stable performance.



</dd><dt><b>

CONSTRAINT *<constraint\_param\>*

</b></dt>
<dd>

Specifies constraints to use for the specified *<data\_statistics\_type\>*. For SKETCH, *<constraint\_param\>* specifies the algorithm to use to build the SKETCH. The default is LOGLOGCOUNTING; the remaining algorithms are for internal use.

```
<constraint_param> ::= 
KMINVAL
| PCSA
| LINEARCOUNTING
| LOGCOUNTING
| LOGLOGCOUNTING
| SUPERLOGLOGCOUNTING
```



</dd>
</dl>



</dd><dt><b>

*<add\_drop\_data\_statistics\_properties\>*

</b></dt>
<dd>

Specifies the properties of the data statistics objects you set using the ADD and DROP keywords.

```
<add_drop_data_statistics_properties> ::= <add_drop_property> [ <add_drop_property> […]]

<add_drop_property> ::=   
{ ADD | DROP } VALID FOR <valid_for_list>
```

This property is supported for column store tables, but not row store, virtual tables or linked database.


<dl>
<dt><b>

VALID FOR *<valid\_for\_list\>*

</b></dt>
<dd>

Defines how the data statistics object may be used. The VALID FOR clause is only permitted with statistics type SIMPLE.

```
<valid_for_list> ::= <usage>[, <usage>[,...] ]

<usage> ::= { ESTIMATION | DATA DEPENDENCY }
```

ESTIMATION initializes the data statistics object for use by the optimizer to improve selectivity estimation. SIMPLE data statistics objects are initialized for estimation use by default.

DATA DEPENDENCY applies to partitioned column store and multistore tables only. It initializes the data statistics object to be used by features that require higher \(or more\) data consistency \(including automatically refreshing and rebuilding when needed\), such as the dynamic partition pruning feature. For more information about the dynamic partition pruning feature, including the types of columns that can have data statistics defined for dynamic partition pruning, see the *SAP HANA Cloud, SAP HANA Database Administration Guide*.



</dd>
</dl>



</dd><dt><b>

*<initial\_refresh\>*

</b></dt>
<dd>

Specifies whether to repopulate the data statistics object with data after altering it.

```
<initial_refresh> ::= [ NO ] INITIAL REFRESH
```

If the object was built, then disabled, and is now being re-enabled, then initial refresh is not required.


<dl>
<dt><b>

INITIAL REFRESH

</b></dt>
<dd>

Alters the definition of the data statistics object and repopulates it with data. The default behavior is INITIAL REFRESH.



</dd><dt><b>

NO INITIAL REFRESH

</b></dt>
<dd>

Alters the definition of the data statistics object, but does not repopulate it with data.

Use NO INITIAL REFRESH when you want to change the underlying data before refreshing the data statistics object.

You cannot specify NO INITIAL REFRESH if ENABLE OFF is not specified.



</dd>
</dl>



</dd>
</dl>



<a name="loioc6564762f4b846e5a76fcfb3fd7a1a88__section_opr_ddt_5cb"/>

## Permissions

One of the following is true:

-   You own the object you are altering statistics on.
-   You have the ALTER object privilege on the object you are altering statistics on.
-   For linked database, you have the LINKED DATABASE object privilege on the remote source, regardless of who owns the remote source.



<a name="loioc6564762f4b846e5a76fcfb3fd7a1a88__sql_drop_statistics_1sql_drop_statistics_description"/>

## Description

The ALTER STATISTICS statement alters the properties of a data statistics object. A typical change to a data statistics object might be to enable or disable it, or to change settings for properties such as BUCKETS or ENABLE ON/OFF.

ADD, DROP and SET clauses can be specified in any order in the ALTER STATISTICS statement, but not more than once each.

You cannot alter the type for the data statistics object. For example, you cannot change a data statistics object from a HISTOGRAM to a SKETCH, you must create the SKETCH data statistics object separately.



<a name="loioc6564762f4b846e5a76fcfb3fd7a1a88__sql_drop_statistics_1sql_drop_statistics_example"/>

## Example

The following example sets the refresh type of a HISTOGRAM on data source T\(X\) to AUTO and rebuilds the data statistics object:

```
ALTER STATISTICS on MYSYSTEM.T(X) TYPE HISTOGRAM SET REFRESH TYPE AUTO;
```

The following example alters the MYSIMPLESTAT data statistics object to enable it for use with dynamic partition pruning and rebuilds the data statistics object:

```
ALTER STATISTICS MYSIMPLESTA ADD VALID FOR DATA DEPENDENCY;
```

The following example sets the number of buckets to 10 on the remote source REMOTE2 using linked database. The NO INITIAL REFRESH clause means the new setting will not take effect until the next time the object is rebuilt using the REFRESH STATISTICS statement.

```
ALTER STATISTICS on "REMOTE2"."SYSTEM"."A1" TYPE TOPK SET BUCKETS 10 NO INITIAL REFRESH;
```

The following example sets the number of buckets to 150 for the TOPK data statistics object on the virtual table REMOTE2\_A1.

```
ALTER STATISTICS on MYSYSTEM.REMOTE2_A1 TYPE TOPK SET BUCKETS 10;
```

**Related Information**  


[CREATE STATISTICS Statement \(Data Definition\)](create-statistics-statement-data-definition-20d5252.md "Creates data statistic objects that allow the query optimizer to make better decisions for query plans.")

[REFRESH STATISTICS Statement \(Data Definition\)](refresh-statistics-statement-data-definition-20fae6d.md "Specifies a column that is part of the data sources.")

[DROP STATISTICS Statement \(Data Definition\)](drop-statistics-statement-data-definition-20d7c59.md "Drops user-defined data statistic objects that the query optimizer uses to make decisions for query plans.")

[M\_DATA\_STATISTICS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-data-statistics-system-view-4f74378.md "Lists data statistics generated when you query column and row store object.")

[M\_SYSTEM\_DATA\_STATISTICS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-system-data-statistics-system-view-b354762.md "Lists data statistics generated by the server when you query a column and row store object.")

[DATA\_STATISTICS System View](../../020-System-Views-Reference/021-System-Views/data-statistics-system-view-20a1f10.md "Provides an overview of data statistics objects.")

