<!-- loio20c8d7fe75191014b8cebeafdbafde33 -->

# M\_TRACEFILE\_CONTENTS System View

Provides SAP HANA information from trace files.



<a name="loio20c8d7fe75191014b8cebeafdbafde33___m__t_r_a_c_e_f_i_l_e__c_o_n_t_e_n_t_s_1struct_M_TRACEFILE_CONTENTS"/>

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

OFFSET

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the file offset in bytes.

</td>
</tr>
<tr>
<td valign="top">

CONTENT

</td>
<td valign="top">

NVARCHAR\(1000\)

</td>
<td valign="top">

Displays the file content at the offset.

</td>
</tr>
</table>



<a name="loio20c8d7fe75191014b8cebeafdbafde33___m__t_r_a_c_e_f_i_l_e__c_o_n_t_e_n_t_s_1fulldesc_M_TRACEFILE_CONTENTS"/>

## Additional Information

This view requires an equal predicate on HOST and FILE\_NAME as part of the WHERE clause. Use HOST, FILE\_NAME as returned by the view M\_TRACEFILES to prevent unintentional materialization of all trace files.

The optional WHERE clause `OFFSET<,<=,=,>,>= value` is efficiently handled by this view. With `OFFSET > -value`, you can read from the end of the file without having to know the file size in advance. With `OFFSET <> -value`, you can read from the start and end of a file. Do not use the equivalent `OFFSET < value OR OFFSET >-value` because this is very inefficient for large files and returns duplicates for small files where the file size is < 2\*value.

Trace files typically contain ASCII or CESU-8, but they can also contain binary data. To support all types of data, each byte from the trace file is encoded as one NVARCHAR with values in the range 0 to 255. To recode as CESU-8 you have to use code like in this Python example:

```
cursor.execute(" select CONTENT from M_TRACEFILE_CONTENTS where HOST='...' and FILE_NAME='...' ")
filedata=''
for row in cursor.fetchall():
    filedata += row[1].encode('latin-1') # reinterpret as bytearray
displaydata = filedata.decode('utf-8','replace') # do not use 'strict' error handling
```

**Related Information**  


[M\_TRACEFILES System View](m-tracefiles-system-view-20c8f48.md "Provides information about all trace files.")

[ALTER SYSTEM CLEAR TRACES Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-traces-statement-system-management-20d1281.md "Clears (removes) trace files opened by SAP HANA.")

[ALTER SYSTEM REMOVE TRACES Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-traces-statement-system-management-20d25bf.md "Deletes the trace files on a specified host to reduce the disk space used by large trace files.")

[M\_SERVICE\_TRACES System View](m-service-traces-system-view-20c4b5c.md "Provides configured trace components for each service type.")

