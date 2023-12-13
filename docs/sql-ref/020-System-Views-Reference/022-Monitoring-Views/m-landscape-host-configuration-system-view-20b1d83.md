<!-- loio20b1d83875191014b028e076c874e9d7 -->

# M\_LANDSCAPE\_HOST\_CONFIGURATION System View

Specifies the host roles in a distributed landscape.



<a name="loio20b1d83875191014b028e076c874e9d7___m__l_a_n_d_s_c_a_p_e__h_o_s_t__c_o_n_f_i_g_u_r_a_t_i_o_n_1struct_M_LANDSCAPE_HOST_CONFIGURATION"/>

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

HOST\_ACTIVE

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the host active status which is a summary of the active values of all the services on that host.

</td>
</tr>
<tr>
<td valign="top">

HOST\_STATUS

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the host status:


<dl>
<dt><b>

OK

</b></dt>
<dd>

The host is operational; the host actual role equals the configured role.



</dd><dt><b>

IGNORE

</b></dt>
<dd>

The host is operational; the host configured as standby is available, but not used.



</dd><dt><b>

INFO

</b></dt>
<dd>

The host is operational; the host actual role is different from the configured role.



</dd><dt><b>

WARNING

</b></dt>
<dd>

The host is not operational; the host should become operational after startup/failover.



</dd><dt><b>

ERROR

</b></dt>
<dd>

The host not operational; the host is in an erroneous state.



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

FAILOVER\_STATUS

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the failover status:


<dl>
<dt><b>

\(empty value\)

</b></dt>
<dd>

No failover is pending or active.



</dd><dt><b>

waiting .. sec

</b></dt>
<dd>

A failure is detected. Waiting is required to prevent an unnecessary failover. A restart of another host does not trigger an immediate failover.



</dd><dt><b>

waiting

</b></dt>
<dd>

A failure is detected. Waiting for another starting host.



</dd><dt><b>

failover to 'host'

</b></dt>
<dd>

Failover to an active host named 'host'.



</dd><dt><b>

failback to 'host'

</b></dt>
<dd>

Failback to worker host active. This happens when a standby host was assigned and is stopped. There is no automatic failback while the standby host is assigned because this would cause downtime.



</dd><dt><b>

failed

</b></dt>
<dd>

The failover failed. See `nameserver.trc` for details



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

FAILOVER\_CONFIG\_GROUP

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the configured failover group.

Hosts can be grouped and during failover a host is looked for within the same group. If no host is available in the same group, hosts from other groups are used.

</td>
</tr>
<tr>
<td valign="top">

FAILOVER\_ACTUAL\_GROUP

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the actual failover group.

</td>
</tr>
<tr>
<td valign="top">

NAMESERVER\_CONFIG\_ROLE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the nameserver configured roles: COORDINATOR/WORKER. During installation, up to 3 hosts are automatically configured as coordinator candidates. All others are worker.

</td>
</tr>
<tr>
<td valign="top">

NAMESERVER\_ACTUAL\_ROLE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the nameserver actual roles: COORDINATOR/WORKER. Exactly one of the candidates is coordinator and all others are worker.

The primary name server and primary index server are both on the same host.

</td>
</tr>
<tr>
<td valign="top">

INDEXSERVER\_CONFIG\_ROLE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the indexserver configured roles: WORKER/STANDBY.

During SAP HANA system installation or host addition, hosts can be assigned the SAP HANA server roles WORKER or STANDBY. The host can also be assigned other roles.

</td>
</tr>
<tr>
<td valign="top">

INDEXSERVER\_ACTUAL\_ROLE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the indexserver roles: COORDINATOR, WORKER, or STANDBY. Exactly one host is coordinator and all others are worker or STANDBY.

</td>
</tr>
<tr>
<td valign="top">

HOST\_CONFIG\_ROLES

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host's configured database and SAP HANA option roles: ETS\_WORKER, ETS\_STANDBY, STANDBY, STREAMING, WORKER, XS\_WORKER, or XS\_STANDBY.

</td>
</tr>
<tr>
<td valign="top">

HOST\_ACTUAL\_ROLES

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host's current database and SAP HANA option roles: ETS\_WORKER, ETS\_STANDBY, STANDBY, STREAMING, WORKER, XS\_WORKER, or XS\_STANDBY.

</td>
</tr>
<tr>
<td valign="top">

STORAGE\_CONFIG\_PARTITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the stable subpath to reassign the same storage partition after failovers.

</td>
</tr>
<tr>
<td valign="top">

STORAGE\_ACTUAL\_PARTITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the unique number of the mount sub-directory used by the host for storing data and logs \(also known as the "subpath"\).

</td>
</tr>
<tr>
<td valign="top">

WORKER\_CONFIG\_GROUPS

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the stable classification values to assign hosts to logical worker groups.

</td>
</tr>
<tr>
<td valign="top">

WORKER\_ACTUAL\_GROUPS

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the current classification values to assign hosts to logical worker groups.

</td>
</tr>
<tr>
<td valign="top">

VOLUME\_REPLICATION\_GROUPS

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the System Managed Volume Replication \(SMVR\) groups assigned to this host.

</td>
</tr>
<tr>
<td valign="top">

VOLUME\_REPLICATION\_ACTUAL\_ROLE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the current replication role in the context of System Managed Volume Replication \(SMVR\): NONE \(or empty\), SOURCE, or REPLICA.

</td>
</tr>
<tr>
<td valign="top">

REMOVE\_STATUS

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Removes progress information.

</td>
</tr>
</table>

