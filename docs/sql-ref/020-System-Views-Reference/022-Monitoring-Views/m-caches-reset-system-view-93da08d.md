<!-- loio93da08d1022946358672c925c3498dab -->

# M\_CACHES\_RESET System View

Provides aggregated information on caches since the last reset.



This view contains values accumulated since the last reset of the main view M\_CACHES. Refer to M\_CACHES for information about the structure and use of this view.

In addition to the members mentioned in M\_CACHES, this view also contains a timestamp field, RESET\_TIME, which indicates the last time the data was reset.



<a name="loio93da08d1022946358672c925c3498dab__section_cpj_1yv_rbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_CACHES System View](m-caches-system-view-20a93aa.md "Provides aggregated information on caches.")

