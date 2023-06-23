<!-- loio20b0956b7519101499bffea75d727aca -->

# M\_HEAP\_MEMORY System View

Provides memory allocator statistics.



<a name="loio20b0956b7519101499bffea75d727aca___m__h_e_a_p__m_e_m_o_r_y_1struct_M_HEAP_MEMORY"/>

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

Displays the persistence volume ID.



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

Displays the stotal allocated size in this allocator and suballocators in bytes.



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

Displays the largest block size in bytes ever alllocated in this allocator and suballocators.



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

Displays the largest size in bytes of this allocator and suballocators \(estimate\).



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

Displays the average allocated memory in bytes by this allocator and its suballocators, multiplied by the time since the start of measurement \(sample based rough estimate\). Deactivated by default this value should only be activated upon request by SAP support. UOM is 1 byte times 1 second.



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

Displays the largest block size in bytes ever allocated in this allocator.



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

Displays the average allocated memory in bytes by this allocator, multiplied by time since start of measurement \(sample based rough estimate\). Deactivaetd by decault, this value should only be activated upon request by SAP support. UOM is 1 byte times 1 second.



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

Displays the name of SAP HANA component of this allocator.



</td>
</tr>
</table>



<a name="loio20b0956b7519101499bffea75d727aca___m__h_e_a_p__m_e_m_o_r_y_1fulldesc_M_HEAP_MEMORY"/>

## Additional Information

This view contains information about memory consumption of various components in the system. Parallel to heap memory, you can also query memory consumption by connection, statement, and user using the M\_CONTEXT\_MEMORY system view.

The overhead of allocators is not considered in this view.

This view has a resettable counterpart; you can see the values since the last reset in the M\_HEAP\_MEMORY\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_HEAP_MEMORY_RESET;`.

**Related Information**  


[M\_HEAP\_MEMORY\_RESET System View](m-heap-memory-reset-system-view-20b0b89.md "Provides memory allocator statistics since the last reset.")

[M\_HEAP\_MEMORY\_AREAS System View](m-heap-memory-areas-system-view-48893b8.md "Provides memory fragmentation details.")

[M\_CONTEXT\_MEMORY System View](m-context-memory-system-view-20ac657.md "Provides memory allocator statistics.")

[M\_SERVICE\_MEMORY System View](m-service-memory-system-view-20bf33c.md "Displays detailed memory utilization information by services.")

