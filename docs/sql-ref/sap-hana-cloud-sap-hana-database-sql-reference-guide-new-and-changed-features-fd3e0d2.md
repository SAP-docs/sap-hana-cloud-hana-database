<!-- loiofd3e0d24c7794cb5968d53cacf4ddb6d -->

# SAP HANA Cloud, SAP HANA Database SQL Reference Guide \(New and Changed Features\)

SAP HANA Cloud introduces new and changed features for the SAP HANA Cloud, SAP HANA Database SQL Reference Guide.



<a name="loiofd3e0d24c7794cb5968d53cacf4ddb6d__section_i4x_tmr_3xb"/>

## QRC 02/2023


<dl>
<dt><b>

M\_VIRTUAL\_TABLE\_REPLICAS System View \(Changed\)

</b></dt>
<dd>

The LAST\_SYNC\_TIME column displays the time of the last replication synchronization.



</dd><dt><b>

M\_SQL\_PLAN\_ADVISOR System View \(New\)

</b></dt>
<dd>

This view provides information on the running status of SQL Plan Advisor. [M\_SQL\_PLAN\_ADVISOR System View](020-System-Views-Reference/022-Monitoring-Views/m-sql-plan-advisor-system-view-afa22f3.md)



</dd><dt><b>

SCORE Function \(Miscellaneous\) \(Changed\)

</b></dt>
<dd>

The SCORE function has been extended to supported new clauses. [SCORE Function \(Miscellaneous\)](010-SQL-Reference/011-SQL-Functions/score-function-miscellaneous-20e6f8e.md)



</dd><dt><b>

GROUP\_SCORE Function \(Miscellaneous\) \(New\)

</b></dt>
<dd>

This new function returns the relevance of grouped records found. [GROUP\_SCORE Function \(Miscellaneous\)](010-SQL-Reference/011-SQL-Functions/group-score-function-miscellaneous-89bc59e.md)



</dd><dt><b>

FIRST\_VALUE Function \(Aggregate\) \(Changed\)

</b></dt>
<dd>

This function now returns spatial data types \(ST\_Geometry, ST\_Point\) when it is executed with spatial types as input parameter. [FIRST\_VALUE Function \(Aggregate\)](010-SQL-Reference/011-SQL-Functions/first-value-function-aggregate-034b175.md)



</dd><dt><b>

LAST\_VALUE Function \(Aggregate\) \(Changed\)

</b></dt>
<dd>

This function now returns spatial data types \(ST\_Geometry, ST\_Point\) when it is executed with spatial types as input parameter. [LAST\_VALUE Function \(Aggregate\)](010-SQL-Reference/011-SQL-Functions/last-value-function-aggregate-32e95b7.md)



</dd><dt><b>

NTH\_VALUE Function \(Aggregate\) \(Changed\)

</b></dt>
<dd>

This function now returns spatial data types \(ST\_Geometry, ST\_Point\) when it is executed with spatial types as input parameter. [NTH\_VALUE Function \(Aggregate\)](010-SQL-Reference/011-SQL-Functions/nth-value-function-aggregate-6522df9.md)



</dd><dt><b>

EXPORT INTO Statement \(Changed\)

</b></dt>
<dd>

The REPLACE option allows you to control the behavior if the export file already exists in the specified directory when performing an EXPORT INTO. [EXPORT INTO Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/export-into-statement-data-import-export-6a6f59b.md)



</dd><dt><b>

AUTHENTICATION\_ERROR\_DETAILS System View \(New\)

</b></dt>
<dd>

This new view displays details of authentication errors occurring during connection using a client or SQL statement. [AUTHENTICATION\_ERROR\_DETAILS System View](020-System-Views-Reference/021-System-Views/authentication-error-details-system-view-818ef2c.md)



</dd><dt><b>

CREATE/ALTER USERGROUPS Statement \(Changed\)

</b></dt>
<dd>

Connection attempts by members of a user group can be restricted using IP / Network addresses. [CREATE USERGROUP Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-usergroup-statement-access-control-9869125.md), [ALTER USERGROUP Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/alter-usergroup-statement-access-control-aa94ca8.md), [USERGROUPS System View](020-System-Views-Reference/021-System-Views/usergroups-system-view-ac342d0.md), [USERGROUP\_CONNECT\_RESTRICTIONS System View](020-System-Views-Reference/021-System-Views/usergroup-connect-restrictions-system-view-57d3364.md)



</dd><dt><b>

REMOTE\_SOURCES System View \(Changed\)

</b></dt>
<dd>

The columns CCM\_CONNECTION\_ID and CCM\_CONNECTION\_VERSION have been added to the view to provide connection information from the Central Connection Management \(CCM\) service. [REMOTE\_SOURCES System View](020-System-Views-Reference/021-System-Views/remote-sources-system-view-20ccdd3.md)



</dd>
</dl>



<a name="loiofd3e0d24c7794cb5968d53cacf4ddb6d__section_cm4_vkz_bwb"/>

## QRC 01/2023


<dl>
<dt><b>

ADD\_WORKDAYS and WORKDAYS\_BETWEEN Function \(Changed\)

</b></dt>
<dd>

-   These functions now support the Factory And Holiday Calendar.
-   The parameters *<table\_name\_suffix\>* and *<client\>* have been added to these functions.
-   [ADD\_WORKDAYS Function \(Datetime\)](010-SQL-Reference/011-SQL-Functions/add-workdays-function-datetime-d22c839.md), [WORKDAYS\_BETWEEN Function \(Datetime\)](010-SQL-Reference/011-SQL-Functions/workdays-between-function-datetime-d232c25.md)



</dd><dt><b>

ALTER SYSTEM \{ADD/ALTER/REMOVE\} STATEMENT HINT Statement \(Changed\)

</b></dt>
<dd>

You can now specify a procedure/function definition for the target query. When specified, the given hint is implicitly applied. [ALTER SYSTEM \{ADD | ALTER | REMOVE\} STATEMENT HINT Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/alter-system-add-alter-remove-statement-hint-statement-system-management-1ec23ef.md)



</dd><dt><b>

ALTER SYSTEM \{ENABLE/DISABLE\} STATEMENT HINT Statement \(Changed\)

</b></dt>
<dd>

You can now specify a procedure/function definition for the target query when enabling or disabling a hint. [ALTER SYSTEM \{ENABLE | DISABLE\} STATEMENT HINT Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/alter-system-enable-disable-statement-hint-statement-system-management-8505e6f.md)



</dd><dt><b>

CREATE/ALTER ROLEGROUP \(Changed\)

</b></dt>
<dd>

The parameter ENABLE | DISABLE ROLE ADMIN allows a user with the object privilege GRANTOR is now able to rescind the special right on this role group for ROLE ADMINS. [CREATE ROLEGROUP Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-rolegroup-statement-access-control-6cf1932.md)



</dd>
<dd>

, [ALTER ROLEGROUP Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/alter-rolegroup-statement-access-control-bb0d9c0.md)



</dd><dt><b>

M\_SQLSCRIPT\_PLAN\_PROFILER\_RESULTS and M\_ACTIVE\_PROCEDURES System Views \(Changed\)

</b></dt>
<dd>

The column STATEMENT\_HASH has been added to these views. [M\_ACTIVE\_PROCEDURES System View](020-System-Views-Reference/022-Monitoring-Views/m-active-procedures-system-view-f3d2330.md), [M\_SQLSCRIPT\_PLAN\_PROFILER\_RESULTS System View](020-System-Views-Reference/022-Monitoring-Views/m-sqlscript-plan-profiler-results-system-view-3f527e6.md)



