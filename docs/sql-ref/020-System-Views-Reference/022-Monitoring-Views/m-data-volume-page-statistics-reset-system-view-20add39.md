<!-- loio20add39675191014a479fcde9de7b196 -->

# M\_DATA\_VOLUME\_PAGE\_STATISTICS\_RESET System View

Provides information about FreeBlockManager SizeClass statistics since the last reset.



This view contains values accumulated since the last reset of the main view M\_DATA\_VOLUME\_PAGE\_STATISTICS. Refer to M\_DATA\_VOLUME\_PAGE\_STATISTICS for information about the structure and use of this view.

In addition to the members mentioned in M\_DATA\_VOLUME\_PAGE\_STATISTICS, this view also contains a timestamp field, RESET\_TIME, which indicates the last time the data was reset.



<a name="loio20add39675191014a479fcde9de7b196__section_stw_mcn_vbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_DATA\_VOLUME\_PAGE\_STATISTICS System View](m-data-volume-page-statistics-system-view-20adabc.md "Provides page usage statistics on data volumes.")

