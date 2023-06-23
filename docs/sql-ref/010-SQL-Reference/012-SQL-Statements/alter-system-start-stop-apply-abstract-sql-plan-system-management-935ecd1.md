<!-- loio935ecd1974af406a91bc1cb60a0e5ef5 -->

# ALTER SYSTEM \{START | STOP\} APPLY ABSTRACT SQL PLAN \(System Management\)

Starts or stops matching executed queries with captured abstract SQL plans.



<a name="loio935ecd1974af406a91bc1cb60a0e5ef5__section_qbl_mp2_qz"/>

## Syntax

```
ALTER SYSTEM { START | STOP } APPLY ABSTRACT SQL PLAN
```



<a name="loio935ecd1974af406a91bc1cb60a0e5ef5__section_ky4_3ck_y2b"/>

## Syntax Elements


<dl>
<dt><b>

START

</b></dt>
<dd>

Loads all valid abstract SQL plans from the ABSTRACT\_SQL\_PLANS system table into the plan stability manager.

Wherever possible, any newly compiled SELECT statements are based on the abstract SQL plans. Queries are checked against the stored abstract plans and the abstract plan is used to generate an exection plan. When the plan is invalidated during generating an execution plan due to an error, the reason for the invalidation will be stored in the NOTES column in ABSTRACT\_SQL\_PLANS.



</dd><dt><b>

STOP

</b></dt>
<dd>

Stops the query optimizer from checking queries against stored abstract plans. STOP also unloads all valid abstract SQL plans in the ABSTRACT\_SQL\_PLANS system table from the plan cache; the optimizer stops using abstract SQL plans to execute queries.



</dd>
</dl>



<a name="loio935ecd1974af406a91bc1cb60a0e5ef5__section_ifw_xsz_pz"/>

## Description

Starts or stops matching executed queries with captured abstract SQL plans.

**Plan cache eviction policy:** When this statement is executed, any stored plans with the status **enabled** are evicted.

**Related Information**  


[SQL Plan Stability](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/deab4aee414e4b00a3df5666a44adfff.html "SQL Plan Stability can be used to guarantee the consistent optimal performance of select statements by capturing query execution plans so that exactly the same plan can be reused when the query is executed again.") :arrow_upper_right:

[ALTER SYSTEM \{ADD | REMOVE\} ABSTRACT SQL PLAN FILTER \(System Management\)](alter-system-add-remove-abstract-sql-plan-filter-system-management-9c6ac16.md "Starts or stops capturing abstract SQL plans for queries that match the specified filters.")

[ALTER SYSTEM \{ENABLE | DISABLE | REMOVE\} ABSTRACT SQL PLAN \(System Management\)](alter-system-enable-disable-remove-abstract-sql-plan-system-management-031158f.md "Enables or disables execution plan generation for abstract SQL plans, or removes plans from the ABSTRACT_SQL_PLANS table.")

[ALTER SYSTEM \{START | STOP\} CAPTURE ABSTRACT SQL PLAN \(System Management\)](alter-system-start-stop-capture-abstract-sql-plan-system-management-dc46271.md "Starts or stops capturing abstract SQL plans for queries that are executed against the database.")

[ABSTRACT\_SQL\_PLANS System View](../../020-System-Views-Reference/021-System-Views/abstract-sql-plans-system-view-ba830ef.md "Lists information about abstract SQL plans.")

[M\_ABSTRACT\_SQL\_PLAN\_OVERVIEW System View](../../020-System-Views-Reference/022-Monitoring-Views/m-abstract-sql-plan-overview-system-view-03aa3ad.md "Provides the status of each Plan Stability Manager on every index server in SAP HANA.")

[M\_ABSTRACT\_SQL\_PLAN\_STATISTICS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-abstract-sql-plan-statistics-system-view-35af7f2.md "Provides SQL query runtime statistics.")

