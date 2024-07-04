<!-- loio1f31f6d463954fdea19f2b98e069b664 -->

# Per-Feature Impacts

Provides a list of SQL and SQLScript impacts from the major features that are not available in SAP HANA Cloud.



<a name="loio1f31f6d463954fdea19f2b98e069b664__section_dpk_gmh_zlb"/>

## Impacts for unavailable high-level features


<dl>
<dt><b>

SAP Accelerator for ASE \(A4A\)

</b></dt>
<dd>

-   'etsserver' service removed.
-   CREATE/ALTER/DROP EXTENDED ROW STORAGE removed.

-   ETS\_ADMIN\_CONSOLE\_PROC removed.




</dd><dt><b>

BO Explorer

</b></dt>
<dd>

-   CS\_BOE\_DIDYOUMEAN\_SEARCH system view removed.

-   CS\_BOE\_PORTAL\_SEARCH system view removed.

-   TEXT\_FILTER no longer supported in GROUP BY.




</dd><dt><b>

Calculation Scenario

</b></dt>
<dd>

-   EXPOSE\_NODE is no longer supported.

-   GRAPH is no longer supported.




</dd><dt><b>

Data Aging

</b></dt>
<dd>

-   CREATE HISTORY TABLE.... statement is no longer supported.

-   CREATE TABLE ...LIKE...WITHOUT HISTORY option is no longer supported.

-   MERGE HISTORY DELTA OF <table\_name\>...statement is no longer supported.

-   UPDATE <table\_name\> MERGE DELTA INTO HISTORY INDEX statement is no longer supported.

-   ALTER REMOTE SOURCE CLEAR LATENCY HISTORY statement is no longer supported.

-   WITH RANGE RESTRICTION clause as part of SELECT, INSERT, UPDATE ,DELETE, REPLACE, UPSERT, MERGE INTO, and CALL statements is no longer supported.

-   M\_HISTORY\_INDEX\_LAST\_COMMIT\_ID view removed.

-   TRANS\_TOKEN\_HISTORY view removed.

-   TRANSACTION\_HISTORY view removed.

-   M\_CS\_LOADS.IS\_HISTORY column removed.

-   M\_CS\_MVCC.IS\_HISTORY column removed.

-   M\_CS\_TABLES.MEMORY\_SIZE\_IN\_HISTORY\_MAIN column removed.

-   M\_CS\_TABLES.MEMORY\_SIZE\_IN\_HISTORY\_DELTA column removed.

-   M\_CS\_TABLES.RAW\_RECORD\_COUNT\_IN\_HISTORY\_MAIN column removed.

-   M\_CS\_TABLES.RAW\_RECORD\_COUNT\_IN\_HISTORY\_DELTA column removed.

-   M\_TABLE\_PERSISTENCE\_LOCATIONS.IS\_HISTORY column removed.

-   M\_CS\_UNLOADS.IS\_HISTORY column removed.




</dd><dt><b>

Dynamic Tiering

</b></dt>
<dd>

-   ALTER EXTENDED STORAGE ... is no longer supported.

-   ALTER TABLE ...USING DEFAULT STORAGE is no longer supported.

-   ALTER TABLE ...USING EXTENDED STORAGE is no longer supported.

-   CREATE EXTENDED STORAGE is no longer supported.

-   CREATE STATISTICS ...FOR EXTENDED STORAGE is no longer supported.

-   CREATE TABLE ...USING DEFAULT STORAGE is no longer supported.

-   CREATE TABLE ...USING EXTENDED STORAG is no longer supported.

-   DROP EXTENDED STORAGE is no longer supported.

-   DROP STATISTICS ...FOR EXTENDED STORAGE is no longer supported.

-   EXTENDED\_STORAGE\_ADMIN is no longer supported.

-   CHECK\_ES removed

-   ES\_REBUILD\_INDEX removed

-   M\_ES\_EXPENSIVE\_STATEMENTS removed.

