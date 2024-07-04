<!-- loio20b071a775191014ab3d92eda7ef62ef -->

# M\_GARBAGE\_COLLECTION\_STATISTICS\_RESET System View

Provides accumulated garbage collection and history manager statistics since the last reset.



This view contains values accumulated since the last reset of the main view M\_GARBAGE\_COLLECTION\_STATISTICS. Refer to M\_GARBAGE\_COLLECTION\_STATISTICS for information about the structure and use of this view.

In addition to the members mentioned in M\_GARBAGE\_COLLECTION\_STATISTICS, this view also contains a timestamp field, RESET\_TIME, which indicates the last time the data was reset.



<a name="loio20b071a775191014ab3d92eda7ef62ef__section_crw_wmj_wbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_GARBAGE\_COLLECTION\_STATISTICS System View](m-garbage-collection-statistics-system-view-20b04b8.md "Provides garbage collection and history manager statistics.")

