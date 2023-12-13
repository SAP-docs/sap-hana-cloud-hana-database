<!-- loio410b8cd3444f4a5ebab98fe05f9cf6a4 -->

# New and Changed Features in 2022 for SAP HANA Cloud, SAP HANA Database SQL Reference Guide

SAP HANA Cloud introduces new and changed features for the SAP HANA Cloud, SAP HANA Database SQL Reference Guide.





<a name="loio410b8cd3444f4a5ebab98fe05f9cf6a4__section_bzj_ndk_gvb"/>

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



<a name="loio410b8cd3444f4a5ebab98fe05f9cf6a4__section_tbs_tkn_15b"/>

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



<a name="loio410b8cd3444f4a5ebab98fe05f9cf6a4__section_oc3_1k4_xyb"/>

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



<a name="loio410b8cd3444f4a5ebab98fe05f9cf6a4__section_flg_v5h_yrb"/>

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

