<!-- loio20c460be751910149173ac5c08d42be5 -->

# M\_SERVICE\_STATISTICS System View

Provides statistics on active services.



<a name="loio20c460be751910149173ac5c08d42be5___m__s_e_r_v_i_c_e__s_t_a_t_i_s_t_i_c_s_1struct_M_SERVICE_STATISTICS"/>

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

Displays the service name.

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

Displays the detail information, similar to COORDINATOR\_TYPE in M\_SERVICES.

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

Displays the active status. This column contains the following values:

-   NO - Displays that the service has not started.
-   YES - Displays that the service has started and is ready for requests.
-   UNKNOWN - Displays the initial state after starting a landscape, or when the state is not known \(for example, after a crash\). If the service does not start within a minute, this state changes to NO.
-   STARTING - Displays that the service is starting. This state might last for several minutes on first startup or recovery.
-   STOPPING - Displays that the service is stopping.



</td>
</tr>
<tr>
<td valign="top">

START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the process start timestamp.

</td>
</tr>
<tr>
<td valign="top">

SYS\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the current system timestamp.

</td>
</tr>
<tr>
<td valign="top">

PROCESS\_CPU

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the CPU usage percentage of the current process. See additional notes after this table.

</td>
</tr>
<tr>
<td valign="top">

PROCESS\_CPU\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the CPU usage of the current process since the start in milliseconds.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_CPU

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the CPU usage percentage of all processes. See additional notes after this table.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_CPU\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the CPU usage of all processes since the start in milliseconds. See additional notes after this table.

</td>
</tr>
<tr>
<td valign="top">

PROCESS\_MEMORY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the process logical memory usage in bytes.

</td>
</tr>
<tr>
<td valign="top">

PROCESS\_PHYSICAL\_MEMORY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the process physical memory usage in bytes.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_MEMORY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the host physical and swap memory usage in bytes.

</td>
</tr>
<tr>
<td valign="top">

AVAILABLE\_MEMORY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the host physical and swap memory size in bytes.

</td>
</tr>
<tr>
<td valign="top">

PHYSICAL\_MEMORY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the host physical memory size in bytes.

</td>
</tr>
<tr>
<td valign="top">

OPEN\_FILE\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of open files.

</td>
</tr>
</table>



<a name="loio20c460be751910149173ac5c08d42be5___m__s_e_r_v_i_c_e__s_t_a_t_i_s_t_i_c_s_1fulldesc_M_SERVICE_STATISTICS"/>

## Additional Information


<dl>
<dt><b>

PROCESS\_CPU , TOTAL\_CPU

</b></dt>
<dd>

PROCESS\_CPU and TOTAL\_CPU contain CPU usage in percent since last select. This select could be done by another user or another session.

To calculate exact CPU usage use 2 selects and this formula:

```
process_cpu = (select2.process_cpu-time - select1.process_cpu_time) / (select2.sys_timestamp - select1.sys_timestamp)
  total_cpu   = (select2.total_cpu_time   - select1.total_cpu_time  ) / (select2.sys_timestamp - select1.sys_timestamp)
```



</dd><dt><b>

TOTAL\_CPU\_TIME

</b></dt>
<dd>

TOTAL\_CPU\_TIME counts the CPU usage as if there would be 1 core. M\_HOST\_RESOURCE\_UTILIZATION shows similar values multiplied by the number of cores.

```
select s.host,s.total_cpu_time,(h.total_cpu_user_time+h.total_cpu_system_time)/i.value 
from m_service_statistics s, m_host_resource_utilization h, m_host_information i
where s.service_name='nameserver' and i.key='cpu_threads'and s.host=h.host and s.host=i.host
```



</dd>
</dl>

**Related Information**  


[M\_HOST\_RESOURCE\_UTILIZATION System View](m-host-resource-utilization-system-view-20b1241.md "Provides information about host resource utilization by all processes (including non-SAP HANA processes). CPU time is in milliseconds and added across all cores since system start.")

[CREATE STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-statistics-statement-data-definition-20d5252.md "Creates data statistic objects that allow the query optimizer to make better decisions for query plans.")

[REFRESH STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/refresh-statistics-statement-data-definition-20fae6d.md "Specifies a column that is part of the data sources.")

[ALTER STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-statistics-statement-data-definition-c656476.md "Alters the properties of a data statistics object.")

[DROP STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-statistics-statement-data-definition-20d7c59.md "Drops user-defined data statistic objects that the query optimizer uses to make decisions for query plans.")

