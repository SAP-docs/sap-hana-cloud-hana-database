<!-- loio1d8ef9ae7a604ccca3798ecb902d4732 -->

# M\_BUFFER\_CACHE\_STATISTICS\_RESET System View

Provides a cache level overview of the configuration, cache status, and memory usage since the last reset.



This view contains values accumulated since the last reset of the main view M\_BUFFER\_CACHE\_STATISTICS. Refer to M\_BUFFER\_CACHE\_STATISTICS for information about the structure and use of this view.

In addition to the members mentioned in M\_BUFFER\_CACHE\_STATISTICS, this view also contains a timestamp field, RESET\_TIME, which indicates the last time the data was reset.



<a name="loio1d8ef9ae7a604ccca3798ecb902d4732__section_tmc_np2_qbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_BUFFER\_CACHE\_STATISTICS System View](m-buffer-cache-statistics-system-view-67939bc.md "Provides a cache level overview of the configuration, cache status, and memory usage.")

