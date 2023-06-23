<!-- loiode4f805158a84e349504f1f9bc2348cf -->

# M\_CS\_TABLE\_HANDLES System View

Shows the threads waiting for table locks.




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

Displays the schema name as used in SQL.



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

Displays the table name as used in SQL.



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

Displays the unique internal table ID which remains unchanged during rename.



</td>
</tr>
<tr>
<td valign="top">

PART\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the logical partition number, 0 if the table is not partitioned, -1 if the logical partition number may not be retrieved from metadata.



</td>
</tr>
<tr>
<td valign="top">

INTERNAL\_PART\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the internal partition number as used in internal IndexName objects.



</td>
</tr>
<tr>
<td valign="top">

LOCK\_ID



</td>
<td valign="top">

VARCHAR\(20\)



</td>
<td valign="top">

Displays the unique identifier for the table at IndexMgr level, also found in dumps, trace output, etc.



</td>
</tr>
<tr>
<td valign="top">

HANDLE\_ID



</td>
<td valign="top">

VARCHAR\(20\)



</td>
<td valign="top">

Displays the unique memory address of the IndexHandle.



</td>
</tr>
<tr>
<td valign="top">

THREAD\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the thread using the IndexHandle \(when it was acquired\).



</td>
</tr>
<tr>
<td valign="top">

CURRENT\_STATE



</td>
<td valign="top">

VARCHAR\(30\)



</td>
<td valign="top">

Displays the current state of the IndexHandle. Values are: search\_delta, finish\_delta\_merge, delete., etc. It is the lowercase state name with the prefix ns\_ removed.



</td>
</tr>
<tr>
<td valign="top">

NEXT\_STATE



</td>
<td valign="top">

VARCHAR\(30\)



</td>
<td valign="top">

Displays the next state of the IndexHandle when waiting for a lock upgrade. Values are the same as for CURRENT\_STATE.



</td>
</tr>
<tr>
<td valign="top">

INITIAL\_ACQUIRE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp value when IndexHandles are upgraded or downgraded to different states. This preserves the time when the IndexHandle was first acquired along with the table name.



</td>
</tr>
<tr>
<td valign="top">

ACQUIRE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp value for the acquired time.



</td>
</tr>
<tr>
<td valign="top">

QUEUE\_POSITION



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the position within the queue, when waiting; otherwise the value is 0.



</td>
</tr>
</table>

