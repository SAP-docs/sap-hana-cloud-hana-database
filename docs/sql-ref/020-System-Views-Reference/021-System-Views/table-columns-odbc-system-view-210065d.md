<!-- loio210065d275191014b18ddc68a972679f -->

# TABLE\_COLUMNS\_ODBC System View

Provides information about available table columns.



<a name="loio210065d275191014b18ddc68a972679f___t_a_b_l_e__c_o_l_u_m_n_s__o_d_b_c_1struct_TABLE_COLUMNS_ODBC"/>

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

TABLE\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the table.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the column.

</td>
</tr>
<tr>
<td valign="top">

DATA\_TYPE\_ID

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the SQL data type ID of the column.

</td>
</tr>
<tr>
<td valign="top">

DATA\_TYPE\_NAME

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the SQL data type name of the column.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_SIZE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the total number of characters required to display the value when it is converted to characters.

</td>
</tr>
<tr>
<td valign="top">

BUFFER\_LENGTH

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the length, in bytes, required to transfer the value.

</td>
</tr>
<tr>
<td valign="top">

DECIMAL\_DIGITS

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the total number of significant digits to the right of the decimal point.

</td>
</tr>
<tr>
<td valign="top">

NUM\_PREC\_RADIX

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays how to interpret columns COLUMN\_SIZE and DECIMAL\_DIGITS. For numeric data types either 10 or 2.

</td>
</tr>
<tr>
<td valign="top">

NULLABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the column is allowed to accept null value: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_DEF

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the default value of the column.

</td>
</tr>
<tr>
<td valign="top">

SQL\_DATA\_TYPE

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the SQL data type ID of the column.

</td>
</tr>
<tr>
<td valign="top">

SQL\_DATETIME\_SUB

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the subtype code for datetime data types.

</td>
</tr>
<tr>
<td valign="top">

CHAR\_OCTET\_LENGTH

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the maximum length, in bytes, of a character or binary data type column.

</td>
</tr>
<tr>
<td valign="top">

POSITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the ordinal position of the column in a record.

</td>
</tr>
<tr>
<td valign="top">

COMMENTS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the description for the column.

</td>
</tr>
</table>



<a name="loio210065d275191014b18ddc68a972679f__section_vsg_hxz_2zb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[TABLES System View](tables-system-view-2101973.md "Provides information about tables in the database.")

[TABLE\_COLUMNS System View](table-columns-system-view-2100d33.md "Provides information about available table columns.")

