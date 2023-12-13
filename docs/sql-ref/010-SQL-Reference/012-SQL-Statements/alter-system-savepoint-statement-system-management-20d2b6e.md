<!-- loio20d2b6e4751910148f429f70714d1910 -->

# ALTER SYSTEM SAVEPOINT Statement \(System Management\)

Executes a database checkpoint on the persistence manager.



<a name="loio20d2b6e4751910148f429f70714d1910__sql_alter_system_savepoint_1sql_alter_system_savepoint_syntax"/>

## Syntax

```
ALTER SYSTEM SAVEPOINT
```



<a name="loio20d2b6e4751910148f429f70714d1910__sql_alter_system_savepoint_1sql_alter_system_savepoint_description"/>

## Description

A savepoint is a point in time when a complete consistent image of the database is persisted to the disk. The consistent image can be used to restart the database.

Normally a savepoint is executed periodically as configured by the configuration parameter `savepoint_interval_s` in the `[persistence]` section of `global.ini`. For special \(normal test\) purposes, the savepoint can be disabled. In this case, use this command to manually execute a savepoint.

The views associated with the ALTER SYSTEM SAVEPOINT statement are: M\_SAVEPOINTS, M\_SAVEPOINT\_STATISTICS, M\_SAVEPOINT\_STATISTICS\_RESET, and HOST\_SAVEPOINTS.

This statement should not be confused with the SAVEPOINT statement, which performs a transactional savepoint.



<a name="loio20d2b6e4751910148f429f70714d1910__section_qy5_3rr_xrb"/>

## Permissions

To execute a savepoint, you must have the SAVEPOINT ADMIN system privilege.



<a name="loio20d2b6e4751910148f429f70714d1910__sql_alter_system_savepoint_1sql_alter_system_savepoint_examples"/>

## Example

Execute a savepoint on the persistence manager.

```
ALTER SYSTEM SAVEPOINT;
```

**Related Information**  


[M\_SAVEPOINT\_STATISTICS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-savepoint-statistics-system-view-20bc9a8.md "Provides information about executed savepoints.")

[M\_SAVEPOINT\_STATISTICS\_RESET System View](../../020-System-Views-Reference/022-Monitoring-Views/m-savepoint-statistics-reset-system-view-20bcc12.md "Provides the savepoint statistics since the last reset.")

[M\_SAVEPOINTS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-savepoints-system-view-20bdd30.md "Displays current and historical savepoint statistics.")

[HOST_SAVEPOINTS View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2023_4_QRC/en-US/3706a4f73e9745d7ba205784a7025c5f.html "Specifies the current and historical savepoint statistics.") :arrow_upper_right:

[SAVEPOINT Statement \(Transaction Management\)](savepoint-statement-transaction-management-cd4172a.md "Defines a location to which a transaction can return if part of the transaction is conditionally canceled.")

