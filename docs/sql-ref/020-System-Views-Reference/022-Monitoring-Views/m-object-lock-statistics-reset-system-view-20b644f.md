<!-- loio20b644fd751910148feae8bfe4cad717 -->

# M\_OBJECT\_LOCK\_STATISTICS\_RESET System View

Provides lock contention statistics, including lock wait count, wait time, and failed count for each object since the last reset.



This view contains values accumulated since the last reset of the main view M\_OBJECT\_LOCK\_STATISTICS. Refer to M\_OBJECT\_LOCK\_STATISTICS for information about the structure and use of this view.

In addition to the members mentioned in M\_OBJECT\_LOCK\_STATISTICS, this view also contains a timestamp field, RESET\_TIME, which indicates the last time the data was reset.

**Related Information**  


[M\_OBJECT\_LOCK\_STATISTICS System View](m-object-lock-statistics-system-view-20b611c.md "Provides lock contention statistics, including lock wait count, wait time, and failed count, for each object.")

