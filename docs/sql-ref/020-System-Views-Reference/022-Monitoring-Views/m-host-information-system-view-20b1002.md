<!-- loio20b10028751910148c1c9de602d771de -->

# M\_HOST\_INFORMATION System View

Provides host information such as machine and OS configuration.



<a name="loio20b10028751910148c1c9de602d771de___m__h_o_s_t__i_n_f_o_r_m_a_t_i_o_n_1struct_M_HOST_INFORMATION"/>

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

KEY



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the key.



</td>
</tr>
<tr>
<td valign="top">

VALUE



</td>
<td valign="top">

NVARCHAR\(2000\)



</td>
<td valign="top">

Displays the value.



</td>
</tr>
</table>


<table>
<tr>
<th valign="top">

KEY



</th>
<th valign="top">

Description



</th>
<th valign="top">

Requires INIFILE ADMIN



</th>
</tr>
<tr>
<td valign="top">

build\_cloud\_edition



</td>
<td valign="top">

Displays the Cloud version number for Cloud releases.



</td>
<td valign="top">

Y



</td>
</tr>
<tr>
<td valign="top">

build\_version



</td>
<td valign="top">

Displays the build version number. This is the same as M\_DATABASE.VERSION.



</td>
<td valign="top">

N



</td>
</tr>
<tr>
<td valign="top">

timezone\_base\_name



</td>
<td valign="top">

Displays the base time zone name.



</td>
<td valign="top">

Y



</td>
</tr>
<tr>
<td valign="top">

timezone\_dst\_name



</td>
<td valign="top">

Displays the daylight savings time zone name.



</td>
<td valign="top">

Y



</td>
</tr>
<tr>
<td valign="top">

timezone\_name



</td>
<td valign="top">

Displays the time zone name.



</td>
<td valign="top">

Y



</td>
</tr>
<tr>
<td valign="top">

timezone\_offset



</td>
<td valign="top">

Displays the time zone offset to GMT, in seconds.



</td>
<td valign="top">

Y



</td>
</tr>
</table>

**Related Information**  


[M\_HOST\_RESOURCE\_UTILIZATION System View](m-host-resource-utilization-system-view-20b1241.md "Provides information about host resource utilization by all processes (including non-SAP HANA processes). CPU time is in milliseconds and added across all cores since system start.")

[M\_HOST\_NETWORK\_STATISTICS System View](m-host-network-statistics-system-view-b589470.md "Provides information about the network statistics of a host.")

[https://launchpad.support.sap.com/\#/notes/2382421](https://launchpad.support.sap.com/#/notes/2382421)

[https://www.kernel.org/doc/Documentation/networking/ip-sysctl.txt](https://www.kernel.org/doc/Documentation/networking/ip-sysctl.txt)

[https://www.kernel.org/doc/Documentation/sysctl/fs.txt](https://www.kernel.org/doc/Documentation/sysctl/fs.txt)

[https://www.kernel.org/doc/Documentation/sysctl/vm.txt](https://www.kernel.org/doc/Documentation/sysctl/vm.txt)

[How to configure HANA network communication channels – Part1. Public network](https://blogs.sap.com/2018/09/20/how-to-configure-hana-network-communication-channels-part1.-public-network/)

