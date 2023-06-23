<!-- loio20d5252d7519101493f5e662a6cda4d4 -->

# CREATE STATISTICS Statement \(Data Definition\)

Creates data statistic objects that allow the query optimizer to make better decisions for query plans.



<a name="loio20d5252d7519101493f5e662a6cda4d4__sql_create_statistics_1sql_create_statistics_syntax"/>

## Syntax

```
CREATE STATISTICS [ <data_statistics_name> ] ON <data_sources> 
 [ <data_statistics_type> ] 
 [ <data_statistics_properties> ]
 [ <initial_refresh> ]
```



<a name="loio20d5252d7519101493f5e662a6cda4d4__sql_create_statistics_1sql_create_statistics_syntax_element"/>

## Syntax Element


<dl>
<dt><b>

*<data\_statistics\_name\>*

</b></dt>
<dd>

Specifies a unique name for the data statistics object.

```
<data_statistics_name> ::= [ <schema_name>.]<identifier>
```

*<data\_statistics\_name\>* is only allowed when the result of the creation is a single data statistics object. The number of data statistics objects created by CREATE STATISTICS is determined by the combination of *<data\_statistics\_type\>* and the number of columns specified in *<data\_sources\>*.

```
<schema_name> ::= <identifier>
```

*<schema\_name\>* must be the same as specified for data source.



</dd><dt><b>

*<data\_sources\>*

</b></dt>
<dd>

Specifies the data sources you want to create data statistics objects for.

```
<data_sources> ::= 
<table_name> [ ( <column_name>[,<column_name>[,...] ] )  ]
```

For RECORD COUNT data statistics objects, you cannot specify columns as part of *<data\_sources\>*.


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

Specifies the table name you want to create statistics on.

```
<table_name> ::= [ <database_name>.]<schema_name>.]<identifier>
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



</dd>
</dl>



</dd><dt><b>

*<data\_statistics\_type\>*

</b></dt>
<dd>

Specifies the type of data statistics object to create.

```
<data_statistics_type> := TYPE <type_name>

<type_name> ::= 
HISTOGRAM 
 | SIMPLE 
 | TOPK
 | SKETCH 
 | SAMPLE [ <sample_size_modifier> ]
 | RECORD COUNT
```

A data source can have only one data statistics object of a certain type. For example, column A of table T can have one data statistics object of type HISTOGRAM and one of type SIMPLE. If the TYPE clause is not specified, then the default is HISTOGRAM. Some data statistic types may not be appropriate for a given data source.


<dl>
<dt><b>

HISTOGRAM

</b></dt>
<dd>

Creates a data statistics object that helps the query optimizer estimate the data distribution in a single-column data source. If you specify multiple columns in *<data\_sources\>*, then multiple data statistics objects \(HISTOGRAM\) are created--one per column specified.



</dd><dt><b>

SIMPLE

</b></dt>
<dd>

Creates a data statistics object that helps the query optimizer calculate basic statistics, such as min, max, null count, count, and distinct count for a single-column data source. If you specify multiple columns in *<data\_sources\>*, then multiple data statistics objects are created--one per column specified. When beneficial, the SQL optimizer maintains system SIMPLE data statistics objects automatically on column and row store tables only.



</dd><dt><b>

TOPK

</b></dt>
<dd>

Creates a data statistics object that helps the query optimizer identify the highest-frequency values in a table data source. If you specify multiple columns in *<data\_sources\>*, then multiple data statistics objects are created--one per column specified. When beneficial, the SQL optimizer maintains system TOPK data statistics objects automatically \(column store only\).



</dd><dt><b>

SKETCH

</b></dt>
<dd>

Creates a data statistics object that helps the query optimizer estimate the number of distinct values in the data source. A data statistics object is created for the specified <code><i class="varname">&lt;table_name&gt;</i>(<i class="varname">&lt;column-name&gt;</i>,...)</code>, which approximates the number of distinct tuples in the projection of the table on the set of specified columns.



</dd><dt><b>

SAMPLE

</b></dt>
<dd>

Creates a sample of data from *<data\_source\>* that the SQL optimizer can use during optimization. When beneficial, the SQL optimizer generates system SAMPLE data statistics objects automatically on column and row store tables. However, this behavior can incur a cost to performance. You can avoid this cost by creating SAMPLE data statistics objects explicitly \(in advance\). Creating them explicitly is especially useful in situations where sampling live table data is expensive \(for example, very large tables\).

<sample\_size\_modifier\> :: = SAMPLE SIZE <unassigned\_integer\> defines the sample size. SAMPLE SIZE <n\> is optional; if it is not given, the default value is 1000.



</dd><dt><b>

RECORD COUNT

</b></dt>
<dd>

Creates a data statistics object that helps the query optimizer calculate the number of records \(rows\) in a table data source. The RECORD COUNT type is a table-wide statistic. You do not specify columns in *<data\_sources\>* when creating a RECORD COUNT data statistics object. CREATE STATISTICS TYPE RECORD COUNT is not supported for column store tables. When beneficial, the SQL optimizer maintains system RECORD COUNT data statistics objects automatically on column and row store tables.



</dd>
</dl>



</dd><dt><b>

*<data\_statistics\_properties\>*

</b></dt>
<dd>

Specifies the properties of the data statistics object.

```
<data_statistics_properties> ::= 
 <data_statistics_property>[,<data_statistics_property>[,...] ]
   
<data_statistics_property> ::= 
 REFRESH TYPE <refresh_type>
 | ENABLE <on_off>
 | BUCKETS <unsigned_integer>
 | QERROR <numeric_literal>
 | QTHETA <unsigned_integer>
 | { MEMORY <memory_bytes> | MEMORY PERCENT <memory_percentage> }
 | ACCURACY <numeric_literal>
 | PREFIX BITS <unsigned_integer>
 | PERSISTENT <on_off>
 | VALID FOR <valid_for_list>
 | CONSTRAINT '<constraint_param>'
```

Restrictions to which properties apply to which statistic types are noted in the property descriptions.


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

ENABLE ON enables the optimizer to see the data statistics object. The data statistics object must be populated with data for the optimizer to use it. ENABLE ON specified with NO INITIAL REFRESH returns an error.

ENABLE ON is the default behavior.

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

Controls the number of bits the SKETCH algorithms use when constructing the SKETCH statistics. Specify this parameter when TYPE is SKETCH. Its value is an integer between 0 and 63. The default is 8.



</dd><dt><b>

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



</dd><dt><b>

CONSTRAINT *<constraint\_param\>*

</b></dt>
<dd>

Specifies constraints to use for the specified *<data\_statistics\_type\>*.

-   For HISTOGRAM, *<constraint\_param\>* specifies the mathematical constraint for the HISTOGRAM:

    ```
    <constraint_param> ::= { QOPTIMAL | MAXDIFF }
    ```

    QOPTIMAL HISTOGRAMS are for column store tables only. MAXDIFF HISTOGRAMS are only for row tables and virtual tables. The defaults are QOPTIMAL for column tables and MAXDIFF for other data sources.

    A non-default CONSTRAINT for HISTOGRAMS results in an error.

    HISTOGRAM sizing restrictions \(BUCKETS, MEMORY, and MEMORY PERCENT\) are applied per HISTOGRAM.

-   For SKETCH, *<constraint\_param\>* specifies the algorithm to use to build the SKETCH. The default is LOGLOGCOUNTING; the remaining algorithms are for internal use.

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

*<initial\_refresh\>*

</b></dt>
<dd>

Specifies whether to populate the data statistics object with data after creation.

```
<initial_refresh> ::= [ NO ] INITIAL REFRESH
```


<dl>
<dt><b>

INITIAL REFRESH

</b></dt>
<dd>

Creates the definition of the data statistics object and populates it with data. The default behavior is INITIAL REFRESH.



</dd><dt><b>

NO INITIAL REFRESH

</b></dt>
<dd>

Creates the definition of the data statistics object, but does not populate it with data.

Use NO INITIAL REFRESH when you want to change the underlying data before refreshing the data statistics object.

You cannot specify NO INITIAL REFRESH if ENABLE OFF is not specified.



</dd>
</dl>



</dd>
</dl>



<a name="loio20d5252d7519101493f5e662a6cda4d4__section_opr_ddt_5cb"/>

## Permissions

One of the following is true with regards to required permission:

-   You own the object you are creating statistics on.
-   You have the ALTER privilege on the object you are creating statistics on.
-   For linked database, you have the LINKED DATABASE object level privilege on the remote source, regardless of who created the remote source.



<a name="loio20d5252d7519101493f5e662a6cda4d4__sql_create_statistics_1sql_create_statistics_description"/>

## Description

The CREATE STATISTICS statement creates data statistics objects that approximate the specified *<data\_sources\>*. The optimizer uses data statistics objects to estimate the properties of the data without directly accessing the data. Data statistics objects can be useful during query optimization and query execution.



<a name="loio20d5252d7519101493f5e662a6cda4d4__sql_create_statistics_1sql_create_statistics_example"/>

## Examples

The following example creates a MAXDIFF HISTOGRAM with a maximum of 100 buckets on, the column T\(X\), where T is a virtual table.

```
CREATE STATISTICS ON MYSYSTEM.T(X) TYPE HISTOGRAM BUCKETS 100;
```

This example creates two SIMPLE statistics on two columns of table T where T is a virtual table, one for each column. The end result is the same as executing two CREATE STATISTICS statements on table T, one for each column.

```
CREATE STATISTICS ON MYSYSTEM.T(X,Y) TYPE SIMPLE;
```

The following example creates a q-optimal HISTOGRAM with a maximum 1000 buckets for each partition of the table on the column T\(X\), where T is a partitioned column store table.

```
CREATE STATISTICS ON MYSYSTEM.T(X) TYPE HISTOGRAM BUCKETS 1000;
```

The following example creates a SKETCH called SKETCH\_T\_XY with a manual refresh type for each partition in the table on the columns T\(X\) and T\(Y\), where T is a partitioned column store table.

```
CREATE STATISTICS MYSYSTEM.SKETCH_T_XY ON MYSYSTEM.T(X,Y) TYPE SKETCH REFRESH TYPE MANUAL;
```

The following example creates RECORD COUNT statistics for the virtual table MY\_VIRUTIAL\_TABLE.

```
CREATE STATISTICS ON MYSYSTEM.MY_VIRTUAL_TABLE TYPE RECORD COUNT;
```

The following example creates TOPK statistics on T\(A\) with 1500 most frequently observed values on the remote source REMOTE1 using linked database:

```
CREATE STATISTICS ON REMOTE1.MYSYSTEM.T(A) TYPE TOPK BUCKETS 1500;
```

The following example creates a SIMPLE data statistics object, MYSIMPLESTAT on a partitioned column store table MYSYSTEM.MY\_TABLE and enables it for use with dynamic partition pruning:

```
CREATE STATISTICS MYSYSTEM.MYSIMPLTESTAT ON MYSYSTEM.MYTABLE(A) TYPE SIMPLE VALID FOR DATA DEPENDENCY;
```

The following example creates SAMPLE statistics with a SAMPLE SIZE of 10000 for a big table MY\_TABLE:

```
CREATE STATISTICS ON MYSYSTEM.MY_TABLE TYPE SAMPLE SAMPLE SIZE 10000;
```

**Related Information**  


[CREATE STATISTICS Statement \(Data Definition\)](create-statistics-statement-data-definition-20d5252.md "Creates data statistic objects that allow the query optimizer to make better decisions for query plans.")

[ALTER STATISTICS Statement \(Data Definition\)](alter-statistics-statement-data-definition-c656476.md "Alters the properties of a data statistics object.")

[REFRESH STATISTICS Statement \(Data Definition\)](refresh-statistics-statement-data-definition-20fae6d.md "Specifies a column that is part of the data sources.")

[DROP STATISTICS Statement \(Data Definition\)](drop-statistics-statement-data-definition-20d7c59.md "Drops user-defined data statistic objects that the query optimizer uses to make decisions for query plans.")

[M\_DATA\_STATISTICS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-data-statistics-system-view-4f74378.md "Lists data statistics generated when you query column and row store object.")

[M\_SYSTEM\_DATA\_STATISTICS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-system-data-statistics-system-view-b354762.md "Lists data statistics generated by the server when you query a column and row store object.")

[DATA\_STATISTICS System View](../../020-System-Views-Reference/021-System-Views/data-statistics-system-view-20a1f10.md "Provides an overview of data statistics objects.")

