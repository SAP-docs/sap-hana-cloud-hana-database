<!-- loio20b0b89f75191014b79bddd68f1bbc56 -->

# M\_HEAP\_MEMORY\_RESET System View

Provides memory allocator statistics since the last reset.



This view contains values accumulated since the last reset of the main view M\_HEAP\_MEMORY. Refer to M\_HEAP\_MEMORY for information about the structure and use of this view.

In addition to the members mentioned in M\_HEAP\_MEMORY, this view also contains a timestamp field, RESET\_TIME, which indicates the last time the data was reset.



<a name="loio20b0b89f75191014b79bddd68f1bbc56__section_elx_pwz_xbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_HEAP\_MEMORY System View](m-heap-memory-system-view-20b0956.md "Provides memory allocator statistics.")

