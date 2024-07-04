<!-- loio20b3079f7519101491b1c22f0d951530 -->

# M\_LIVECACHE\_OMS\_VERSIONS System View

Detailed information on the OMS versions that currently exists.



<a name="loio20b3079f7519101491b1c22f0d951530___m__l_i_v_e_c_a_c_h_e__o_m_s__v_e_r_s_i_o_n_s_1struct_M_LIVECACHE_OMS_VERSIONS"/>

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

VERSION\_ID

</td>
<td valign="top">

NVARCHAR\(22\)

</td>
<td valign="top">

Displays the ID of the OMS version.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_DATE

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp of the creation of the OMS version.

</td>
</tr>
<tr>
<td valign="top">

LAST\_OPEN\_DATE

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when the OMS version was opened last.

</td>
</tr>
<tr>
<td valign="top">

IS\_OPEN

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays the flag indicating whether the version is currently open: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the ID of the connection/session that the version is bound to.

</td>
</tr>
<tr>
<td valign="top">

LIVECACHE\_MVCC\_SNAPSHOT\_TIMESTAMP

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the consistent view MVCC snapshot timestamp.

</td>
</tr>
<tr>
<td valign="top">

HEAP\_USAGE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the memory that is currently used by the version in bytes.

</td>
</tr>
<tr>
<td valign="top">

VERSION\_DESCRIPTION

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the description.

</td>
</tr>
</table>



<a name="loio20b3079f7519101491b1c22f0d951530__section_ulf_kb1_ybc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.



<a name="loio20b3079f7519101491b1c22f0d951530___m__l_i_v_e_c_a_c_h_e__o_m_s__v_e_r_s_i_o_n_s_1fulldesc_M_LIVECACHE_OMS_VERSIONS"/>

## Additional Information

Status information is shown for each OMS version that currently exists.

This view can only be used if liveCache is enabled.

**Related Information**  


[HOST_LIVECACHE_OMS_VERSIONS View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2024_3_QRC/en-US/29ffcc773260413481653377de803596.html "Returns LiveCache OMS versions per host status information.") :arrow_upper_right:

[M\_LIVECACHE\_PROCEDURE\_STATISTICS System View](m-livecache-procedure-statistics-system-view-20b32d0.md "Provides accumulated LiveCache procedure statistics.")

[System-Versioned Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/91302b26f62c4433bbc58e0a951cdc1d.html "System-versioned tables are part of the SQL standard. They support the tracking of changes on column store tables by capturing the validity period of each record.") :arrow_upper_right:

