<!-- loio20b26d94751910148765ff319bdcbc72 -->

# M\_LIVECACHE\_CONTAINER\_STATISTICS\_RESET System View

Provides accumulated LiveCache container statistics since last reset.



This view contains values accumulated since the last reset of the main view M\_LIVECACHE\_CONTAINER\_STATISTICS. Refer to M\_LIVECACHE\_CONTAINER\_STATISTICS for information about the structure and use of this view.

In addition to the fields mentioned in M\_LIVECACHE\_CONTAINER\_STATISTICS, this view also contains a timestamp field, RESET\_TIME, which indicates the last time the data was reset.



<a name="loio20b26d94751910148765ff319bdcbc72__section_oll_sb1_ybc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_LIVECACHE\_CONTAINER\_STATISTICS System View](m-livecache-container-statistics-system-view-20b2491.md "Provides accumulated liveCache container statistics.")

