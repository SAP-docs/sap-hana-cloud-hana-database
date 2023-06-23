<!-- loio20bf33c975191014bc16d7ffb7717db2 -->

# M\_SERVICE\_MEMORY System View

Displays detailed memory utilization information by services.



<a name="loio20bf33c975191014bc16d7ffb7717db2___m__s_e_r_v_i_c_e__m_e_m_o_r_y_1struct_M_SERVICE_MEMORY"/>

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

Unit



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

 



</td>
<td valign="top">

Displays the process ID.



</td>
</tr>
<tr>
<td valign="top">

LOGICAL\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the virtual memory size, in bytes, from the operating system perspective.



</td>
</tr>
<tr>
<td valign="top">

PHYSICAL\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the physical resident memory size, in bytes, from the operating system perspective.



</td>
</tr>
<tr>
<td valign="top">

CODE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the code size, including shared libraries in bytes.



</td>
</tr>
<tr>
<td valign="top">

STACK\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the stack size in bytes.



</td>
</tr>
<tr>
<td valign="top">

HEAP\_MEMORY\_ALLOCATED\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the heap part of the memory pool.



</td>
</tr>
<tr>
<td valign="top">

HEAP\_MEMORY\_USED\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the amount of pool heap memory that is in use in bytes.



</td>
</tr>
<tr>
<td valign="top">

SHARED\_MEMORY\_ALLOCATED\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the shared memory part of the memory pool in bytes.



</td>
</tr>
<tr>
<td valign="top">

SHARED\_MEMORY\_USED\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the amount of pool shared memory that is in use in bytes.



</td>
</tr>
<tr>
<td valign="top">

COMPACTORS\_ALLOCATED\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the part of the memory pool that can potentially \(if unpinned\) be freed during a memory shortage in bytes.



</td>
</tr>
<tr>
<td valign="top">

COMPACTORS\_FREEABLE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the memory that can be freed during a memory shortage in bytes.



</td>
</tr>
<tr>
<td valign="top">

ALLOCATION\_LIMIT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the maximum memory pool size in bytes \(configurable value\).



</td>
</tr>
<tr>
<td valign="top">

EFFECTIVE\_ALLOCATION\_LIMIT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the effective maximum memory pool size, in bytes, considering the pool sizes of other processes \(computed value\).



</td>
</tr>
<tr>
<td valign="top">

BLOCKED\_MEMORY\_LIMIT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the minimum guaranteed memory for the process in bytes.



</td>
</tr>
<tr>
<td valign="top">

FREE\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the allocated free memory in bytes.



</td>
</tr>
<tr>
<td valign="top">

MIN\_SEGMENT\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the minimum segment size for getting heap memory from the operating system in bytes.



</td>
</tr>
<tr>
<td valign="top">

VIRTUAL\_ADDRESS\_SPACE\_USED\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the used size of the virtual address space in bytes.



</td>
</tr>
<tr>
<td valign="top">

VIRTUAL\_ADDRESS\_SPACE\_TOTAL\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the total virtual address space for each process in bytes.



</td>
</tr>
<tr>
<td valign="top">

FRAGMENTED\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Byte



</td>
<td valign="top">

Displays the amount of memory held by SAP HANA memory management in bytes. This memory cannot be easily reused for new memory allocations.



</td>
</tr>
<tr>
<td valign="top">

TOTAL\_MEMORY\_USED\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

 



</td>
<td valign="top">

Displays the amount of memory in use from the memory pool in bytes.



</td>
</tr>
</table>

**Related Information**  


[M\_SERVICES System View](m-services-system-view-20c4ef8.md "Provides the status of all services.")

[M\_SERVICE\_COMPONENT\_MEMORY System View](m-service-component-memory-system-view-20bed4f.md "Provides service-specific memory usage by logical component.")

[M\_SERVICE\_STATISTICS System View](m-service-statistics-system-view-20c460b.md "Provides statistics on active services.")

[ALTER SYSTEM STOP SERVICE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-stop-service-statement-system-management-20d30da.md "Stops single or multiple services on the designated host.")

[ALTER SYSTEM RECONFIGURE SERVICE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-reconfigure-service-statement-system-management-20d23ea.md "Reconfigures a specified service by applying the current configuration parameters.")

[SAP HANA Used Memory](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/8d277dcc98a94784a4375c029d19d088.html "The total amount of memory used by SAP HANA is referred to as used memory. It includes program code and stack, all data and system tables, and the memory required for temporary computations.") :arrow_upper_right:

[Memory Sizing](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/bdf26308bb571014b7bcd3bcd586aecd.html "Memory sizing is the process of estimating in advance the amount of memory that will be required to run a certain workload on an SAP HANA database. To understand memory sizing, several questions need to be answered.") :arrow_upper_right:

