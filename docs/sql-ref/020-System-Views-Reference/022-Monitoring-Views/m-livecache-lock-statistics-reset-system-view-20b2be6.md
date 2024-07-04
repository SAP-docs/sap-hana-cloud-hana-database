<!-- loio20b2be61751910149bfbd747822d8131 -->

# M\_LIVECACHE\_LOCK\_STATISTICS\_RESET System View

LiveCache lock statistics \(since last reset\).



This view contains values accumulated since the last reset of the main view M\_LIVECACHE\_LOCK\_STATISTICS. Refer to M\_LIVECACHE\_LOCK\_STATISTICS for information about the structure and use of this view.

In addition to the members mentioned in M\_LIVECACHE\_LOCK\_STATISTICS, this view also contains a timestamp field, RESET\_TIME, which indicates the last time the data was reset.



<a name="loio20b2be61751910149bfbd747822d8131__section_e5k_bc1_ybc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_LIVECACHE\_LOCK\_STATISTICS System View](m-livecache-lock-statistics-system-view-20b287a.md "Provides accumulated LiveCache lock statistics.")

