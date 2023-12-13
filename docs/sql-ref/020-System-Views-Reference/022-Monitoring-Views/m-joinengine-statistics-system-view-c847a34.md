<!-- loioc847a34e30cc43bca23ae4b297a667f6 -->

# M\_JOINENGINE\_STATISTICS System View

Provides statistics about join engine runtime objects used for column store join operations.



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

Displays the internal port number.

</td>
</tr>
<tr>
<td valign="top">

TRANSLATION\_TABLE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of translation tables.

</td>
</tr>
<tr>
<td valign="top">

TRANSLATION\_TABLE\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the memory used by translation tables in bytes.

</td>
</tr>
<tr>
<td valign="top">

TRANSLATION\_TABLE\_UNLOAD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of translation table unloads.

</td>
</tr>
</table>

**Related Information**  


[M\_JOIN\_DATA\_STATISTICS System View](m-join-data-statistics-system-view-528de29.md "Provides column store join engine join statistics.")

[M\_JOIN\_TRANSLATION\_TABLES System View](m-join-translation-tables-system-view-f4a7c5e.md "Provides column store join engine translation tables statistics.")

