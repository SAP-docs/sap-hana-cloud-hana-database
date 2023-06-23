<!-- loio20a1f10a7519101487fcaa1bddb4f7c3 -->

# DATA\_STATISTICS System View

Provides an overview of data statistics objects.



<a name="loio20a1f10a7519101487fcaa1bddb4f7c3___d_a_t_a__s_t_a_t_i_s_t_i_c_s_1struct_DATA_STATISTICS"/>

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

NVARCHAR\(9\)



</td>
<td valign="top">

Displays the data statistics type.



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

Displays the data statistics name.



</td>
</tr>
<tr>
<td valign="top">

DATA\_SOURCE\_OBJECT\_TYPE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays the data source object type, for example, TABLE.



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

Displays the schema name of the data source.



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

Displays the object name of the data source.



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

Displays the column names of the data source.



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

Displays the storage type of the data source.



</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the time when the data statistics object was created.



</td>
</tr>
<tr>
<td valign="top">

CONSTRAINT



</td>
<td valign="top">

NVARCHAR\(20\)



</td>
<td valign="top">

Displays the constraint for the build algorithm for the data statistics object.



</td>
</tr>
<tr>
<td valign="top">

IS\_PERSISTENT



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the content of the data statistics object is persistent or not: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

IS\_ENABLED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the data statistics object is enabled: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

CREATE\_MEMORY



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the memory size that the data statistics object uses in bytes. This value is set in the CREATE STATISTICS statement.



</td>
</tr>
<tr>
<td valign="top">

CREATE\_MEMORY\_PERCENT



</td>
<td valign="top">

REAL



</td>
<td valign="top">

Displays the memory size, as a percentage of the data source size, to be used by the data statistics object specified in the CREATE STATISTICS statement



</td>
</tr>
<tr>
<td valign="top">

CREATE\_BUCKETS



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of buckets specified in the CREATE STATISTICS statement



</td>
</tr>
<tr>
<td valign="top">

CREATE\_QERROR



</td>
<td valign="top">

REAL



</td>
<td valign="top">

Displays the parameter qerror for the data statistics object of type HISTOGRAM as specified in the CREATE STATISTICS statement



</td>
</tr>
<tr>
<td valign="top">

CREATE\_QTHETA



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the parameter qtheta for the data statistics object of type HISTOGRAM as specified at the CREATE STATISTICS statement



</td>
</tr>
<tr>
<td valign="top">

CREATE\_ACCURACY



</td>
<td valign="top">

REAL



</td>
<td valign="top">

Displays the parameter accuracy for the data statistics object of type SKETCH as specified in the CREATE STATISTICS statement



</td>
</tr>
<tr>
<td valign="top">

CREATE\_PREFIX\_BITS



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the parameter prefix bits for the data statistics object of type SKETCH as specified at the CREATE STATISTICS statement.



</td>
</tr>
<tr>
<td valign="top">

CREATE\_SAMPLE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the sample size, in bytes, to be used by the data statistics object of type SAMPLE specified in the CREATE STATISTICS statement.



</td>
</tr>
<tr>
<td valign="top">

CREATE\_SAMPLE\_SIZE\_PERCENT



</td>
<td valign="top">

REAL



</td>
<td valign="top">

Displays the sample size, as a percentage of the data source size, to be used by the data statistics object of type SAMPLE specified in the CREATE STATISTICS statement.



</td>
</tr>
<tr>
<td valign="top">

VALID\_FOR



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays how the data statistics object may be used: ESTIMATION/DATA DEPENDENCY.



</td>
</tr>
<tr>
<td valign="top">

INVALIDATION\_REASON



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the reason for invalidating a data statistics object:


<dl>
<dt><b>

NULL

</b></dt>
<dd>

The object is valid.



</dd><dt><b>

USER ACTION

</b></dt>
<dd>

The data statistics object is invalid because a user has disabled it.



</dd><dt><b>

ALTER TABLE MOVE

</b></dt>
<dd>

The data statistics object is disabled because a user relocated the table to a different storage space.



</dd><dt><b>

ALTER COLUMN DATA TYPE

</b></dt>
<dd>

The data statistics object is disabled because the data type of the underlying column\(s\) no longer supports the statistics type.



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

[M\_DATA\_STATISTICS System View](../022-Monitoring-Views/m-data-statistics-system-view-4f74378.md "Lists data statistics generated when you query column and row store object.")

[M\_SYSTEM\_DATA\_STATISTICS System View](../022-Monitoring-Views/m-system-data-statistics-system-view-b354762.md "Lists data statistics generated by the server when you query a column and row store object.")

