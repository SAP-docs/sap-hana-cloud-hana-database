<!-- loio20be95ce751910149ed6a7149487d7ee -->

# M\_SEQUENCES System View

Provides statistics for sequence caches.



<a name="loio20be95ce751910149ed6a7149487d7ee___m__s_e_q_u_e_n_c_e_s_1struct_M_SEQUENCES"/>

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

HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host where the sequence cache exists. This is only displayed when the cache is greater than 1 and the value has been cached.

</td>
</tr>
<tr>
<td valign="top">

PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the port where the sequence cache exists. This is only displayed when the cache is greater than 1 and the value has been cached.

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

Displays the sequence name.

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

Displays the cache size of the sequence cache in bytes.

</td>
</tr>
<tr>
<td valign="top">

START\_VALUE

</td>
<td valign="top">

DECIMAL

</td>
<td valign="top">

Displays the start value of the sequence cache. This is only displayed when the cache is greater than 1 and the value has been cached.

</td>
</tr>
<tr>
<td valign="top">

END\_VALUE

</td>
<td valign="top">

DECIMAL

</td>
<td valign="top">

Displays the end value of the sequence cache. This is only displayed when the cache is greater than 1 and the value has been cached.

</td>
</tr>
<tr>
<td valign="top">

CURRENT\_VALUE

</td>
<td valign="top">

DECIMAL

</td>
<td valign="top">

Displays the current value of the sequence cache in bytes.

</td>
</tr>
</table>

**Related Information**  


[SEQUENCES System View](../021-System-Views/sequences-system-view-20cf0e7.md "Provides information about available sequences.")

[CREATE SEQUENCE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-sequence-statement-data-definition-20d5092.md "Creates a sequence that generates primary key values that are unique across multiple tables, and for generating default values for a table.")

[ALTER SEQUENCE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-sequence-statement-data-definition-20d06b0.md "Alters an existing sequence.")

[DROP SEQUENCE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-sequence-statement-data-definition-20d7a85.md "Removes a sequence.")

[CURRENT\_UPDATE\_STATEMENT\_SEQUENCE Function \(Miscellaneous\)](../../010-SQL-Reference/011-SQL-Functions/current-update-statement-sequence-function-miscellaneous-9ae97ed.md "Returns the number of write statements that have been issued in a transaction incremented by 1.")

