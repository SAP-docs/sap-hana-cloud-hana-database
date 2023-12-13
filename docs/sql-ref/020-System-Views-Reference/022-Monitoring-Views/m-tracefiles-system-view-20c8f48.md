<!-- loio20c8f48075191014b594b63d18f2a08f -->

# M\_TRACEFILES System View

Provides information about all trace files.



<a name="loio20c8f48075191014b594b63d18f2a08f___m__t_r_a_c_e_f_i_l_e_s_1struct_M_TRACEFILES"/>

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

FILE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the file name.

</td>
</tr>
<tr>
<td valign="top">

FILE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the file size in bytes.

</td>
</tr>
<tr>
<td valign="top">

FILE\_MTIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the file date.

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

Shows the used disk space. This can help to identify issues caused by a full disk.

</td>
</tr>
</table>



<a name="loio20c8f48075191014b594b63d18f2a08f___m__t_r_a_c_e_f_i_l_e_s_1fulldesc_M_TRACEFILES"/>

## Additional Information

With the CLEAR command, all files that were opened by a service are removed or reset to size 0. On a distributed system, this command clears all traces on all hosts. .

```
ALTER SYSTEM CLEAR TRACES ('ALERT','CLIENT','CRASHDUMP,'*','INDEXSERVER',...,,'DAEMON' );
```

It can clear different types of files:


<table>
<tr>
<th valign="top">

Name.

</th>
<th valign="top">

Files.

</th>
</tr>
<tr>
<td valign="top">

ALERT.

</td>
<td valign="top">

<service\>alert....trc.

</td>
</tr>
<tr>
<td valign="top">

CLIENT.

</td>
<td valign="top">

localclient\_....trc.

</td>
</tr>
<tr>
<td valign="top">

CRASHDUMP.

</td>
<td valign="top">

\*.crashdump....trc.

</td>
</tr>
<tr>
<td valign="top">

\*.

</td>
<td valign="top">

open \*.trc files of all active services.

</td>
</tr>
<tr>
<td valign="top">

INDEXSERVER,NAMESERVER,...,DAEMON

</td>
<td valign="top">

open \*.trc files of a single service type.

</td>
</tr>
</table>

**Related Information**  


[M\_TRACEFILE\_CONTENTS System View](m-tracefile-contents-system-view-20c8d7f.md "Provides SAP HANA information from trace files.")

[ALTER SYSTEM REMOVE TRACES Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-traces-statement-system-management-20d25bf.md "Deletes the trace files on a specified host to reduce the disk space used by large trace files.")

[ALTER SYSTEM CLEAR TRACES Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-traces-statement-system-management-20d1281.md "Clears (removes) trace files opened by SAP HANA.")

[M\_SERVICE\_TRACES System View](m-service-traces-system-view-20c4b5c.md "Provides configured trace components for each service type.")

