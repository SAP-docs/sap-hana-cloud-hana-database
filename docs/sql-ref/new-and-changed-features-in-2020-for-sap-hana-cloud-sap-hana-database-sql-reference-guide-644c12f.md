<!-- loio644c12fa61ef4aff8ce0ad197cf7283c -->

# New and Changed Features in 2020 for SAP HANA Cloud, SAP HANA Database SQL Reference Guide

SAP HANA Cloud introduces new and changed features for the SAP HANA Cloud, SAP HANA Database SQL Reference Guide.



<a name="loio644c12fa61ef4aff8ce0ad197cf7283c__section_nvn_5hp_nnb"/>

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



<a name="loio644c12fa61ef4aff8ce0ad197cf7283c__section_jz4_lj1_nmb"/>

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



<a name="loio644c12fa61ef4aff8ce0ad197cf7283c__section_v2v_yvb_jlb"/>

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

