<!-- loio20ac89e1751910149394c799da04a008 -->

# M\_CONTEXT\_MEMORY\_RESET System View

Provides memory allocator statistics since the last reset.



This view contains values accumulated since the last reset of the main view M\_CONTEXT\_MEMORY. Refer to M\_CONTEXT\_MEMORY for information about the structure and use of this view.

In addition to the members mentioned in M\_CONTEXT\_MEMORY, this view also contains a timestamp field, RESET\_TIME, which indicates the last time the data was reset.



<a name="loio20ac89e1751910149394c799da04a008__section_khy_hy5_tbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_CONTEXT\_MEMORY System View](m-context-memory-system-view-20ac657.md "Provides memory allocator statistics.")

