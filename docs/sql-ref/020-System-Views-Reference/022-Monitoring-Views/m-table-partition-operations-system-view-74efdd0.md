<!-- loio74efdd0717bd44528263ca684e159635 -->

# M\_TABLE\_PARTITION\_OPERATIONS System View

Provides information on table partition operations from the memory ring buffer or disk trace files.




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

START\_TIME



</td>
<td valign="top">

LONGDATE



</td>
<td valign="top">

Displays the time the statement started.



</td>
</tr>
<tr>
<td valign="top">

DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the duration, in microseconds, the statement ran.



</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the table name.



</td>
</tr>
<tr>
<td valign="top">

USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the user name who executed the operation.



</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_HASH



</td>
<td valign="top">

VARCHAR\(32\)



</td>
<td valign="top">

Displays the unique identifier for a statement string.



</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_STRING



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the statement string.



</td>
</tr>
<tr>
<td valign="top">

PARTITION\_DEFINITION



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the partition definition after executing the statement.



</td>
</tr>
<tr>
<td valign="top">

OPERATION\_TYPE



</td>
<td valign="top">

VARCHAR\(64\)



</td>
<td valign="top">

Displays the operation type strings. Valid strings include:

-   ADD PARTITION
-   DROP PARTITION
-   ALTER TABLE PARTITION BY
-   MOVE PARTITION
-   ENABLE DYNAMIC RANGE
-   DISABLE DYNAMIC RANGE
-   ALTER PARTITION PROPERTY
-   MERGE PARTITIONS
-   ADD PARTITION FROM OTHERS
-   ADD PARTITION FROM OTHERS FOR INTERVAL
-   DROP EMPTY PARTITIONS



</td>
</tr>
<tr>
<td valign="top">

IS\_ONLINE



</td>
<td valign="top">

VARCHAR\(5\)



</td>
<td valign="top">

Indicates whether DDL is online \(TRUE\) or offline \(FALSE\).



</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_SOURCE



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays source information of the application



</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the application.



</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the application user name.



</td>
</tr>
<tr>
<td valign="top">

CLIENT\_IP



</td>
<td valign="top">

VARCHAR\(45\)



</td>
<td valign="top">

Displays the IP address of the of client machine.



</td>
</tr>
</table>



<a name="loio74efdd0717bd44528263ca684e159635__section_d21_l1h_mqb"/>

## Additional Information

Users with the CATALOG READ system privilege can view information on all records in this system view. Users without this system privilege can only view information on tables that they own.