</dd><dt><b>

SELECT Statement \(Changed\)

</b></dt>
<dd>

A new clause, *<collation\_clause\>* supports collation at the statement. [SELECT Statement \(Data Manipulation\)](010-SQL-Reference/012-SQL-Statements/select-statement-data-manipulation-20fcf24.md)



</dd><dt><b>

M\_DATA\_VOLUME\_RECLAIM\_STATISTICS System View \(New\)

</b></dt>
<dd>

A new view has been introduced to display reclamation statistics on a data volume. [M\_DATA\_VOLUME\_RECLAIM\_STATISTICS System View](020-System-Views-Reference/022-Monitoring-Views/m-data-volume-reclaim-statistics-system-view-a46bcb1.md)



</dd><dt><b>

M\_ABSTRACT\_SQL\_PLAN\_STATISTICS System View \(Changed\)

</b></dt>
<dd>

Several columns have been added to the view to display information on the minimum, maximum, average of CPU time and memory size. [M\_ABSTRACT\_SQL\_PLAN\_STATISTICS System View](020-System-Views-Reference/022-Monitoring-Views/m-abstract-sql-plan-statistics-system-view-35af7f2.md)



</dd><dt><b>

CREATE / ALTER WORKLOAD MAPPINGS Statements \(Changed\)

</b></dt>
<dd>

You can now include APPLICATION SOURCE as a key value when creating and altering workload mappings. The WORKLOAD\_MAPPINGS System View has also been extended to display this value. [CREATE WORKLOAD MAPPING Statement \(Workload Management\)](010-SQL-Reference/012-SQL-Statements/create-workload-mapping-statement-workload-management-996978a.md), [ALTER WORKLOAD MAPPING Statement \(Workload Management\)](010-SQL-Reference/012-SQL-Statements/alter-workload-mapping-statement-workload-management-81fc16b.md), [WORKLOAD\_MAPPINGS System View](020-System-Views-Reference/021-System-Views/workload-mappings-system-view-89a0660.md)



</dd><dt><b>

M\_OUTBOUND\_NETWORK\_IO System View \(New\)

</b></dt>
<dd>

This new view provides REST statistics data, aggregated per SQL statement and categorized as ADMIN/READ/WRITE. [M\_OUTBOUND\_NETWORK\_IO System View](020-System-Views-Reference/022-Monitoring-Views/m-outbound-network-io-system-view-36582b7.md)



</dd>
</dl>



<a name="loiofd3e0d24c7794cb5968d53cacf4ddb6d__section_bzj_ndk_gvb"/>

## QRC 04/2022


<dl>
<dt><b>

M\_REMOTE\_SERVICES System View \(New\)

</b></dt>
<dd>

This new view provides information on outbound connectivity status to external SAP-managed services running in SAP HANA cloud. [M\_REMOTE\_SERVICES System View](020-System-Views-Reference/022-Monitoring-Views/m-remote-services-system-view-a4bbb3b.md)



</dd><dt><b>

CALL Statement \(Changed\)

</b></dt>
<dd>

The CALL statement now supports the cascading of hints into internal SQL statements after optimization. When there are nested CALL statements, CASCADE hints are also propagated into the nested procedures. [CALL Statement \(Procedural\)](010-SQL-Reference/012-SQL-Statements/call-statement-procedural-20d364c.md)



</dd><dt><b>

GRANT Statement \(Changed\)

</b></dt>
<dd>

The PARTITION ADMIN system privilege has been introduced to allow the execution of non-destructive partitioning clauses in the ALTER TABLE Statement. [GRANT Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md), [Non-Heterogeneous Alter Partition Clauses](010-SQL-Reference/012-SQL-Statements/non-heterogeneous-alter-partition-clauses-f7ae27c.md), [Heterogeneous Alter Partition Clauses](010-SQL-Reference/012-SQL-Statements/heterogeneous-alter-partition-clauses-a4258b8.md).



</dd>
</dl>


<dl>
<dt><b>

ALTER SYSTEM ALTER AUDIT LOG Statement \(New\)

</b></dt>
<dd>

The audit log table is now configured to use SAP HANA Native Storage Extensions \(NSE\) by default. You can also choose to load it completely into memory as before. [ALTER SYSTEM ALTER AUDIT LOG \(System Management\)](010-SQL-Reference/012-SQL-Statements/alter-system-alter-audit-log-system-management-f135e4a.md)



</dd>
</dl>


<dl>
<dt><b>

WORKLOAD MAPPINGS System View \(Changed\)

</b></dt>
<dd>

The IS\_VALID column has been added to this view to indicate whether the workload mapping is valid or not. [WORKLOAD\_MAPPINGS System View](020-System-Views-Reference/021-System-Views/workload-mappings-system-view-89a0660.md)



</dd><dt><b>

CREATE AUDIT POICY Statement \(Changed\)

</b></dt>
<dd>

-   You can now specify schema names for some DDL based audit actions. The Audit Actions system view has been extended to include this information. [CREATE AUDIT POLICY Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-audit-policy-statement-access-control-20d3d56.md), [AUDIT\_ACTIONS System View](020-System-Views-Reference/021-System-Views/audit-actions-system-view-b856cdd.md)
-   The audit actions IMPORT, IMPORT SCAN, and EXPORT statements can now be tracked by the audit policy. [CREATE AUDIT POLICY Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-audit-policy-statement-access-control-20d3d56.md)



</dd><dt><b>

M\_CACHE and M\_CACHE\_ENTRIES System Views \(Changed\)

</b></dt>
<dd>

These system views now include information on the time of the last access of the cache instance. [M\_CACHES System View](020-System-Views-Reference/022-Monitoring-Views/m-caches-system-view-20a93aa.md), [M\_CACHE\_ENTRIES System View](020-System-Views-Reference/022-Monitoring-Views/m-cache-entries-system-view-20a907b.md)



</dd><dt><b>

CREATE FUZZY SEARCH INDEX Statement \(Changed\)

</b></dt>
<dd>

Fuzzy search indexes now support NCLOB columns. [CREATE FUZZY SEARCH INDEX Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-fuzzy-search-index-statement-data-definition-9b79b31.md)



</dd>
</dl>



<a name="loiofd3e0d24c7794cb5968d53cacf4ddb6d__section_tbs_tkn_15b"/>

## QRC 03/2022


<dl>
<dt><b>

CREATE CERTIFICATE Statement \(Changed\)

</b></dt>
<dd>

Duplicate certificates are supported as long as a certificate name is specified and unique. [CREATE CERTIFICATE Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/create-certificate-statement-system-management-ba87935.md)



</dd><dt><b>

CREATE REMOTE SOURCE Statement \(Changed\)

</b></dt>
<dd>

The CREATE REMOTE SOURCE statement has been extended to support X509 *<PSE\_name\>*. [CREATE REMOTE SOURCE Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-remote-source-statement-access-control-20d4834.md)



</dd><dt><b>

ALTER SYSTEM REMOVE ABSTRACT SQL PLAN RELATED OBJECT DEFINITION Statement \(Changed\)

</b></dt>
<dd>

You can now remove all or only invalid related objects of the captured plan. Information related to the related object definition have been added to the M\_ABSTRACT\_SQL\_PLAN\_OVERVIEW System View. [ALTER SYSTEM \{ENABLE | DISABLE | REMOVE\} ABSTRACT SQL PLAN \(System Management\)](010-SQL-Reference/012-SQL-Statements/alter-system-enable-disable-remove-abstract-sql-plan-system-management-031158f.md), [M\_ABSTRACT\_SQL\_PLAN\_OVERVIEW System View](020-System-Views-Reference/022-Monitoring-Views/m-abstract-sql-plan-overview-system-view-03aa3ad.md)



</dd><dt><b>

GRANT / REVOKE Statement \(Changed\)

</b></dt>
<dd>

The CREATE ADAPTER system privilege has been added to support the creation of adapters to which object privileges can be granted. The ADAPTERS System View has been modified to display information on this new type of adapter. [GRANT Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md), [REVOKE Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/revoke-statement-access-control-20fc91c.md), [ADAPTERS System View](020-System-Views-Reference/021-System-Views/adapters-system-view-6d91840.md)



</dd><dt><b>

AUDIT\_LOG System View \(Changed\)

</b></dt>
<dd>

SAP passport information has been added to the AUDIT\_LOG System View to assist in the analysis of errors related to SAP Passport. [AUDIT\_LOG System View](020-System-Views-Reference/021-System-Views/audit-log-system-view-d1fe124.md)



</dd><dt><b>

CREATE AUDIT POLICY Statement \(Changed\)

</b></dt>
<dd>

Audit policies now supports the specification of usergroups in addition to users for explicit inclusion or exclusion in the logging of audit events. The AUDIT\_POLICIES System View has been modified to reflect this changed. [CREATE AUDIT POLICY Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-audit-policy-statement-access-control-20d3d56.md), [AUDIT\_POLICIES System View](020-System-Views-Reference/021-System-Views/audit-policies-system-view-209e4d3.md)



</dd><dt><b>

CREATE FUZZY SEARCH INDEX Statement \(Changed\)

</b></dt>
<dd>

Fuzzy search indexes now support NCLOB columns. [CREATE FUZZY SEARCH INDEX Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-fuzzy-search-index-statement-data-definition-9b79b31.md)



</dd>
</dl>



## QRC 02/2022


<dl>
<dt><b>

IMPORT / IMPORT FROM / IMPORT SCAN Statements \(Changed\)

</b></dt>
<dd>

You can now import from publicly readable cloud storage. [IMPORT Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-statement-data-import-export-20f75ad.md), [IMPORT FROM Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-from-statement-data-import-export-20f712e.md), [IMPORT SCAN Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-scan-statement-data-import-export-20f79b2.md)



</dd><dt><b>

CREATE WORKLOAD CLASS Statement \(Changed\)

</b></dt>
<dd>

Some limitations to support thread limits on hierarchical workload class have been removed. [CREATE WORKLOAD CLASS Statement \(Workload Management\)](010-SQL-Reference/012-SQL-Statements/create-workload-class-statement-workload-management-dc417c3.md)



</dd><dt><b>

M\_PREPARED\_STATEMENTS and M\_ACTIVE\_STATEMENTS System Views \(Changed\)

</b></dt>
<dd>

These views have been enhanced to support thread limits. [M\_PREPARED\_STATEMENTS System View](020-System-Views-Reference/022-Monitoring-Views/m-prepared-statements-system-view-20b7ea5.md), [M\_ACTIVE\_STATEMENTS System View](020-System-Views-Reference/022-Monitoring-Views/m-active-statements-system-view-d20500a.md)



</dd><dt><b>

M\_CS\_TABLE\_LOCKS and M\_CS\_TABLE\_HANDLES System Views \(New\)

</b></dt>
<dd>

Two public monitoring views are now available to provide information about locked tables and threads waiting to lock tables, from the perspective of the Column Store lock manager \(IndexMgr\). [M\_CS\_TABLE\_HANDLES System View](020-System-Views-Reference/022-Monitoring-Views/m-cs-table-handles-system-view-de4f805.md), [M\_CS\_TABLE\_LOCKS System View](020-System-Views-Reference/022-Monitoring-Views/m-cs-table-locks-system-view-d1e5888.md)



</dd><dt><b>

CREATE FUZZY SEARCH INDEX Statement \(New\)

</b></dt>
<dd>

You can now create a fuzzy search index on NVARCHAR and NCLOB columns. The index name has also been added to the M\_FUZZY\_SEACH INDEXES system view. [CREATE FUZZY SEARCH INDEX Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-fuzzy-search-index-statement-data-definition-9b79b31.md), [M\_FUZZY\_SEARCH\_INDEXES System View](020-System-Views-Reference/022-Monitoring-Views/m-fuzzy-search-indexes-system-view-20b027c.md)



</dd><dt><b>

TABLE\_COLUMNS System View \(Changed\)

</b></dt>
<dd>

The size of the FUZZY\_SEARCH\_MODE column has been increased to display 32 characters. [TABLE\_COLUMNS System View](020-System-Views-Reference/021-System-Views/table-columns-system-view-2100d33.md)



</dd><dt><b>

EFFECTIVE\_PRIVILEGES and EFFECTIVE\_ROLES System Views \(Changed\)

</b></dt>
<dd>

Three new columns have been added to the view to support searches for effective privileges and roles, respectively, for a given role. [EFFECTIVE\_PRIVILEGES System View](020-System-Views-Reference/021-System-Views/effective-privileges-system-view-20a2f3e.md), [EFFECTIVE\_ROLES System View](020-System-Views-Reference/021-System-Views/effective-roles-system-view-20a3229.md)



</dd><dt><b>

GRANT / REVOKE Statement \(Changed\)

</b></dt>
<dd>

Two new privileges, DROP and GRANTOR, have been added to the GRANT and REVOKE statements to control the ability to manage user groups. [GRANT Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md), [REVOKE Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/revoke-statement-access-control-20fc91c.md)



</dd><dt><b>

Arrays \(Changed\)

</b></dt>
<dd>

You can now use a SQL parameter or SQLScript variable as an array index. For example:

```
CREATE TABLE T1(ARR INT ARRAY);
INSERT INTO T1 VALUES (ARRAY(1,2,3,4));
SELECT ARR[?] FROM T1;
```

[Multi-valued Data Types](010-SQL-Reference/multi-valued-data-types-cae8b00.md)



</dd><dt><b>

M\_TABLE\_PARTITIONS System View \(Changed\)

</b></dt>
<dd>

The column PERSISTENT\_MEMORY\_SIZE\_IN\_TOTAL has been added to the view to display persistent memory consumption \(in bytes\) for every column store table. [M\_TABLE\_PARTITIONS System View](020-System-Views-Reference/022-Monitoring-Views/m-table-partitions-system-view-6e81917.md)



</dd>
</dl>



<a name="loiofd3e0d24c7794cb5968d53cacf4ddb6d__section_flg_v5h_yrb"/>

## QRC 01/2022


<dl>
<dt><b>

ALTER TABLE Statement \(Changed\)

</b></dt>
<dd>

Non-heterogeneous partitioned tables now support the AT LOCATION clause with the MERGE PARTITIONS clause. [Non-Heterogeneous Alter Partition Clauses](010-SQL-Reference/012-SQL-Statements/non-heterogeneous-alter-partition-clauses-f7ae27c.md)



</dd><dt><b>

