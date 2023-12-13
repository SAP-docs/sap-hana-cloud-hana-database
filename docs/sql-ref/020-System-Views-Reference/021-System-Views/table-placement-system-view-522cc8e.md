<!-- loio522cc8ecebbe4508b572d0f61cec8e28 -->

# TABLE\_PLACEMENT System View

Provides table placement information.



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

GROUP\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the group name.

</td>
</tr>
<tr>
<td valign="top">

GROUP\_TYPE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the group type.

</td>
</tr>
<tr>
<td valign="top">

SUBTYPE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the subtype.

</td>
</tr>
<tr>
<td valign="top">

MIN\_ROWS\_FOR\_PARTITIONING

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum number of rows for partitioning.

</td>
</tr>
<tr>
<td valign="top">

INITIAL\_PARTITIONS

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the initial number of partitions.

</td>
</tr>
<tr>
<td valign="top">

REPARTITIONING\_THRESHOLD

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the repartitioning threshold.

</td>
</tr>
<tr>
<td valign="top">

LOCATION

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the location.

</td>
</tr>
<tr>
<td valign="top">

DYNAMIC\_RANGE\_THRESHOLD

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the dynamic range threshold.

</td>
</tr>
<tr>
<td valign="top">

SAME\_PARTITION\_COUNT

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether to use the same count of partitions for each table belonging to the group: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

PERSISTENT\_MEMORY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the data is loaded in persistent memory: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

PAGE\_LOADABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the data is page loadable: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

REPLICA\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Sets the required number of replicas.

</td>
</tr>
<tr>
<td valign="top">

NUMA\_NODE\_INDEXES

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Sets the allowed numa nodes.

</td>
</tr>
</table>



<a name="loio522cc8ecebbe4508b572d0f61cec8e28__section_bdc_fxz_2zb"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[ALTER SYSTEM ALTER TABLE PLACEMENT Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-alter-table-placement-statement-system-management-0715b97.md "Changes table classification and placement settings for table groups.")

[Table Placement](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/22888f9344954f258284d2dd936d0d0a.html "Table classification and table placement configuration, enhanced by partitioning, build the foundation for controlling the data distribution in a SAP HANA scale-out environment.") :arrow_upper_right:

[TABLES System View](tables-system-view-2101973.md "Provides information about tables in the database.")

[TABLE\_PLACEMENT System View](table-placement-system-view-522cc8e.md "Provides table placement information.")

[TABLE\_PLACEMENT\_LOCATIONS System View](table-placement-locations-system-view-9e74012.md "Provides table placement location information.")

[M\_TABLE\_PLACEMENT\_LOCATIONS System View](../022-Monitoring-Views/m-table-placement-locations-system-view-7ecc1cc.md "Provides table placement location monitoring information.")

[M\_TABLE\_LOCATIONS System View](../022-Monitoring-Views/m-table-locations-system-view-20c65d5.md "Provides information about tables and their logical location. Physical locations are shown in M_TABLE_PERSISTENCE_LOCATIONS.")

