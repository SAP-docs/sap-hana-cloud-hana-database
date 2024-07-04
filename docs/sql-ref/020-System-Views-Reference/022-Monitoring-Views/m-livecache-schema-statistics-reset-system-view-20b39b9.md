<!-- loio20b39b98751910148b9c9ad78dbcec3f -->

# M\_LIVECACHE\_SCHEMA\_STATISTICS\_RESET System View

Provides accumulated LiveCache schema statistics since the last reset.



This view contains values accumulated since the last reset of the main view M\_LIVECACHE\_SCHEMA\_STATISTICS. Refer to M\_LIVECACHE\_SCHEMA\_STATISTICS for information about the structure and use of this view.

In addition to the fields mentioned in M\_LIVECACHE\_SCHEMA\_STATISTICS, this view also contains a timestamp field, RESET\_TIME, which indicates the last time the data was reset.



<a name="loio20b39b98751910148b9c9ad78dbcec3f__section_jfs_zd1_ybc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_LIVECACHE\_SCHEMA\_STATISTICS System View](m-livecache-schema-statistics-system-view-20b3778.md "Provides accumulated liveCache schema statistics.")

