<!-- loioc178ed2e4435410a9d70120b02fbae40 -->

# New and Changed Features in 2024 for SAP HANA Cloud, SAP HANA Database SQL Reference Guide \(New and Changed Features\)

SAP HANA Cloud introduces new and changed features for the SAP HANA Cloud, SAP HANA Database SQL Reference Guide.



<a name="loioc178ed2e4435410a9d70120b02fbae40__section_vrp_tm4_xyb"/>

## QRC 01/2024


<dl>
<dt><b>

M\_SYSTEM\_LIMITS System View \(Changed\)

</b></dt>
<dd>

This view has been modified to display the maximum number of connections value on the MAXIMUM\_NUMBER\_OF\_SESSIONS row. [M\_SYSTEM\_LIMITS System View](020-System-Views-Reference/022-Monitoring-Views/m-system-limits-system-view-20c6023.md)



</dd><dt><b>

M\_CACHE\_ENTRIES System View \(Changed\)

</b></dt>
<dd>

The ENTRY\_HASH column has been added to the view to allow the removal of cache entries by hash value. [M\_CACHE\_ENTRIES System View](020-System-Views-Reference/022-Monitoring-Views/m-cache-entries-system-view-20a907b.md)



</dd><dt><b>

M\_APPLICATION\_LOCKS System View \(New\)

</b></dt>
<dd>

This new system view was added to support the Application Locks feature. For more information on this feature, see [3432435](https://me.sap.com/notes/3432435). [M\_APPLICATION\_LOCKS System View](020-System-Views-Reference/022-Monitoring-Views/m-application-locks-system-view-952b9cc.md)



</dd><dt><b>

M\_TRANSACTIONS and M\_BLOCKED\_TRANSACTIONS System Views \(Changed\)

</b></dt>
<dd>

New columns were added and existing columns modified to support the Application Locks feature. For more information on this feature, see [3432435](https://me.sap.com/notes/3432435). [M\_TRANSACTIONS System View](020-System-Views-Reference/022-Monitoring-Views/m-transactions-system-view-20c9610.md), [M\_BLOCKED\_TRANSACTIONS System View](020-System-Views-Reference/022-Monitoring-Views/m-blocked-transactions-system-view-20a8c51.md)



</dd><dt><b>

STRUCTURED FILTER CHECK \(New\)

</b></dt>
<dd>

Row-level security policies are now supported in SQL Views / Parameterized SQL Views through a structured filter check. [CREATE VIEW Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-view-statement-data-definition-20d5fa9.md), [ALTER VIEW Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/alter-view-statement-data-definition-3bc8951.md), [CREATE STRUCTURED FILTER Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-structured-filter-statement-data-definition-f0238ff.md), [ALTER STRUCUTRED FILTER Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/alter-strucutred-filter-statement-data-definition-07b14e0.md), [DROP STRUCTURED PRIVILEGE Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/drop-structured-privilege-statement-access-control-4742f57.md)



</dd><dt><b>

M\_CONTEXT\_MEMORY System View \(Changed\)

</b></dt>
<dd>

The WORKLOAD\_CLASS\_NAME column has been added to the view to provide information on the corresponding workload class. [M\_CONTEXT\_MEMORY System View](020-System-Views-Reference/022-Monitoring-Views/m-context-memory-system-view-20ac657.md)



</dd><dt><b>

CALL Statement \(Changed\)

</b></dt>
<dd>

The ASYNC keyword has been added to the CALL statement. The keyword creates a ASYNC\_CALL\_ID, which lets you cancel a specific procedure running in the background and view information about the procedure associated with the ID. [CALL Statement \(Procedural\)](010-SQL-Reference/012-SQL-Statements/call-statement-procedural-20d364c.md), [CANCEL ASYNC CALL Statement](010-SQL-Reference/012-SQL-Statements/cancel-async-call-statement-63ae89e.md), [M\_PROCEDURE\_ASYNC\_EXECUTIONS System View](020-System-Views-Reference/022-Monitoring-Views/m-procedure-async-executions-system-view-1478581.md)



</dd><dt><b>

STATEMENT\_EXECUTION\_HOST Function and STATEMENT\_EXECUTION\_PORT Function \(New\)

</b></dt>
<dd>

Two new functions have been added to return the host and port of the node executing the statement. [STATEMENT\_EXECUTION\_HOST Function \(Miscellaneous\)](010-SQL-Reference/011-SQL-Functions/statement-execution-host-function-miscellaneous-d42113d.md), [STATEMENT\_EXECUTION\_PORT Function \(Miscellaneous\)](010-SQL-Reference/011-SQL-Functions/statement-execution-port-function-miscellaneous-4b410dd.md)



</dd><dt><b>

M\_MULTIDIMENSIONAL\_STATEMENTS System View \(Changed\)

</b></dt>
<dd>

Two new columns, EXECUTION\_MEMORY\_SIZE and EXECUTION\_CPU\_TIME have been added to the view. [M\_MULTIDIMENSIONAL\_STATEMENTS System View](020-System-Views-Reference/022-Monitoring-Views/m-multidimensional-statements-system-view-4de7e92.md)



</dd><dt><b>

M\_MULTIDIMENSIONAL\_STATEMENT\_STATISTICS System View \(Changed\)

</b></dt>
<dd>

Several new columns have been added to the view to provide information on execution memory size and execution CPU time. [M\_MULTIDIMENSIONAL\_STATEMENT\_STATISTICS System View](020-System-Views-Reference/022-Monitoring-Views/m-multidimensional-statement-statistics-system-view-5b04f05.md)



</dd><dt><b>

M\_SQL\_PLAN\_CACHE System View \(Changed\)

</b></dt>
<dd>

Two new columns, PREFERRED\_ROUTING\_VOLUME\_IDS and HEX\_REJECTION\_REASON have been added to the view. The size of the LAST\_INVALIDATION\_REASON column has been extended to 500 characters and a timestamp has been added to the displayed reason. [M\_SQL\_PLAN\_CACHE System View](020-System-Views-Reference/022-Monitoring-Views/m-sql-plan-cache-system-view-20c57b8.md)



</dd><dt><b>

M\_REMOTE\_MEMORY\_STATEMENTS System View \(Changed\)

</b></dt>
<dd>

Several new columns have been added to the view to support the SAP Passport in SAP HANA Cloud. [M\_REMOTE\_STATEMENTS System View](020-System-Views-Reference/022-Monitoring-Views/m-remote-statements-system-view-20b9a22.md)



</dd><dt><b>

M\_SQL\_PLAN\_CACHE\_AUTO\_RECOMPILATION\_STATISTICS and M\_SQL\_PLAN\_CACHE\_EXECUTION\_ENGINE\_STATISTICS System View \(New\)

</b></dt>
<dd>

These new views have been added to provide information about plan changes. [M\_SQL\_PLAN\_CACHE\_AUTO\_RECOMPILATION\_STATISTICS System View](020-System-Views-Reference/022-Monitoring-Views/m-sql-plan-cache-auto-recompilation-statistics-system-view-a3cfe60.md), [M\_SQL\_PLAN\_CACHE\_EXECUTION\_ENGINE\_STATISTICS System View](020-System-Views-Reference/022-Monitoring-Views/m-sql-plan-cache-execution-engine-statistics-system-view-ad088a4.md)



</dd><dt><b>

M\_SQL\_PLAN\_ADVISOR System View \(New\)

</b></dt>
<dd>

This new view provides information on the running status of the SQL Plan Advisor. [M\_SQL\_PLAN\_ADVISOR System View](020-System-Views-Reference/022-Monitoring-Views/m-sql-plan-advisor-system-view-afa22f3.md),



</dd><dt><b>

CREATE VIRTUAL FUNCTION Statement \(Procedural\) \(New\)

</b></dt>
<dd>

Creates a virtual table user-defined function \(TUDF\) that points to a remote table user-defined function in another SAP HANA system. [CREATE VIRTUAL FUNCTION Statement \(Procedural\)](010-SQL-Reference/012-SQL-Statements/create-virtual-function-statement-procedural-55d2f44.md),



</dd><dt><b>

M\_MERGED\_TRACES System View \(Changed\)

</b></dt>
<dd>

Two new columns, W3C\_TRACE\_ID and W3C\_SPAN\_ID, were added to show W3C trace context information from trace files. [M\_MERGED\_TRACES System View](020-System-Views-Reference/022-Monitoring-Views/m-merged-traces-system-view-20b52c0.md),



</dd>
</dl>