CREATE/ALTER JWT and CREATE/ALTER SAML PROVIDER Statements \(Changed\)

</b></dt>
<dd>

Automatic user creation is now supported for SAML and JWT with LDAP authorization. The JWT and SAML system views have been update to reflect this information. [CREATE JWT PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-jwt-provider-statement-access-control-bfe3daf.md), [ALTER JWT PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/alter-jwt-provider-statement-access-control-61863f6.md), [CREATE SAML PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-saml-provider-statement-access-control-20d4cca.md), [ALTER SAML PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/alter-saml-provider-statement-access-control-20d04f7.md), [JWT\_PROVIDERS System View](020-System-Views-Reference/021-System-Views/jwt-providers-system-view-3df748d.md), [SAML\_PROVIDERS System View](020-System-Views-Reference/021-System-Views/saml-providers-system-view-20cda7b.md)



</dd><dt><b>

CREATE/ALTER TABLE Statement - PRIMARY KEY CHECK \(Changed\)

</b></dt>
<dd>

SAP HANA database now supports the performance of primary key checks on partitions. [Heterogeneous Create Partition Clauses](https://help.sap.com/viewer/c1d3f60099654ecfb3fe36ac93c121bb/latest/en-US/d496e58ce9b54bac9674beda4a636946.html), [Heterogeneous Alter Partition Clauses](https://help.sap.com/viewer/c1d3f60099654ecfb3fe36ac93c121bb/latest/en-US/a4258b865710423b8712b06fb5b8e7c5.html), [Non-heterogeneous Create Partition Clauses](https://help.sap.com/viewer/c1d3f60099654ecfb3fe36ac93c121bb/latest/en-US/ca6a99bbfcd94be9ab8020a86f43caae.html), [Non-heterogeneous Alter Partition Clauses](https://help.sap.com/viewer/c1d3f60099654ecfb3fe36ac93c121bb/latest/en-US/f7ae27ca1b954471a4e1a7feab2c24d7.html)



</dd><dt><b>

GRANT/REVOKE Statements \(Changed\)

</b></dt>
<dd>

Within the GRANT and REVOKE statements, when granting roles in a role group, the USING GROUP clause allows the role group, instead of the executing user, to be the grantor. System views have been updated to include role group as a valid grantor type. [GRANT Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md), [REVOKE Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/revoke-statement-access-control-20fc91c.md), [EFFECTIVE\_ROLES System View](020-System-Views-Reference/021-System-Views/effective-roles-system-view-20a3229.md), [EFFECTIVE\_ROLE\_GRANTEES System View](020-System-Views-Reference/021-System-Views/effective-role-grantees-system-view-d2beddd.md), [GRANTED\_ROLES System View](020-System-Views-Reference/021-System-Views/granted-roles-system-view-20a5c3b.md)



</dd><dt><b>

IMPORT FROM / EXPORT INTO Statements \(Changed\)

</b></dt>
<dd>

The EXPORT INTO and IMPORT FROM statements now supports the JSON file type. [IMPORT FROM Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-from-statement-data-import-export-20f712e.md), [EXPORT INTO Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/export-into-statement-data-import-export-6a6f59b.md)



</dd><dt><b>

IMPORT/EXPORT, IMPORT FROM/EXPORT TO, and IMPORT SCAN Statements \(Changed\)

</b></dt>
<dd>

The import and export functionality now supports SAP HANA Cloud, data lake Files. [IMPORT Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-statement-data-import-export-20f75ad.md),[IMPORT FROM Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-from-statement-data-import-export-20f712e.md), [IMPORT SCAN Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-scan-statement-data-import-export-20f79b2.md),[EXPORT Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/export-statement-data-import-export-20da0be.md), [EXPORT INTO Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/export-into-statement-data-import-export-6a6f59b.md) 



</dd><dt><b>

SELECT Statement \(Changed\)

</b></dt>
<dd>

The SELECT statement now supports the parameters WAIT, NOWAIT, and IGNORE LOCKED in the FOR SHARE LOCK clause.[SELECT Statement \(Data Manipulation\)](010-SQL-Reference/012-SQL-Statements/select-statement-data-manipulation-20fcf24.md)



</dd><dt><b>

SET | UNSET ROLEGROUPS Statements \(New\)

</b></dt>
<dd>

You can define a role group to which each subsequently created role is automatically assigned until the value is unset. [SET ROLEGROUP Statement \(Session Management\)](010-SQL-Reference/012-SQL-Statements/set-rolegroup-statement-session-management-6e62e7e.md), [UNSET ROLEGROUP Statement \(Session Management\)](010-SQL-Reference/012-SQL-Statements/unset-rolegroup-statement-session-management-2f2ee71.md), [CURRENT\_ROLEGROUP Function \(Miscellaneous\)](010-SQL-Reference/011-SQL-Functions/current-rolegroup-function-miscellaneous-5132e3b.md)



</dd><dt><b>

SET | UNSET USERGROUPS Statements \(New\)

</b></dt>
<dd>

You can define a user group to which each subsequently created user is automatically assigned until the value is unset. [SET USERGROUP Statement \(Session Management\)](010-SQL-Reference/012-SQL-Statements/set-usergroup-statement-session-management-1991853.md), [UNSET USERGROUP Statement \(Session Management\)](010-SQL-Reference/012-SQL-Statements/unset-usergroup-statement-session-management-996f997.md), [CURRENT\_USERGROUP Function \(Miscellaneous\)](010-SQL-Reference/011-SQL-Functions/current-usergroup-function-miscellaneous-95fb067.md)



</dd>
</dl>



<a name="loiofd3e0d24c7794cb5968d53cacf4ddb6d__section_hx4_bjk_grb"/>

## QRC 04/2021


<dl>
<dt><b>

ROLEGROUPS \(New\)

</b></dt>
<dd>

SAP HANA database now supports role groups, which are new database objects. With new object privileges, they allow for separate administration \(creation/grant/revoke\) of the contained roles between groups and roles without a group. [CREATE ROLEGROUP Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-rolegroup-statement-access-control-6cf1932.md), [DROP ROLEGROUP Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/drop-rolegroup-statement-access-control-9506eaa.md). [CREATE ROLE Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-role-statement-access-control-20d4a23.md), [ALTER ROLE Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/alter-role-statement-access-control-c16ff34.md), [ROLEGROUPS System Views](020-System-Views-Reference/021-System-Views/rolegroups-system-views-5e2b4b9.md)



</dd><dt><b>

SELECT Statement \(Changed\)

</b></dt>
<dd>

The SELECT statement now supports parameterized SQL views. [SELECT Statement \(Data Manipulation\)](010-SQL-Reference/012-SQL-Statements/select-statement-data-manipulation-20fcf24.md)



</dd><dt><b>

ALTER TABLE Statement \(Changed\)

</b></dt>
<dd>

You can now move multiple partitions in parallel and online. [Non-Heterogeneous Alter Partition Clauses](010-SQL-Reference/012-SQL-Statements/non-heterogeneous-alter-partition-clauses-f7ae27c.md), [Heterogeneous Alter Partition Clauses](010-SQL-Reference/012-SQL-Statements/heterogeneous-alter-partition-clauses-a4258b8.md)



</dd><dt><b>

LDAP Functionality \(Changed\)

</b></dt>
<dd>

LDAP automatic user creation is now supported. [CREATE LDAP PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-ldap-provider-statement-access-control-3b72203.md), [ALTER LDAP PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/alter-ldap-provider-statement-access-control-ae9ba28.md), [LDAP\_PROVIDERS System View](020-System-Views-Reference/021-System-Views/ldap-providers-system-view-5b54fe2.md)



</dd><dt><b>

CREATE / ALTER SAML PROVIDER Statements \(Changed\)

</b></dt>
<dd>

You can now specify a value to be used as XS\_APPLICATIONUSER during login. [CREATE SAML PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-saml-provider-statement-access-control-20d4cca.md), [ALTER SAML PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/alter-saml-provider-statement-access-control-20d04f7.md), [SAML\_PROVIDERS System View](020-System-Views-Reference/021-System-Views/saml-providers-system-view-20cda7b.md)



</dd><dt><b>

DELETE Statement \(Changed\)

</b></dt>
<dd>

Rows that are fully contained within given time period now be deleted. [DELETE Statement \(Data Manipulation\)](010-SQL-Reference/012-SQL-Statements/delete-statement-data-manipulation-20d6169.md)



</dd><dt><b>

CREATE / DROP INDEX Statement \(Changed\)

</b></dt>
<dd>

The ONLINE clause now supports non-replicated, non-history tables when creating and dropping a non-unique index on non-paged base columns. [CREATE INDEX Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-index-statement-data-definition-20d44b4.md), [DROP INDEX Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/drop-index-statement-data-definition-20d6f4e.md)



</dd>
</dl>



<a name="loiofd3e0d24c7794cb5968d53cacf4ddb6d__section_w1w_gl3_kqb"/>

## QRC 3/2021


<dl>
<dt><b>

ALTER TABLE Statement \(Changed\)

</b></dt>
<dd>

You can now add a primary key using an existing unique index. [ALTER TABLE Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md)



</dd><dt><b>

ALTER USER Statement \(Changed\)

</b></dt>
<dd>

You can now add multiple mappings between a JWT or SAML provider and a user. When removing these mappings, you can specify an individual mapping or remove all mappings between the user and provider. [ALTER USER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/alter-user-statement-access-control-20d3459.md)



</dd><dt><b>

CREATE / ALTER TABLE Statements \(Changed\)

</b></dt>
<dd>

Dynamic interval now works with TINYINT, SMALLINT, INT, and BIGINT columns. [CREATE TABLE Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md), [ALTER TABLE Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md)



</dd><dt><b>

CREATE USERGROUP \(Changed\)

</b></dt>
<dd>

During the creation of a usergroup, you can enable \(default\) or disable the parameter set. [CREATE USERGROUP Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-usergroup-statement-access-control-9869125.md) 



</dd><dt><b>

CREATE / ALTER WORKLOAD CLASS Statements \(Changed\)

</b></dt>
<dd>

You can now specify a hierarchy for workload classes to inherit TOTAL STATEMENT MEMORY LIMIT from a parent workload class. [CREATE WORKLOAD CLASS Statement \(Workload Management\)](010-SQL-Reference/012-SQL-Statements/create-workload-class-statement-workload-management-dc417c3.md), [ALTER WORKLOAD CLASS Statement \(Workload Management\)](010-SQL-Reference/012-SQL-Statements/alter-workload-class-statement-workload-management-d4b4659.md)



</dd><dt><b>

GRANT / REVOKE Statements \(Changed\)

</b></dt>
<dd>

The USERGROUP OPERATOR object privilege has been renamed to OPERATOR. USERGROUP OPERATOR is still accepted as an alias. [GRANT Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md), [REVOKE Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/revoke-statement-access-control-20fc91c.md)



</dd><dt><b>

IMPORT/EXPORT, IMPORT FROM/EXPORT TO, IMPORT SCAN \(Changed\)

</b></dt>
<dd>

The import and export functionality now supports:

-   the WITH CREDENTIAL parameter which allows the user to define the credentials once and reuse them in subsequent import and export statements. The credentials are no longer entered as plain text.
-   Google Cloud Platform

[CREATE CREDENTIAL Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-credential-statement-access-control-20d3f46.md), [ALTER CREDENTIAL Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/alter-credential-statement-access-control-20cfdad.md), [IMPORT Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-statement-data-import-export-20f75ad.md),[IMPORT FROM Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-from-statement-data-import-export-20f712e.md), [IMPORT SCAN Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-scan-statement-data-import-export-20f79b2.md),[EXPORT Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/export-statement-data-import-export-20da0be.md), [EXPORT INTO Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/export-into-statement-data-import-export-6a6f59b.md) 



</dd><dt><b>

M\_CS\_INDEXES System View \(Changed\)

</b></dt>
<dd>

Four new columns have been added to the view: MEMORY\_SIZE\_IN\_TOTAL, MEMORY\_SIZE\_IN\_CONCAT, MOST\_SELECTIVE\_COLUMN\_NAME, and INVERTED\_INDIVIDUAL\_COST. [M\_CS\_INDEXES System View](020-System-Views-Reference/022-Monitoring-Views/m-cs-indexes-system-view-00257f0.md)



</dd><dt><b>

M\_DELTA\_MERGE\_STATISTICS System View \(Changed\)

</b></dt>
<dd>

Several new columns have been added to the view for improved monitoring. [M\_DELTA\_MERGE\_STATISTICS System View](020-System-Views-Reference/022-Monitoring-Views/m-delta-merge-statistics-system-view-20aed3e.md)



</dd><dt><b>

M\_TABLE\_REPLICATION\_VOLUME\_STATISTICS, M\_TABLE\_REPLICATION\_VOLUME\_STATISTICS\_RESET, M\_TABLE\_REPLICATION\_VOLUME\_HISTORY \(New\)

</b></dt>
<dd>

Three new monitoring views have been introduced for monitoring asynchronous table replication \(ATR\), optimistic synchronous table replication \(OSTR\), and remote table replication \(RTR\). [M\_TABLE\_REPLICATION\_VOLUME\_STATISTICS System View](020-System-Views-Reference/022-Monitoring-Views/m-table-replication-volume-statistics-system-view-425a15e.md), [M\_TABLE\_REPLICATION\_VOLUME\_HISTORY System View](020-System-Views-Reference/022-Monitoring-Views/m-table-replication-volume-history-system-view-ad1b14f.md), [M\_TABLE\_REPLICATION\_VOLUME\_STATISTICS\_RESET System View](020-System-Views-Reference/022-Monitoring-Views/m-table-replication-volume-statistics-reset-system-view-89bc182.md)



</dd><dt><b>

Monitor Table Partition Operations

</b></dt>
<dd>

You can now monitor the history of all partition-relevant operations on a partitioned table.

-   The configuration parameter *enable* in the *table\_partition\_operation\_trace* section in the ALTER SYSTEM ALTER CONFIGURATION statement lets you turn monitoring ON and OFF. [ALTER SYSTEM ALTER CONFIGURATION Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/alter-system-alter-configuration-statement-system-management-20d08a5.md), [SAP HANA Cloud Configuration Parameter Reference](https://help.sap.com/viewer/138dcf7d779543608917a2307a6115f2/latest/en-US/4b4d88980622427ab2d6ca8c05448166.html)
-   The *M\_TABLE\_PARTITION\_OPERATIONS* monitoring view lets you view Partition Operation Tracing information from the memory ring buffer or disk trace files. [M\_TABLE\_PARTITION\_OPERATIONS System View](020-System-Views-Reference/022-Monitoring-Views/m-table-partition-operations-system-view-74efdd0.md)
-   The new *TABLE PARTITION OPERATIONS* trace\_type in the ALTER SYSTEM CLEAR TRACES statement lets you clear the monitored information. [ALTER SYSTEM CLEAR TRACES Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/alter-system-clear-traces-statement-system-management-20d1281.md)



</dd><dt><b>

SESSION USER Data Masking \(Changed\)

</b></dt>
<dd>

Tables and views now support session user data masking. [CREATE TABLE Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md), [ALTER TABLE Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md), [CREATE VIEW Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-view-statement-data-definition-20d5fa9.md), [ALTER VIEW Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/alter-view-statement-data-definition-3bc8951.md), [TABLES System View](020-System-Views-Reference/021-System-Views/tables-system-view-2101973.md), [VIEWS System View](020-System-Views-Reference/021-System-Views/views-system-view-2102bf2.md), [EFFECTIVE\_MASK\_EXPRESSIONS System View](020-System-Views-Reference/021-System-Views/effective-mask-expressions-system-view-aa0a92b.md)



</dd><dt><b>

TRUNCATE TABLE Statement \(Changed\)

</b></dt>
<dd>

You can now truncate a table partition by partition spec. [TRUNCATE TABLE Statement \(Data Manipulation\)](010-SQL-Reference/012-SQL-Statements/truncate-table-statement-data-manipulation-20fe29f.md)



</dd><dt><b>

Use Certificate Names when Creating Certificates \(Changed\)

</b></dt>
<dd>

When creating or dropping certificates and PSEs, you can now specify a certificate name or a certificate id. The CERTIFICATES and PSE\_CERTIFICATES System Views have been updated to include the certificate name. [CREATE CERTIFICATE Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/create-certificate-statement-system-management-ba87935.md), [DROP CERTIFICATE Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/drop-certificate-statement-system-management-b7784cf.md), [ALTER PSE Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/alter-pse-statement-system-management-9c22c6f.md), [CERTIFICATES System View](020-System-Views-Reference/021-System-Views/certificates-system-view-d076e2b.md), [PSE\_CERTIFICATES System View](020-System-Views-Reference/021-System-Views/pse-certificates-system-view-0184e53.md)



</dd>
</dl>



<a name="loiofd3e0d24c7794cb5968d53cacf4ddb6d__section_ygh_yjt_4pb"/>

## QRC 2/2021


<dl>
<dt><b>

M\_OUT\_OF\_MEMORY\_EVENTS System View \(Changed\)

</b></dt>
<dd>

A new column has been introduced: WORKLOAD\_CLASS\_NAME. [M\_OUT\_OF\_MEMORY\_EVENTS System View](020-System-Views-Reference/022-Monitoring-Views/m-out-of-memory-events-system-view-933cf12.md)



</dd><dt><b>

Statement Hint \(Changed\)

</b></dt>
<dd>

The pattern symbol $$?$$ is now supported in the ALTER SYSTEM... STATEMENT HINT statement for add, remote, enable, and disable statement hints with a simple pattern. [ALTER SYSTEM \{ADD | ALTER | REMOVE\} STATEMENT HINT Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/alter-system-add-alter-remove-statement-hint-statement-system-management-1ec23ef.md)



</dd><dt><b>

CREATE/DROP PUBLIC KEYS Statements \(New\)

</b></dt>
<dd>

You can now manage public keys for use with JWT authentication. [CREATE PUBLIC KEY Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/create-public-key-statement-system-management-80bae7b.md), [DROP PUBLIC KEY Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/drop-public-key-statement-system-management-1f935a3.md), [ALTER PSE Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/alter-pse-statement-system-management-9c22c6f.md).

Two new views, PUBLIC\_KEYS and PSE\_PUBLIC\_KEYS have been created to support this management. [PUBLIC\_KEYS System View](020-System-Views-Reference/021-System-Views/public-keys-system-view-4924523.md), [PSE\_PUBLIC\_KEYS System View](020-System-Views-Reference/021-System-Views/pse-public-keys-system-view-bded95a.md)



</dd><dt><b>

CURRENT\_TIMESTAMP and CURRENT\_UTCTIMESTAMP Functions \(Changed\)

</b></dt>
<dd>

You can now specify the precision \(0-7\) of the number of sub-seconds to display. [CURRENT\_TIMESTAMP Function \(Datetime\)](010-SQL-Reference/011-SQL-Functions/current-timestamp-function-datetime-20de551.md), [CURRENT\_UTCTIMESTAMP Function \(Datetime\)](010-SQL-Reference/011-SQL-Functions/current-utctimestamp-function-datetime-20e0f06.md)



</dd><dt><b>

JSON\_TABLE Function \(Changed\)

</b></dt>
<dd>

This function now supports different JSON path expressions depending on their location in grammar and corresponding error types. [JSON\_TABLE Function \(JSON\)](010-SQL-Reference/011-SQL-Functions/json-table-function-json-f8f6916.md)



</dd><dt><b>

CREATE/ALTER JWT PROVIDER Statements \(Changed\)

</b></dt>
<dd>

The JWT provider now checks for additional claims during authentication. It also allows you to set the XS\_APPLICATIONUSER session variable during login. To support this functionality, PRIORITY has been added to the JWT\_PROVIDERS System View and the JWT\_PROVIDER\_CLAIMS system view has be introduced to view claims defined for a JWT provider. [CREATE JWT PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-jwt-provider-statement-access-control-bfe3daf.md), [ALTER JWT PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/alter-jwt-provider-statement-access-control-61863f6.md), [JWT\_PROVIDERS System View](020-System-Views-Reference/021-System-Views/jwt-providers-system-view-3df748d.md), [JWT\_PROVIDER\_CLAIMS System View](020-System-Views-Reference/021-System-Views/jwt-provider-claims-system-view-86beb3c.md)



</dd>
</dl>



<a name="loiofd3e0d24c7794cb5968d53cacf4ddb6d__section_sgp_qjl_h4b"/>

## QRC 1/2021


<dl>
<dt><b>

ABAP\_DF16RAW\_TO\_SMALLDECIMAL / ABAP\_DF34RAW\_TO\_DECIMAL Statements \(New\)

</b></dt>
<dd>

Two new functions, ABAP\_DF16RAW\_TO\_SMALLDECIMAL and ABAP\_DF34RAW\_TO\_DECIMAL, have been introduced to convert from ABAP decfloat type \(DF16\_RAW and DF34\_RAW\) to HANA decfloat type \(smalldecimal and decimal\). [ABAP\_DF16RAW\_TO\_SMALLDECIMAL Function \(String\)](010-SQL-Reference/011-SQL-Functions/abap-df16raw-to-smalldecimal-function-string-3233450.md), [ABAP\_DF34RAW\_TO\_DECIMAL Function \(String\)](010-SQL-Reference/011-SQL-Functions/abap-df34raw-to-decimal-function-string-d88c19d.md)



</dd><dt><b>

ALTER TABLE..ALTER PARTITION Statements \(Changed\)

</b></dt>
<dd>

You can now specify multiple partition numbers in a comma separated list in ALTER PARTITION clauses. [Non-Heterogeneous Alter Partition Clauses](010-SQL-Reference/012-SQL-Statements/non-heterogeneous-alter-partition-clauses-f7ae27c.md), [Heterogeneous Alter Partition Clauses](010-SQL-Reference/012-SQL-Statements/heterogeneous-alter-partition-clauses-a4258b8.md)



</dd><dt><b>

ALTER VIRTUAL TABLE Statement \(Changed\)

</b></dt>
<dd>

You can now apply single-level range partitioning to snapshot replicas. [ALTER VIRTUAL TABLE Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/alter-virtual-table-statement-data-definition-5182698.md)



</dd><dt><b>

CREATE TABLE and ALTER TABLE Statements \(Changed\)

</b></dt>
<dd>

You can now create system-versioned tables with transactional system-time. [CREATE TABLE Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md), [ALTER TABLE Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md)

You can now group table options for replica tables. [CREATE TABLE Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md), [ALTER TABLE Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md)



</dd><dt><b>

GRANT / REVOKE Statements \(Changed\)

</b></dt>
<dd>

The new object privileges, ALTER, DROP, and REFERENCES, have been added to the PROVIDER object to allow for the management of X.509 providers. [GRANT Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md), [REVOKE Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/revoke-statement-access-control-20fc91c.md)



</dd><dt><b>

HANA\_CLOUD Macro \(New\)

</b></dt>
<dd>

You can now write syntax that distinguishes between SAP HANA Cloud and SAP HANA on-premise. [HANA\_CLOUD Macro](010-SQL-Reference/hana-cloud-macro-6694324.md)



</dd><dt><b>

LDAP Functionality \(New\)

</b></dt>
<dd>

LDAP authentication is now supported. [CREATE LDAP PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-ldap-provider-statement-access-control-3b72203.md), [ALTER LDAP PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/alter-ldap-provider-statement-access-control-ae9ba28.md), [DROP LDAP PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/drop-ldap-provider-statement-access-control-340e913.md)



</dd><dt><b>

M\_BUFFER\_CACHE\_POOL\_STATISTICS System View \(Changed\)

</b></dt>
<dd>

A new column has been introduced: PINNED\_BUFFER\_COUNT. [M\_BUFFER\_CACHE\_POOL\_STATISTICS System View](020-System-Views-Reference/022-Monitoring-Views/m-buffer-cache-pool-statistics-system-view-4c417c7.md)



</dd><dt><b>

M\_BUFFER\_CACHE\_STATISTICS System View \(Changed\)

</b></dt>
<dd>

A new column has been introduced: PINNED\_SIZE. [M\_BUFFER\_CACHE\_STATISTICS System View](020-System-Views-Reference/022-Monitoring-Views/m-buffer-cache-statistics-system-view-67939bc.md)



</dd><dt><b>

M\_SERVICE\_THREADS / M\_SERVICE\_THREAD\_SAMPLES System Views \(Changed\)

</b></dt>
<dd>

A new column has been introduced: WORKLOAD\_CLASS\_NAME. [M\_SERVICE\_THREADS System View](020-System-Views-Reference/022-Monitoring-Views/m-service-threads-system-view-20c499a.md), [M\_SERVICE\_THREAD\_SAMPLES System View](020-System-Views-Reference/022-Monitoring-Views/m-service-thread-samples-system-view-d2176a6.md)



</dd><dt><b>

M\_SQL\_PLAN\_CACHE / M\_SQL\_PLAN\_STATISTICS System Views \(Changed\)

</b></dt>
<dd>

Sixteen new columns have been introduced: four for CPU time and twelve for NSE buffer cache. [M\_SQL\_PLAN\_CACHE System View](020-System-Views-Reference/022-Monitoring-Views/m-sql-plan-cache-system-view-20c57b8.md), [M\_SQL\_PLAN\_STATISTICS System View](020-System-Views-Reference/022-Monitoring-Views/m-sql-plan-statistics-system-view-84d12a5.md)



</dd>
</dl>



<a name="loiofd3e0d24c7794cb5968d53cacf4ddb6d__section_nvn_5hp_nnb"/>

## QRC 4/2020


<dl>
<dt><b>

ALTER / DROP JWT PROVIDER Statements \(New\)

</b></dt>
<dd>

You can now alter and drop JWT providers. [ALTER JWT PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/alter-jwt-provider-statement-access-control-61863f6.md), [DROP SAML PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/drop-saml-provider-statement-access-control-20d76c8.md)



</dd><dt><b>

ALTER / DROP SAML PROVIDER Statements \(New\)

</b></dt>
<dd>

You can now alter and drop SAML providers. [ALTER SAML PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/alter-saml-provider-statement-access-control-20d04f7.md), [DROP JWT PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/drop-jwt-provider-statement-access-control-e3caf68.md)



</dd><dt><b>

ALTER SYSTEM REMOVE SQL PLAN CACHE Statement \(Changed\)

</b></dt>
<dd>

You can now use a WHERE clause to specify which SQL plan entries to remove. [ALTER SYSTEM REMOVE SQL PLAN CACHE Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/alter-system-remove-sql-plan-cache-statement-system-management-dafece7.md)



</dd><dt><b>

CAST Function \(Changed\)

</b></dt>
<dd>

When you cast a parameter as a data type, the parameter is now bound as that data type. Previously the parameter was bound as a string and converted. [CAST Function \(Data Type Conversion\)](010-SQL-Reference/011-SQL-Functions/cast-function-data-type-conversion-20db6dd.md)



</dd><dt><b>

CREATE TABLE Statement \(Changed\)

</b></dt>
<dd>

The clause WITH INDEX *<defined\_index\_name\_list\>* has been added to the CREATE TABLE LIKE clause. For each specified index on the source table, a matching index is created on the target table. [CREATE TABLE Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md) 



</dd><dt><b>

CREATE / ALTER TABLE Statements \(Changed\)

</b></dt>
<dd>

The DYNAMIC clause for the OTHERS partition has been extended to include a time interval property. The property lets you specify the interval between the last and the next range partition created dynamically. [CREATE TABLE Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md), [ALTER TABLE Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md)



</dd><dt><b>

CREATE / ALTER WORKLOAD CLASS Statements \(Changed\)

</b></dt>
<dd>

Two new admission control queue threshold properties, ADMISSION CONTROL QUEUE CPU THRESHOLD and ADMISSION CONTROL QUEUE MEMORY THRESHOLD, have been implemented. [CREATE WORKLOAD CLASS Statement \(Workload Management\)](010-SQL-Reference/012-SQL-Statements/create-workload-class-statement-workload-management-dc417c3.md), [ALTER WORKLOAD CLASS Statement \(Workload Management\)](010-SQL-Reference/012-SQL-Statements/alter-workload-class-statement-workload-management-d4b4659.md)

Columns were added to the WORKLOAD\_CLASSES, M\_WORKLOAD\_CLASS\_STATISTICS, M\_ADMISSION\_CONTROL\_QUEUES, M\_ADMISSION\_CONTROL\_EVENTS, and M\_LOAD\_HISTORY\_SERVICE views for these properties.



</dd><dt><b>

CREATE / ALTER / DROP X509 PROVIDER Statements \(New\)

</b></dt>
<dd>

This syntax allows you to manage X.509 providers. [CREATE X509 PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-x509-provider-statement-access-control-3b3163d.md), [ALTER X509 PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/alter-x509-provider-statement-access-control-4f7e59d.md), [DROP X509 PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/drop-x509-provider-statement-access-control-f7a37e8.md)

Two new system views, X509\_PROVIDERS and X509\_PROVIDER\_RULES, have been added. The X509\_USER\_MAPPINGS system view has an additional column, X509\_PROVIDER\_NAME.



</dd><dt><b>

EXPLAIN PLAN Statement \(Changed\)

</b></dt>
<dd>

You can now show the recompiled query plan of a parameterized query without first executing the query. [EXPLAIN PLAN Statement \(Data Manipulation\)](010-SQL-Reference/012-SQL-Statements/explain-plan-statement-data-manipulation-20d9ec5.md)



</dd><dt><b>

EXPORT / EXPORT INTO Statements \(Changed\)

</b></dt>
<dd>

EXPORT and EXPORT INTO now support files in AliCloud. [EXPORT Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/export-statement-data-import-export-20da0be.md), [EXPORT INTO Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/export-into-statement-data-import-export-6a6f59b.md)



</dd><dt><b>

EXPORT INTO Statement \(Changed\)

</b></dt>
<dd>

Parquet formats now support compression codes and row group size. [EXPORT INTO Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/export-into-statement-data-import-export-6a6f59b.md)



</dd><dt><b>

GRANT / REVOKE Statements \(Changed\)

</b></dt>
<dd>

Three new object privileges, ALTER, DROP, and REFERENCES, have been added to the PROVIDER object to allow for the management of JWT and SAML providers. [GRANT Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md), [REVOKE Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/revoke-statement-access-control-20fc91c.md)



</dd><dt><b>

IMPORT / IMPORT FROM Statements \(Changed\)

</b></dt>
<dd>

IMPORT and IMPORT FROM now support files in AliCloud. [IMPORT Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-statement-data-import-export-20f75ad.md), [IMPORT FROM Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-from-statement-data-import-export-20f712e.md)



</dd><dt><b>

TRUNCATE TABLE Statement \(Changed\)

</b></dt>
<dd>

You can now truncate specific partitions of a table. [TRUNCATE TABLE Statement \(Data Manipulation\)](010-SQL-Reference/012-SQL-Statements/truncate-table-statement-data-manipulation-20fe29f.md)



</dd>
</dl>



<a name="loiofd3e0d24c7794cb5968d53cacf4ddb6d__section_jz4_lj1_nmb"/>

## QRC 3/2020


<dl>
<dt><b>

ALTER VIRTUAL TABLE Statement \(Changed\)

</b></dt>
<dd>

You can now asynchronously add and refresh replicas. [ALTER VIRTUAL TABLE Statement \(Data Definition\)](010-SQL-Reference/012-SQL-Statements/alter-virtual-table-statement-data-definition-5182698.md)



</dd><dt><b>

CREATE JWT PROVIDER Statement \(New\)

</b></dt>
<dd>

You can now create JWT providers. [CREATE JWT PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-jwt-provider-statement-access-control-bfe3daf.md)



</dd><dt><b>

CREATE SAML PROVIDER Statement \(New\)

</b></dt>
<dd>

You can now create SAML providers. [CREATE SAML PROVIDER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-saml-provider-statement-access-control-20d4cca.md)



</dd><dt><b>

CONNECT Statement \(Changed\)

</b></dt>
<dd>

You can now connect using a JWT token. [CONNECT Statement \(Session Management\)](010-SQL-Reference/012-SQL-Statements/connect-statement-session-management-20d3b9a.md)



</dd><dt><b>

EXPORT / EXPORT INTO Statement \(Changed\)

</b></dt>
<dd>

You can now export data using a parquet file type. [EXPORT Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/export-statement-data-import-export-20da0be.md), [EXPORT INTO Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/export-into-statement-data-import-export-6a6f59b.md)



</dd><dt><b>

GRANT / REVOKE Statements \(Changed\)

</b></dt>
<dd>

Two new privileges, CREATE JWT PROVIDER and CREATE SAML PROVIDER, have been added to allow the creation of providers. [GRANT Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md), [REVOKE Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/revoke-statement-access-control-20fc91c.md)



</dd><dt><b>

IMPORT / IMPORT FROM Statement \(Changed\)

</b></dt>
<dd>

You can now import data using a parquet file type. [IMPORT Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-statement-data-import-export-20f75ad.md), [IMPORT FROM Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-from-statement-data-import-export-20f712e.md)



</dd><dt><b>

IMPORT SCAN Statement \(New\)

</b></dt>
<dd>

You can now search the specified path or file for exported objects. [IMPORT SCAN Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-scan-statement-data-import-export-20f79b2.md)



</dd><dt><b>

M\_CONNECTIONS System View \(changed\)

</b></dt>
<dd>

Three new columns have been added: SSL\_VERSION, SSL\_CIPHER, and HAS\_SSL\_CLIENT\_CERTIFICATE. [M\_CONNECTIONS System View](020-System-Views-Reference/022-Monitoring-Views/m-connections-system-view-20abcf1.md)



</dd><dt><b>

HINT Details \(changed\)

</b></dt>
<dd>

The new CS\_JOIN\_REDUCTION\_MULTICOLUMN\_FIRST\(*<table\_name\>**<column\_name\>*\) hint has been added. [HINT Details](010-SQL-Reference/012-SQL-Statements/hint-details-4ba9edc.md)



</dd>
</dl>



<a name="loiofd3e0d24c7794cb5968d53cacf4ddb6d__section_v2v_yvb_jlb"/>

## QRC 2/2020


<dl>
<dt><b>

ALTER PSE Statement \(Changed\)

</b></dt>
<dd>

You can now set one or more remote sources on a PSE purpose. [ALTER PSE Statement \(System Management\)](010-SQL-Reference/012-SQL-Statements/alter-pse-statement-system-management-9c22c6f.md)



</dd><dt><b>

CREATE USER Statement \(Changed\)

</b></dt>
<dd>

When creating a new user, if the user creating the new user has the USERGROUP OPERATOR privilege on only one usergroup, the SET USERGROUP clause is no longer required. [CREATE USER Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-user-statement-access-control-20d5ddb.md)



</dd><dt><b>

CREATE / ALTER / DROP USERGROUP Statements \(New\)

</b></dt>
<dd>

This syntax allows you to manage usergroups. [CREATE USERGROUP Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/create-usergroup-statement-access-control-9869125.md), [ALTER USERGROUP Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/alter-usergroup-statement-access-control-aa94ca8.md), [DROP USERGROUP Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/drop-usergroup-statement-access-control-6dc0ada.md)



</dd><dt><b>

EXPORT / EXPORT INTO Statements \(New\)

</b></dt>
<dd>

You can now export data.

You can now exclude remote table data in an export without having to use the CATALOG ONLY option.

[EXPORT INTO Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/export-into-statement-data-import-export-6a6f59b.md), [EXPORT Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/export-statement-data-import-export-20da0be.md)



</dd><dt><b>

GRANT / REVOKE Statements \(Changed\)

</b></dt>
<dd>

A new privilege, CREATE USERGROUP, has been added to allow the creation and dropping of usergroups. [GRANT Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md), [REVOKE Statement \(Access Control\)](010-SQL-Reference/012-SQL-Statements/revoke-statement-access-control-20fc91c.md)



</dd><dt><b>

IMPORT / IMPORT FROM Statements \(New\)

</b></dt>
<dd>

You can now import data. [IMPORT FROM Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-from-statement-data-import-export-20f712e.md) [IMPORT Statement \(Data Import Export\)](010-SQL-Reference/012-SQL-Statements/import-statement-data-import-export-20f75ad.md)



</dd>
</dl>

