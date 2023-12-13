<!-- loio24d9c1e9c5924de788034047bfddc15d -->

# New and Changed Features in 2021 for SAP HANA Cloud, SAP HANA Database SQL Reference Guide

SAP HANA Cloud introduces new and changed features for the SAP HANA Cloud, SAP HANA Database SQL Reference Guide.



<a name="loio24d9c1e9c5924de788034047bfddc15d__section_hx4_bjk_grb"/>

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



<a name="loio24d9c1e9c5924de788034047bfddc15d__section_w1w_gl3_kqb"/>

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



<a name="loio24d9c1e9c5924de788034047bfddc15d__section_ygh_yjt_4pb"/>

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



<a name="loio24d9c1e9c5924de788034047bfddc15d__section_sgp_qjl_h4b"/>

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



<a name="loio24d9c1e9c5924de788034047bfddc15d__section_nvn_5hp_nnb"/>

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

