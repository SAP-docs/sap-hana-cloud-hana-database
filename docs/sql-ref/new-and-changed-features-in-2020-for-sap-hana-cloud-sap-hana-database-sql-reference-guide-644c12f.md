<!-- loio644c12fa61ef4aff8ce0ad197cf7283c -->

# New and Changed Features in 2020 for SAP HANA Cloud, SAP HANA Database SQL Reference Guide

SAP HANA Cloud introduces new and changed features for the SAP HANA Cloud, SAP HANA Database SQL Reference Guide.



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

