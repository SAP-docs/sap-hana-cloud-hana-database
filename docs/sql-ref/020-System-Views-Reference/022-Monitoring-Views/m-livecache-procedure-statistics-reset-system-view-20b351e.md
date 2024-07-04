<!-- loio20b351e775191014a944caab4d9519da -->

# M\_LIVECACHE\_PROCEDURE\_STATISTICS\_RESET System View

LiveCache procedure statistics \(since last reset\).



This view contains values accumulated since the last reset of the main view M\_LIVECACHE\_PROCEDURE\_STATISTICS. Refer to M\_LIVECACHE\_PROCEDURE\_STATISTICS for information about the structure and use of this view.

In addition to the members mentioned in M\_LIVECACHE\_PROCEDURE\_STATISTICS, this view also contains a timestamp field, RESET\_TIME, which indicates the last time the data was reset.



<a name="loio20b351e775191014a944caab4d9519da__section_ipn_wd1_ybc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_LIVECACHE\_PROCEDURE\_STATISTICS System View](m-livecache-procedure-statistics-system-view-20b32d0.md "Provides accumulated LiveCache procedure statistics.")

