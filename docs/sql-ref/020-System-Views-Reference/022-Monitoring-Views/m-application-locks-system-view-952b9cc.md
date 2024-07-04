<!-- loio952b9cc66b694f0f87f62c6ec8f20f2f -->

# M\_APPLICATION\_LOCKS System View

Displays the status of currently acquired name locks with detailed information such as lock acquisition time, lock mode.




<table>
<tr>
<th valign="top">

COLUMN\_NAME

</th>
<th valign="top">

DATA\_TYPE

</th>
<th valign="top">

DESCRIPTION

</th>
</tr>
<tr>
<td valign="top">

CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the connection ID.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_OWNER\_TRANSACTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the transaction object ID that owns the lock.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_OWNER\_UPDATE\_TRANSACTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the write transaction ID that owns the lock.

</td>
</tr>
<tr>
<td valign="top">

ACQUIRED\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the lock acquisition time.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_NAME

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the lock name.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_MODE

</td>
<td valign="top">

VARCHAR\(16\)

</td>
<td valign="top">

Displays the lock mode. Valid entries are EXCLUSIVE and SHARED.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_SCOPE

</td>
<td valign="top">

VARCHAR\(16\)

</td>
<td valign="top">

Displays the scope of lock. Valid entries are SESSION and TRANSACTION.

</td>
</tr>
</table>



<a name="loio952b9cc66b694f0f87f62c6ec8f20f2f__section_alk_yj2_qbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