-   M\_ES\_TABLES removed.

-   M\_ES\_DBSPACES removed.

-   M\_ES\_DBSPACE\_FILES removed.

-   M\_ES\_CONNECTIONS removed.

-   M\_ES\_TRANSACTIONS removed.

-   M\_ES\_DELTA\_MERGE\_STATISTICS removed.

-   M\_ES\_LOCKS removed.

-   M\_ES\_DELTA\_MEMORY removed.

-   M\_ES\_OVERVIEW removed.

-   M\_ES\_RESULT\_CACHE removed.

-   M\_ES\_SERVICE\_REPLICATION removed.

-   M\_TABLE\_PRUNING\_STATISTICS removed.

-   M\_VOLUME\_FILES\_ES removed.




</dd><dt><b>

External Machine Learning \(EML\)

</b></dt>
<dd>

-   External Machine Learning AFL is no longer supported.

-   'grpc' ADAPTER is no longer supported.

-   \_SYS\_AFL.EML\_MODEL\_CONFIGURATION table is no longer supported.

-   \_SYS\_AFL.EML\_PREDICT function is no longer supported.

-   \_SYS\_AFL.EML\_PREDICTM function is no longer supported.

-   AFL\_\_SYS\_AFL\_EML\_EXECUTE privilege is no longer supported.




</dd><dt><b>

Flexible Tables

</b></dt>
<dd>

-   ALTER TABLE ... ALTER SCHEMA FLEXIBILITY ... is no longer supported.

-   ALTER TABLE ... DISABLE SCHEMA FLEXIBILITY is no longer supported.

-   ALTER TABLE ... ENABLE SCHEMA FLEXIBILITY is no longer supported.

-   CREATE TABLE ... WITH SCHEMA FLEXIBILITY ... is no longer supported.

-   CREATE TABLE ... WITHOUT SCHEMA FLEXIBILITY ... is no longer supported.

-   ALTER SYSTEM RECLAIM FLEXIBLE TABLES is no longer supported.

-   IMPORT FROM ... WITH SCHEMA FLEXIBILITY is no longer supported.

-   FLEXIBLE\_TABLES view is removed.




</dd><dt><b>

MDC

</b></dt>
<dd>

-   GRANT TENANT ADMIN TO is no longer supported.

-   REVOKE TENANT ADMIN TO is no longer supported.




</dd><dt><b>

R Integration

</b></dt>
<dd>

-   RSERVE REMOTE SOURCES parameter of ALTER USER removed.

-   'rserve' ADAPTER no longer supported.

-   GRANT/REVOKE R SCRIPT privilege removed.

-   SQLScript LANGUAGE option RLANG no longer supported.

-   Calculation scenario is no longer supported.




</dd><dt><b>

SAP HANA Accelerator for ASE

</b></dt>
<dd>

-   'etsserver' service removed.

-   ETS\_ADMIN\_CONSOLE\_PROC removed.




</dd><dt><b>

SAP Host Agent

</b></dt>
<dd>

-   M\_HOST\_AGENT\_INFORMATION view removed.

-   M\_HOST\_AGENT\_METRICS view removed.




</dd><dt><b>

SAP HANA CDS

</b></dt>
<dd>

-   Models need to be converted to SCP CAP \(Cloud Application Programming\).

-   \_SYS\_REPO schema is removed.

-   \_SYS\_RT schema is removed.




</dd><dt><b>

Security Changes

</b></dt>
<dd>

-   SAPLogon / SAPAssertion Authentication is no longer supported.

-   XS classic-based Creation of SAML Assertions \(Single Sign Out\) is no longer supported.

-   Kerberos / SPNEGO Authentication is no longer supported.

-   DATA ADMIN Privilege removed

-   EXTENDED\_STORAGE\_ADMIN removed.

-   TENANT ADMIN Privilege removed




</dd><dt><b>

