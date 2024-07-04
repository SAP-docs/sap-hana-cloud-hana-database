<!-- loiodc462710a89d4ebc981eda6908db28dc -->

# ALTER SYSTEM \{START | STOP\} CAPTURE ABSTRACT SQL PLAN \(System Management\)

Starts or stops capturing abstract SQL plans for queries that are executed against the database.



## Syntax

```
ALTER SYSTEM START CAPTURE ABSTRACT SQL PLAN
    [ FOR USER <user_name_list> ]
    [ WITH SQL PLAN CACHE ]

| ALTER SYSTEM STOP CAPTURE ABSTRACT SQL PLAN
```



## Syntax Element


<dl>
<dt><b>

START

</b></dt>
<dd>

Starts the collection of abstract SQL plans for newly compiled queries.



</dd>
<dd>


<dl>
<dt><b>

FOR USER *<user\_name\_list\>*

</b></dt>
<dd>

Captures and stores abstract SQL plans for newly compiled queries that are executed by the specified users.

```
<user_name_list>::= <user_name>[, <user_name>]...
```



</dd>
</dl>


<dl>
<dt><b>

WITH SQL PLAN CACHE

</b></dt>
<dd>

Controls whether cached SQL queries in the SQL plan cache are captured. Specify this clause to capture newly compiled SQL queries and capture cached SQL queries. Otherwise, only newly compiled SQL queries are captured \(the default\).

This clause recompiles the queries that are currently cached in the system.



</dd>
</dl>



</dd><dt><b>

STOP

</b></dt>
<dd>

Stops the collection of abstract SQL plans for newly compiled queries.

If a background job is still capturing plans when this statement is executed, then plan stability does not capture any more plans. The stop capture takes effect after the current statement that is being captured is finished.



</dd>
</dl>



## Description

The capture process runs in the background while selected queries are executed.



## Example

Start capturing abstract SQL plans for all database users:

```
ALTER SYSTEM START CAPTURE ABSTRACT SQL PLAN;
```

Capture abstract SQL plans only for the specified users:

```
ALTER SYSTEM START CAPTURE ABSTRACT SQL PLAN FOR USER TESTUSER1, TESTUSER2;
```

**Related Information**  


[SQL Plan Stability](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/deab4aee414e4b00a3df5666a44adfff.html "SQL Plan Stability can be used to guarantee the consistent optimal performance of select statements by capturing query execution plans so that exactly the same plan can be reused when the query is executed again.") :arrow_upper_right:

[ALTER SYSTEM \{ENABLE | DISABLE | REMOVE\} ABSTRACT SQL PLAN \(System Management\)](alter-system-enable-disable-remove-abstract-sql-plan-system-management-031158f.md "Enables or disables execution plan generation for abstract SQL plans, or removes plans from the ABSTRACT_SQL_PLANS table.")

[ALTER SYSTEM \{START | STOP\} APPLY ABSTRACT SQL PLAN \(System Management\)](alter-system-start-stop-apply-abstract-sql-plan-system-management-935ecd1.md "Starts or stops matching executed queries with captured abstract SQL plans.")

[ABSTRACT\_SQL\_PLANS System View](../../020-System-Views-Reference/021-System-Views/abstract-sql-plans-system-view-ba830ef.md "Lists information about abstract SQL plans.")

[M\_ABSTRACT\_SQL\_PLAN\_OVERVIEW System View](../../020-System-Views-Reference/022-Monitoring-Views/m-abstract-sql-plan-overview-system-view-03aa3ad.md "Provides the status of each Plan Stability Manager on every index server in SAP HANA.")

[M\_ABSTRACT\_SQL\_PLAN\_STATISTICS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-abstract-sql-plan-statistics-system-view-35af7f2.md "Provides SQL query runtime statistics.")

