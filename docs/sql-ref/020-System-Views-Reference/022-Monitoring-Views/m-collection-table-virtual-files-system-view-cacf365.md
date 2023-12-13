<!-- loiocacf365d31424043af7333a4ac15ddc0 -->

# M\_COLLECTION\_TABLE\_VIRTUAL\_FILES System View

Provides information about the virtual files for JSON collections.



<a name="loiocacf365d31424043af7333a4ac15ddc0__section_thx_gtd_dbb"/>

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

Displays the host name.

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

Displays the internal port.

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

COLLECTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the ID of the collection.

</td>
</tr>
<tr>
<td valign="top">

VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the volume ID.

</td>
</tr>
<tr>
<td valign="top">

FILE\_TYPE

</td>
<td valign="top">

NVARCHAR

</td>
<td valign="top">

Displays the type of file.

</td>
</tr>
<tr>
<td valign="top">

INTERNAL\_OBJECT\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the internal identifier for the table.

</td>
</tr>
<tr>
<td valign="top">

FILE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the file.

</td>
</tr>
<tr>
<td valign="top">

CONTAINER\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the container ID.

</td>
</tr>
<tr>
<td valign="top">

PHYSICAL\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the storage size used for the file in bytes.

</td>
</tr>
<tr>
<td valign="top">

PAGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of storage pages used for the file.

</td>
</tr>
</table>

**Related Information**  


[M\_COLLECTION\_TABLES System View](m-collection-tables-system-view-0976863.md "Provides information about JSON collections.")

