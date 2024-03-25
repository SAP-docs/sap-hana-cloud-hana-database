<!-- loio20cf0e79751910149462bf9e7d571ab8 -->

# SEQUENCES System View

Provides information about available sequences.



<a name="loio20cf0e79751910149462bf9e7d571ab8___s_e_q_u_e_n_c_e_s_1struct_SEQUENCES"/>

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

Displays the schema name of the sequence.

</td>
</tr>
<tr>
<td valign="top">

SEQUENCE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the sequence.

</td>
</tr>
<tr>
<td valign="top">

SEQUENCE\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the sequence.

</td>
</tr>
<tr>
<td valign="top">

START\_NUMBER

</td>
<td valign="top">

DECIMAL

</td>
<td valign="top">

Displays the start number.

</td>
</tr>
<tr>
<td valign="top">

MIN\_VALUE

</td>
<td valign="top">

DECIMAL

</td>
<td valign="top">

Displays the minimum value of the sequence in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAX\_VALUE

</td>
<td valign="top">

DECIMAL

</td>
<td valign="top">

Displays the maximum value of the sequence in bytes.

</td>
</tr>
<tr>
<td valign="top">

INCREMENT\_BY

</td>
<td valign="top">

DECIMAL

</td>
<td valign="top">

Displays the incremental value.

</td>
</tr>
<tr>
<td valign="top">

IS\_CYCLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the sequence starts with the MIN\_VALUE after having reached the MAX\_VALUE in cases where INCREMENT\_BY is greater than 0, or if the sequence starts with the MAX\_VALUE after having reached the MIN\_VALUE in cases where INCREMENT\_BY is less than 0: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

RESET\_BY\_QUERY

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the reset by query string for the sequence.

</td>
</tr>
<tr>
<td valign="top">

CACHE\_SIZE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the cache size of the sequence in bytes.

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

Displays the creation time of the sequence.

</td>
</tr>
</table>



<a name="loio20cf0e79751910149462bf9e7d571ab8__section_kfp_jsz_2zb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_SEQUENCES System View](../022-Monitoring-Views/m-sequences-system-view-20be95c.md "Provides statistics for sequence caches.")

[CREATE SEQUENCE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-sequence-statement-data-definition-20d5092.md "Creates a sequence that generates primary key values that are unique across multiple tables, and for generating default values for a table.")

[ALTER SEQUENCE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-sequence-statement-data-definition-20d06b0.md "Alters an existing sequence.")

