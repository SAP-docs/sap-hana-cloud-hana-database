<!-- loio48893b832d1b4767886764a89588a76b -->

# M\_HEAP\_MEMORY\_AREAS System View

Provides memory fragmentation details.



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

VOLUME\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the persistence volume ID.



</td>
</tr>
<tr>
<td valign="top">

AREA



</td>
<td valign="top">

STRING



</td>
<td valign="top">

Identifies the part of the memory management being used, for example, the PoolAllocator.



</td>
</tr>
<tr>
<td valign="top">

USED\_SIZED



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the bytes in use.



</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total bytes in the area.



</td>
</tr>
</table>

**Related Information**  


[M\_HEAP\_MEMORY System View](m-heap-memory-system-view-20b0956.md "Provides memory allocator statistics.")

[M\_CONTEXT\_MEMORY System View](m-context-memory-system-view-20ac657.md "Provides memory allocator statistics.")

[M\_SERVICE\_MEMORY System View](m-service-memory-system-view-20bf33c.md "Displays detailed memory utilization information by services.")

