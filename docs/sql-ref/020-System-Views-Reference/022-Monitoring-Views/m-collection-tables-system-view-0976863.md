<!-- loio0976863fb6fb4d9fbb67280c834cd7aa -->

# M\_COLLECTION\_TABLES System View

Provides information about JSON collections.



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

CREATE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the creation time of the table collection.

</td>
</tr>
<tr>
<td valign="top">

ESTIMATED\_DOCUMENT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the estimated document count.

</td>
</tr>
<tr>
<td valign="top">

ALLOCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the allocated size of the collection in bytes.

</td>
</tr>
<tr>
<td valign="top">

USED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the used size of the collection in bytes.

</td>
</tr>
<tr>
<td valign="top">

LOAD\_STATUS

</td>
<td valign="top">

NVARCHAR

</td>
<td valign="top">

Displays whether the table collection is LOADED or UNLOADED.

</td>
</tr>
</table>

**Related Information**  


[M\_COLLECTION\_TABLE\_VIRTUAL\_FILES System View](m-collection-table-virtual-files-system-view-cacf365.md "Provides information about the virtual files for JSON collections.")

