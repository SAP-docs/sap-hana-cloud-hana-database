<!-- loio20ab646a7519101495afecfb0882d10e -->

# M\_CONDITIONAL\_VARIABLES\_RESET System View

Semaphore statistics \(since last reset\) .



This view contains values accumulated since the last reset of the main view M\_CONDITIONAL\_VARIABLES. Refer to M\_CONDITIONAL\_VARIABLES for information about the structure and use of this view. In addition to the members mentioned in M\_CONDITIONAL\_VARIABLES, this view also contains a timestamp field RESET\_TIME, which indicates the last time the data was reset.



<a name="loio20ab646a7519101495afecfb0882d10e__section_bzx_vt5_tbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_CONDITIONAL\_VARIABLES System View](m-conditional-variables-system-view-20ab2f6.md "Provides semaphore statistics.")

