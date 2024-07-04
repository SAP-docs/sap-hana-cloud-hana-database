<!-- loio20c4ef8375191014bd51ad2f0677db6a -->

# M\_SERVICES System View

Provides the status of all services.



<a name="loio20c4ef8375191014bd51ad2f0677db6a___m__s_e_r_v_i_c_e_s_1struct_M_SERVICES"/>

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

SERVICE\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the service name. See M\_SERVICE\_TYPES for all known service names.

</td>
</tr>
<tr>
<td valign="top">

PROCESS\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the process ID.

</td>
</tr>
<tr>
<td valign="top">

DETAIL

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Internal use only. Use COORDINATOR\_TYPE to test the service role.

</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_STATUS

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the active status: NO, YES, UNKNOWN, STARTING, or STOPPING.

</td>
</tr>
<tr>
<td valign="top">

SQL\_PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the SQL port.

</td>
</tr>
<tr>
<td valign="top">

COORDINATOR\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the coordinator type in the distributed landscape: COORDINATOR, WORKER, STANDBY, or NONE.

</td>
</tr>
<tr>
<td valign="top">

VOLUME\_REPLICATION\_ROLE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the current replication role in the context of System Managed Volume Replication \(SMVR\): NONE \(or empty\), SOURCE, or REPLICA.

</td>
</tr>
<tr>
<td valign="top">

IS\_DATABASE\_LOCAL

</td>
<td valign="top">

NVARCHAR\(2\)

</td>
<td valign="top">

Displays whether or not the service is local to the database.

</td>
</tr>
</table>

**Related Information**  


[ALTER SYSTEM STOP SERVICE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-stop-service-statement-system-management-20d30da.md "Stops single or multiple services on the designated host.")

[ALTER SYSTEM RECONFIGURE SERVICE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-reconfigure-service-statement-system-management-20d23ea.md "Reconfigures a specified service by applying the current configuration parameters.")

[M\_SERVICE\_TYPES System View](m-service-types-system-view-20c4d1d.md "Provides information about service types.")

[Data Storage Security](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/b30fda1483b34628802a8d62bd5d39df.html "Several mechanisms are used to protect security-relevant data used by the SAP HANA Cloud, SAP HANA database from unauthorized access.") :arrow_upper_right:

