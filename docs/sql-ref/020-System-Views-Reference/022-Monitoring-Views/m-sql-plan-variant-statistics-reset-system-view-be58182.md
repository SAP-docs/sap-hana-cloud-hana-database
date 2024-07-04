<!-- loiobe58182f7ecc47f285bd9cfa599688cf -->

# M\_SQL\_PLAN\_VARIANT\_STATISTICS\_RESET System View

Provides statistics of a live variant plan since the last reset.



This view contains values accumulated since the last reset of the main view M\_SQL\_PLAN\_VARIANT\_STATISTICS. Refer to M\_SQL\_PLAN\_VARIANT\_STATISTICS for information about the structure and use of this view.

In addition to the columns mentioned in M\_SQL\_PLAN\_STATISTICS, this view also contains a timestamp field, RESET\_TIME, which indicates the last time the data was reset as the first column.

**Related Information**  


[M\_SQL\_PLAN\_VARIANT\_STATISTICS System View](m-sql-plan-variant-statistics-system-view-b8d14c0.md "Provides statistics for Plan Variant, a method that enables the caching of multiple plans (variant plans) for each parameterized query.")

