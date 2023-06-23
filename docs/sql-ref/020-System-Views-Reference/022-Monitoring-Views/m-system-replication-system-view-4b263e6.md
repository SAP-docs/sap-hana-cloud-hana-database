<!-- loio4b263e651f6a42cb836d7aff26894bc5 -->

# M\_SYSTEM\_REPLICATION System View

Monitors system replication information.



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

SITE\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the generated site ID.



</td>
</tr>
<tr>
<td valign="top">

SITE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the site name.



</td>
</tr>
<tr>
<td valign="top">

SECONDARY\_SITE\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the generated site ID of the secondary site.



</td>
</tr>
<tr>
<td valign="top">

SECONDARY\_SITE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the secondary logical site name.



</td>
</tr>
<tr>
<td valign="top">

REPLICATION\_MODE



</td>
<td valign="top">

NVARCHAR\(7\)



</td>
<td valign="top">

Displays the configured replication mode:

-   SYNC: the synchronous replication that acknowledges when a buffer has been written to a disk.
-   SYNCMEM: the synchronous replication that acknowledges when a buffer has arrived in the memory.
-   ASYNC: the asynchronous replication.
-   UNKNOWN: set if the replication mode cannot be determined \(for example, if there is a communication error when getting status information from a service\).



</td>
</tr>
<tr>
<td valign="top">

REPLICATION\_STATUS



</td>
<td valign="top">

NVARCHAR\(12\)



</td>
<td valign="top">

Displays the replication status.



</td>
</tr>
<tr>
<td valign="top">

OPERATION\_MODE



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the operation mode.



</td>
</tr>
<tr>
<td valign="top">

SECONDARY\_READ\_ACCESS\_STATUS



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Indicates whether the secondary system is read-enabled and if read access is activated:

-   NOT CONFIGURED: Displays that an operation mode is used that does not allow read access.
-   STOPPED: Displays that the secondary is running in operation mode logreplay\_readaccess, but it is currently stopped.
-   VERSION MISMATCH: Displays that the secondary system is running in operation mode logreplay\_readaccess but read access is internally disabled on the secondary system because it is on a different SAP HANA version than the primary system.
-   INITIALIZING: Displays that the secondary site is running in operation mode logreplay\_readaccess but read access is not yet completely initialized. SQL connections to the secondary system fail in this state.
-   ACTIVE: Displays that the secondary system is running in operation mode logreplay\_readaccess and is initialized for read access. SQL connections are possible in this state.



</td>
</tr>
<tr>
<td valign="top">

TIER



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the tier on which the source site is located.



</td>
</tr>
</table>

