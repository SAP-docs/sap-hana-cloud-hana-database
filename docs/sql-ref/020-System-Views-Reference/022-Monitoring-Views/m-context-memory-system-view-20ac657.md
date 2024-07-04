<!-- loio20ac657275191014b707d77a01a7c495 -->

# M\_CONTEXT\_MEMORY System View

Provides memory allocator statistics.



<a name="loio20ac657275191014b707d77a01a7c495___m__c_o_n_t_e_x_t__m_e_m_o_r_y_1struct_M_CONTEXT_MEMORY"/>

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

Displays the internal port number.

</td>
</tr>
<tr>
<td valign="top">

VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the persistence colume ID.

</td>
</tr>
<tr>
<td valign="top">

STATISTICS\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the statistics object unique ID.

</td>
</tr>
<tr>
<td valign="top">

CATEGORY

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the allocator name.

</td>
</tr>
<tr>
<td valign="top">

DEPTH

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the depth.

</td>
</tr>
<tr>
<td valign="top">

INCLUSIVE\_SIZE\_IN\_USE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current size of this allocator, including suballocators in bytes.

</td>
</tr>
<tr>
<td valign="top">

INCLUSIVE\_COUNT\_IN\_USE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of blocks currently in use, including suballocators.

</td>
</tr>
<tr>
<td valign="top">

INCLUSIVE\_ALLOCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total allocated size in this allocator and suballocators in bytes.

</td>
</tr>
<tr>
<td valign="top">

INCLUSIVE\_DEALLOCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total deallocated size in this allocator and suballocators in bytes.

</td>
</tr>
<tr>
<td valign="top">

INCLUSIVE\_ALLOCATED\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of allocations, including suballocators.

</td>
</tr>
<tr>
<td valign="top">

INCLUSIVE\_DEALLOCATED\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of deallocations, including suballocators.

</td>
</tr>
<tr>
<td valign="top">

INCLUSIVE\_MAX\_SINGLE\_ALLOCATION\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the largest block size, in bytes, ever allocated in this allocator and suballocators.

</td>
</tr>
<tr>
<td valign="top">

INCLUSIVE\_PEAK\_ALLOCATION\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the largest size of this allocator and suballocators \(estimate\) in bytes.

</td>
</tr>
<tr>
<td valign="top">

INCLUSIVE\_LIMIT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum allowed memory size of the specified allocator and suballocators in bytes. The limit is not a hard limit and may therefore be violated slightly. It is not possible to set limits for each allocator individually.

</td>
</tr>
<tr>
<td valign="top">

INCLUSIVE\_IN\_USE\_INTEGRAL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average allocated memory by this allocator and its suballocators, multiplied by the time since the start of measurement \(sample based rough estimate\). Deactivated by default, this value should only be activated upon request by SAP support. The UOM is 1 byte times 1 second.

</td>
</tr>
<tr>
<td valign="top">

EXCLUSIVE\_SIZE\_IN\_USE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current size of this allocator in bytes.

</td>
</tr>
<tr>
<td valign="top">

EXCLUSIVE\_COUNT\_IN\_USE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of blocks currently in use.

</td>
</tr>
<tr>
<td valign="top">

EXCLUSIVE\_ALLOCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total allocated size in this allocator in bytes.

</td>
</tr>
<tr>
<td valign="top">

EXCLUSIVE\_DEALLOCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total deallocated size in this allocator in bytes.

</td>
</tr>
<tr>
<td valign="top">

EXCLUSIVE\_ALLOCATED\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of allocations.

</td>
</tr>
<tr>
<td valign="top">

EXCLUSIVE\_DEALLOCATED\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of deallocations.

</td>
</tr>
<tr>
<td valign="top">

EXCLUSIVE\_MAX\_SINGLE\_ALLOCATION\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the largest block size, in bytes, ever allocated in this allocator.

</td>
</tr>
<tr>
<td valign="top">

EXCLUSIVE\_PEAK\_ALLOCATION\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the largest size of this allocator \(estimate\) in bytes.

</td>
</tr>
<tr>
<td valign="top">

EXCLUSIVE\_ALLOC\_ERRORS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of allocation errors.

</td>
</tr>
<tr>
<td valign="top">

EXCLUSIVE\_IN\_USE\_INTEGRAL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average allocated memory by this allocator in byptes, multiplied by the time since the start of measurement \(sample based rough estimate\), Usually deactiveate, this value should only be activated at the requested by SAP support. The UOM is 1 byte times 1 second.

</td>
</tr>
<tr>
<td valign="top">

FLAGS

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the allocator flags.

</td>
</tr>
<tr>
<td valign="top">

COMPONENT

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the name of the SAP HANA component of this allocator.

</td>
</tr>
<tr>
<td valign="top">

WORKLOAD\_CLASS\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the effective workload class.

</td>
</tr>
</table>



<a name="loio20ac657275191014b707d77a01a7c495__section_wm5_xx5_tbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.



<a name="loio20ac657275191014b707d77a01a7c495___m__c_o_n_t_e_x_t__m_e_m_o_r_y_1fulldesc_M_CONTEXT_MEMORY"/>

## Additional Information

This view contains information about memory consumption grouped by connections and users. It does not contain information about all memory, only on memory that can be uniquely associated with either a connection, a statement, or a user.

To see information about allocated memory by component, use the M\_HEAP\_MEMORY system view.

This view has a resettable counterpart; you can see the values since the last reset in the M\_CONTEXT\_MEMORY\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_CONTEXT_MEMORY_RESET;`.

**Related Information**  


[M\_CONTEXT\_MEMORY\_RESET System View](m-context-memory-reset-system-view-20ac89e.md "Provides memory allocator statistics since the last reset.")

[M\_HEAP\_MEMORY System View](m-heap-memory-system-view-20b0956.md "Provides memory allocator statistics.")

[M\_CATALOG\_MEMORY System View](m-catalog-memory-system-view-20a994e.md "Provides memory usage information by catalog manager.")

[Memory Sizing](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/bdf26308bb571014b7bcd3bcd586aecd.html "Memory sizing is the process of estimating in advance the amount of memory that will be required to run a certain workload on an SAP HANA database. To understand memory sizing, several questions need to be answered.") :arrow_upper_right:

[Memory Allocator Statistics](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/546bac9a6f924210aabd34dc90c00e05.html "Detailed information about memory consumption can be found by looking into allocator statistics.") :arrow_upper_right:

[Managing Memory by Object Usage](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/815fd19868d84c13962852faa3b1ee85.html "You can use the Unused Retention Period feature to automatically unload objects from memory which are not being used.") :arrow_upper_right:

