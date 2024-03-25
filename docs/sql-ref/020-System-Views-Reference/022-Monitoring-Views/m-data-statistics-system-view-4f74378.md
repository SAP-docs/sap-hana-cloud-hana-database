<!-- loio4f74378472cb46a6bbff3582b1863bac -->

# M\_DATA\_STATISTICS System View

Lists data statistics generated when you query column and row store object.



<a name="loio4f74378472cb46a6bbff3582b1863bac___d_a_t_a__s_t_a_t_i_s_t_i_c_s_1struct_DATA_STATISTICS"/>

## Structure


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

DATA\_STATISTICS\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the data statistics object ID.

</td>
</tr>
<tr>
<td valign="top">

DATA\_STATISTICS\_TYPE

</td>
<td valign="top">

NVARCHAR\(12\)

</td>
<td valign="top">

Displays the data statistics object type.

</td>
</tr>
<tr>
<td valign="top">

DATA\_STATISTICS\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the data statistics object schema.

</td>
</tr>
<tr>
<td valign="top">

DATA\_STATISTICS\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the data statistics object name.

</td>
</tr>
<tr>
<td valign="top">

DATA\_SOURCE\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the data source object.

</td>
</tr>
<tr>
<td valign="top">

DATA\_SOURCE\_OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the data source object.

</td>
</tr>
<tr>
<td valign="top">

DATA\_SOURCE\_COLUMN\_NAMES

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Lists the column names of the data source.

</td>
</tr>
<tr>
<td valign="top">

DATA\_SOURCE\_STORAGE\_TYPE

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the source storage type of the data source.

</td>
</tr>
<tr>
<td valign="top">

DATA\_SOURCE\_PART\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the partition ID of the data source.

</td>
</tr>
<tr>
<td valign="top">

LAST\_REFRESH\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time the data statistics on the object were last generated.

</td>
</tr>
<tr>
<td valign="top">

LAST\_REFRESH\_REASON

</td>
<td valign="top">

NVARCHAR\(19\)

</td>
<td valign="top">

Displays the time the data statistics object was generated.

</td>
</tr>
<tr>
<td valign="top">

DATA\_STATISTICS\_CONTENT

</td>
<td valign="top">

NCLOB \(max size 2Gb\)

</td>
<td valign="top">

Lists the content and properties of the data statistics object as of the last refresh \(JSON format\). The content section is empty for SIMPLE, SKETCH, and RECORD COUNT; it contains bucket boundaries and counts for HISTOGRAM and a values and frequencies list for TOPK. For SAMPLE, it contains a list of sample output. The content is similar to exported data for data statistics objects.

The properties section contains properties relevant to the data statistics of the specified type. The properties section, when present, may include some of the following properties:


<dl>
<dt><b>

MEMORY

</b></dt>
<dd>

Displays the memory size used by the data statistics object in bytes



</dd><dt><b>

MEMORY PERCENT

</b></dt>
<dd>

Displays the memory size used by the data statistics object, as a percentage of the data source size



</dd><dt><b>

COUNT

</b></dt>
<dd>

Displays the number of rows in the data source



</dd><dt><b>

DISTINCT COUNT

</b></dt>
<dd>

Displays the number of unique values in the data source



</dd><dt><b>

NULL COUNT

</b></dt>
<dd>

Displays the number of NULL values in the data source



</dd><dt><b>

BUCKETS

</b></dt>
<dd>

Displays the number of buckets in the data statistics object



</dd><dt><b>

QERROR

</b></dt>
<dd>

Displays the value of the qerror parameter used for building the data statistics object



</dd><dt><b>

QTHETA

</b></dt>
<dd>

Displays the value of the qtheta parameter used for building the data statistics object



</dd><dt><b>

ACCURACY

</b></dt>
<dd>

Displays the accuracy parameter used for building the data statistics object



</dd><dt><b>

PREFIX BITS

</b></dt>
<dd>

Displays the prefix bits parameter used for building the data statistics object



</dd><dt><b>

MIN VALUE

</b></dt>
<dd>

Displays the minimum value in the data source in bytes



</dd><dt><b>

MAX VALUE

</b></dt>
<dd>

Displays the maximum value in the data source in bytes



</dd><dt><b>

MAX\_ROWID

</b></dt>
<dd>

Displays the maximum rowID for the data statistics object



</dd><dt><b>

MIN MAX IS VALID

</b></dt>
<dd>

Displays whether MIN/MAX values are valid



</dd><dt><b>

SAMPLE SIZE

</b></dt>
<dd>

Displays the sample size at build time, expressed in bytes



</dd><dt><b>

SAMPLE SIZE PERCENT

</b></dt>
<dd>

Displays the sample size at build time, expressed as a percent of the data volume



</dd>
</dl>



</td>
</tr>
</table>

**Related Information**  


[CREATE STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-statistics-statement-data-definition-20d5252.md "Creates data statistic objects that allow the query optimizer to make better decisions for query plans.")

[ALTER STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-statistics-statement-data-definition-c656476.md "Alters the properties of a data statistics object.")

[REFRESH STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/refresh-statistics-statement-data-definition-20fae6d.md "Specifies a column that is part of the data sources.")

[DROP STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-statistics-statement-data-definition-20d7c59.md "Drops user-defined data statistic objects that the query optimizer uses to make decisions for query plans.")

[M\_SYSTEM\_DATA\_STATISTICS System View](m-system-data-statistics-system-view-b354762.md "Lists data statistics generated by the server when you query a column and row store object.")

[DATA\_STATISTICS System View](../021-System-Views/data-statistics-system-view-20a1f10.md "Provides an overview of data statistics objects.")

[Managing Statistics](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/0a9ae9e9ccc743f4a2808399da354657.html "Statistics assist the query optimizer in making better decisions and work for both virtual tables and linked database.") :arrow_upper_right:

