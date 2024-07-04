<!-- loioc178ed2e4435410a9d70120b02fbae40 -->

# New and Changed Features in 2024 for SAP HANA Cloud, SAP HANA Database SQL Reference Guide \(New and Changed Features\)

SAP HANA Cloud introduces new and changed features for the SAP HANA Cloud, SAP HANA Database SQL Reference Guide.



<a name="loioc178ed2e4435410a9d70120b02fbae40__section_l3x_gsd_y1c"/>

## QRC 02/2024


<dl>
<dt><b>

M\_HOST\_INFORMATION \(Changed\)

</b></dt>
<dd>

Some fields \(keys\) in the view are hidden and fulfilled with dummy/null values. See [3468710](https://me.sap.com/notes/3468710) for details.



</dd><dt><b>

Heterogeneous Create Partition Clauses and Heterogeneous Alter Partition Clauses \(Changed\)

</b></dt>
<dd>

-   Range generation has been extended to include decreasing and bidirectional dynamic range generation. A new column was added to the TABLE\_PARTITIONS view to display this information.
-   Dynamic range checking can now be set a the table level. A new column was added to the PARTITIONED\_TABLES view to display this information.
-   The *<set\_movable\>* property allows you to control whether a partition is movable. A new column was added to the TABLE\_PARTITIONS and M\_TABLE\_PARTITIONS views to display this information.
-   Table partitions now support dynamic aging. A new column was added to the TABLE\_PARTITIONS view to display this information.
-   [Heterogeneous Create Partition Clauses](010-SQL-Reference/012-SQL-Statements/heterogeneous-create-partition-clauses-d496e58.md), [Heterogeneous Alter Partition Clauses](010-SQL-Reference/012-SQL-Statements/heterogeneous-alter-partition-clauses-a4258b8.md), [TABLE\_PARTITIONS System View](020-System-Views-Reference/021-System-Views/table-partitions-system-view-c81d9be.md), [PARTITIONED\_TABLES System View](020-System-Views-Reference/021-System-Views/partitioned-tables-system-view-cdd4329.md), [M\_TABLE\_PARTITIONS System View](020-System-Views-Reference/022-Monitoring-Views/m-table-partitions-system-view-6e81917.md)



</dd><dt><b>

VIEW\_PARAMETERS, PROCEDURE\_PARAMETERS, FUNCITON\_PARAMETERS System Views \(Changed\)

</b></dt>
<dd>

These views have been extended to include the DEFAULT\_VALUE column, which displays the default value of the object. [FUNCTION\_PARAMETERS System View](020-System-Views-Reference/021-System-Views/function-parameters-system-view-20a4c5c.md), [PROCEDURE\_PARAMETERS System View](020-System-Views-Reference/021-System-Views/procedure-parameters-system-view-20cc6b9.md), [VIEW\_PARAMETERS System View](020-System-Views-Reference/021-System-Views/view-parameters-system-view-45b86e8.md)



</dd><dt><b>

IMPORT FROM Statement \(Changed\)

</b></dt>
<dd>

This statement now supports file-based column mapping. [IMPORT FROM Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-from-statement-data-import-export-20f712e.md)



</dd><dt><b>

CREATE FUZZY SEARCH INDEX Statement \(Changed\)

</b></dt>
<dd>

This statement now supports MIME TYPE and TOKEN SEPARATORS options for text mode searches. [CREATE FUZZY SEARCH INDEX Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-fuzzy-search-index-statement-data-definition-9b79b31.md)



</dd><dt><b>

Managed PSE \(New\)

</b></dt>
<dd>

SAP HANA database now supports managed PSEs. A new system view, MANAGED\_PSES System View, was introduced and several existing system views were extended to support this feature.

See [CREATE PSE Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/create-pse-statement-system-management-4d80bf6.md), [ALTER PSE Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/alter-pse-statement-system-management-9c22c6f.md)[REFRESH PSE Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/refresh-pse-statement-system-management-c2f1007.md), [SET PSE Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/set-pse-statement-system-management-10fe807.md), [UNSET PSE Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/unset-pse-statement-system-management-4082553.md)

See [M\_MANAGED\_PSES System View](020-System-Views-Reference/022-Monitoring-Views/m-managed-pses-system-view-5c745ca.md), [PSES System View](020-System-Views-Reference/021-System-Views/pses-system-view-6d9713d.md), [PSE\_PURPOSE\_OBJECTS System View](020-System-Views-Reference/021-System-Views/pse-purpose-objects-system-view-437cd32.md), [PUBLIC\_KEYS System View](020-System-Views-Reference/021-System-Views/public-keys-system-view-4924523.md), [PSE\_PUBLIC\_KEYS System View](020-System-Views-Reference/021-System-Views/pse-public-keys-system-view-bded95a.md)



</dd><dt><b>

M\_SQL\_PLAN\_VARIANT\_STATISTICS and M\_SQL\_PLAN\_VARIANT\_STATISTICS\_RESET System Views \(New\)

</b></dt>
<dd>

Two new views have been introduced to support Plan Variant. [M\_SQL\_PLAN\_VARIANT\_STATISTICS System View](020-System-Views-Reference/022-Monitoring-Views/m-sql-plan-variant-statistics-system-view-b8d14c0.md), [M\_SQL\_PLAN\_VARIANT\_STATISTICS\_RESET System View](020-System-Views-Reference/022-Monitoring-Views/m-sql-plan-variant-statistics-reset-system-view-be58182.md)



</dd><dt><b>

EXPLAIN PLAN Statement \(Changed\)

</b></dt>
<dd>

You can now specify a variant id when evaluating an execution plan. [EXPLAIN PLAN Statement \(Data Manipulation\)](010-SQL-Reference/012-SQL-Statements/explain-plan-statement-data-manipulation-20d9ec5.md)



</dd>
</dl>



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

Row-level security policies are now supported in SQL Views / Parameterized SQL Views through a structured filter check. [CREATE VIEW Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-view-statement-data-definition-20d5fa9.md), [ALTER VIEW Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/alter-view-statement-data-definition-3bc8951.md), [CREATE STRUCTURED FILTER Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-structured-filter-statement-data-definition-f0238ff.md), [ALTER STRUCTURED FILTER Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/alter-structured-filter-statement-data-definition-07b14e0.md), [DROP STRUCTURED PRIVILEGE Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/drop-structured-privilege-statement-access-control-4742f57.md)



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

