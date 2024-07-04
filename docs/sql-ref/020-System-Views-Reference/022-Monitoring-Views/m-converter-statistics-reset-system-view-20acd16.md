<!-- loio20acd16f751910149e4be808d272e63e -->

# M\_CONVERTER\_STATISTICS\_RESET System View

Provides converter statistics since the last reset.



This view contains values accumulated since the last reset of the main view M\_CONVERTER\_STATISTICS. Refer to M\_CONVERTER\_STATISTICS for information about the structure and use of this view.

In addition to the members mentioned in M\_CONVERTER\_STATISTICS, this view also contains a timestamp field, RESET\_TIME, which indicates the last time the data was reset.



<a name="loio20acd16f751910149e4be808d272e63e__section_wkj_ry5_tbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_CONVERTER\_STATISTICS System View](m-converter-statistics-system-view-20acadb.md "Provides converter statistics.")