Smart Data Access \(refer to [2600176](https://me.sap.com/notes/2600176) for details\)

</b></dt>
<dd>

-   **Adapters no longer supported:**

-   Google Big Query \(odbc\) - 'bigquery'

-   Hadoop - 'hadoop'

-   Hive - 'hiveodbc'

-   IBM DB2 - 'db2'

-   IBM Netezza - 'netezza'

-   MS SQL Server - 'mssql'

-   Oracle - 'oracle'

-   Teradata - 'tdodbc'

-   SPARK SQL - 'sparksql'

-   **Adapters previously deprecated and no longer supported:**

-   Generic ODBC - 'odbc'

-   MII - 'mii'

-   MySQL - 'mysql'

-   PostgreSQL - 'postresql' \(2892211\)

-   **Adapters planned but not initially available:**

-   SAP ASE - 'aseodbc'

-   SAP IQ - 'iqodbc'

-   SAP MaxDB - 'maxdb'




</dd><dt><b>

Text Analysis

</b></dt>
<dd>

-   TEXT, BINTEXT, and SHORTTEXT datatype removed.

-   FULLTEXT index removed where CREATE/ALTER/DROP FULLTEXT INDEX statements are no longer supported.

-   CONTAINS option FULLTEXT ON/OFF/AUTOMATIC and LINGUISTIC are removed.

-   TA\_ANALYZE procedure removed.

-   TM\_CATEGORIZE\_KNN procedure removed.

-   TM\_GET\_RELATED\_TERMS procedure removed.

-   TM\_GET\_RELEVANT\_TERMS procedure removed.

-   TM\_GET\_SUGGESTED\_TERMS procedure removed.

-   TM\_GET\_RELATED\_DOCUMENTS procedure removed.

-   TM\_GET\_RELEVANT\_DOCUMENTS procedure removed.

-   RPROC\_MOVE\_RTABLE\_TO\_DBM\_FULLTEXT\_QUEUES procedure removed.

-   M\_FULLTEXT\_COLUMN\_STATISTICS removed.

-   M\_FULLTEXT\_QUEUES removed.

-   M\_INDEXING\_QUEUES removed.

-   FULLTEXT\_INDEXES removed.

-   M\_TEXT\_ANALYSIS\_LANGUAGES removed.

-   M\_TEXT\_ANALYSIS\_MIME\_TYPES removed.




</dd><dt><b>

Time Series Tables

</b></dt>
<dd>

-   SERIES option of CREATE TABLE is no longer supported.



</dd>
</dl>

**Related Information**  


[Compatibility with Other SAP HANA Versions](https://help.sap.com/viewer/3c53bc7b58934a9795b6dd8c7e28cf05/hanacloud/en-US/11cc86c44d0b4dd3bf70e16870d9d4df.html)

[SAP Note 2695472](https://me.sap.com/notes/2695472 "Statement on SAP HANA XS Classic and the SAP HANA Repository and SAP Business Technology Platform, SAP HANA Service")

[SAP Note 2993439](https://me.sap.com/notes/2993439 "2993439 - Statement on SAP HANA Studio and SAP HANA Cloud")

[SAP Note 2868742](https://me.sap.com/notes/2868742 "Differences between SAP HANA Cloud and SAP HANA Platform for SQL, SQLScript and SAP HDI (SAP HANA Deployment Infrastructure")

[SAP HANA Cloud Configuration Parameter Reference](https://help.sap.com/viewer/138dcf7d779543608917a2307a6115f2/2024_3_QRC/en-US/4b4d88980622427ab2d6ca8c05448166.html "Reference documentation for public configuration parameters in SAP HANA Cloud.") :arrow_upper_right:

[Managing SAP HANA Users](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/ed7af17e5ae14de694d9bee5f35098f4.html "Every user who wants to work with the SAP HANA database must have a database user who can log on and is authorized to perform their individual tasks.") :arrow_upper_right:

