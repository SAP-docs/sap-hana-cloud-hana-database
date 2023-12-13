<!-- loiob58947046b354d0ea1c27af7e21520ff -->

# M\_HOST\_NETWORK\_STATISTICS System View

Provides information about the network statistics of a host.



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

Displays the host name the network statistics refer to.

</td>
</tr>
<tr>
<td valign="top">

TCP\_SEGMENTS\_RECEIVED

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of TCP segments received.

</td>
</tr>
<tr>
<td valign="top">

TCP\_SEGMENTS\_SENT\_OUT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of TCP segments sent out.

</td>
</tr>
<tr>
<td valign="top">

TCP\_SEGMENTS\_RETRANSMITTED

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of TCP segments that had to be retransmitted.

</td>
</tr>
<tr>
<td valign="top">

TCP\_BAD\_SEGMENTS\_RECEIVED

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of TCP segments that were broken upon receiving.

</td>
</tr>
</table>



<a name="loiob58947046b354d0ea1c27af7e21520ff__section_llz_3sp_q2b"/>

## Additional Information

Most columns correspond to the similarly named values reported by `netstat -s`.

**Related Information**  


[M\_HOST\_INFORMATION System View](m-host-information-system-view-20b1002.md "Provides host information such as machine and OS configuration.")

[M\_HOST\_RESOURCE\_UTILIZATION System View](m-host-resource-utilization-system-view-20b1241.md "Provides information about host resource utilization by all processes (including non-SAP HANA processes). CPU time is in milliseconds and added across all cores since system start.")

