<!-- loio20bcc12e75191014a36fc77b1d8cc961 -->

# M\_SAVEPOINT\_STATISTICS\_RESET System View

Provides the savepoint statistics since the last reset.



This view contains values accumulated since the last reset of the main view M\_SAVEPOINT\_STATISTICS. Refer to M\_SAVEPOINT\_STATISTICS for information about the structure and use of this view.

This view is associated with the ALTER SYSTEM SAVEPOINT statement.

In addition to the members mentioned in M\_SAVEPOINT\_STATISTICS, this view also contains a timestamp field, RESET\_TIME, which indicates the last time the data was reset.

**Related Information**  


[M\_SAVEPOINT\_STATISTICS System View](m-savepoint-statistics-system-view-20bc9a8.md "Provides information about executed savepoints.")

[ALTER SYSTEM SAVEPOINT Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-savepoint-statement-system-management-20d2b6e.md "Executes a database checkpoint on the persistence manager.")

