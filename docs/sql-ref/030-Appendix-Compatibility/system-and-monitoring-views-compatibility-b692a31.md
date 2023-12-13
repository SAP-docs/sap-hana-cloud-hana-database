<!-- loiob692a317baf744b1a17abbe72108719c -->

# System and Monitoring Views Compatibility

Lists system and monitoring view \(SYS schema\) features in other versions of SAP HANA that are not available in SAP HANA Cloud.



## Introduction

Many of the columns and views in this list are associated with larger features that are not available or supported in SAP HANA Cloud. For the list of larger features not available in SAP HANA Cloud, see the feature compatibility topic at the beginning of this guide.

If your solution uses any of the items listed here and you are migrating to SAP HANA Cloud, then you may need to make changes.


<table>
<tr>
<th valign="top">

View Name

</th>
<th valign="top">

Columns removed or other changes

</th>
</tr>
<tr>
<td valign="top">

CDS\_...

</td>
<td valign="top">

All views starting with CDS\_ are not available \(HANA CDS is not supported\)

</td>
</tr>
<tr>
<td valign="top">

CS\_BO\_...

</td>
<td valign="top">

All views starting with CS\_BOE\_ are not available \(HANA BO Explorer is not supported\)

</td>
</tr>
<tr>
<td valign="top">

COLUMNS

</td>
<td valign="top">

Not available. Use TABLE\_COLUMNS or VIEW\_COLUMNS instead.

</td>
</tr>
<tr>
<td valign="top">

DATA\_STATISTICS

</td>
<td valign="top">

The following columns are not available. Use M\_DATA\_STATISTICS.DATA\_STATISTICS\_CONTENT instead:

-   COUNT

-   LAST\_REFRESH\_ACCURACY

-   LAST\_REFRESH\_BUCKET

-   LAST\_REFRESH\_MEMORY

-   LAST\_REFRESH\_MEMORY\_PERCENT

-   LAST\_REFRESH\_PREFIX\_BITS

-   LAST\_REFRESH\_QERROR

-   LAST\_REFRESH\_QTHETA

-   LAST\_REFRESH\_REASON

-   LAST\_REFRESH\_TIME

-   MAXVALUE\_NUMERIC

-   MAXVALUE\_STRING

-   MINVALUE\_NUMERIC

-   MINVALUE\_STRING


DATA\_SOURCE\_PART\_ID column is not available. Use M\_DATA\_STATISTICS.DATA\_SOURCE\_PART\_ID instead.

DISTINCT\_COUNT column is not available. Use M\_DATA\_STATISTICS.DISTINCT\_COUNT instead.

NULL\_COUNT column is not available

</td>
</tr>
<tr>
<td valign="top">

EFFECTIVE\_APPLICATION\_PRIVILEGES

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

EFFECTIVE\_PRIVILEGES

</td>
<td valign="top">

COLUMN NAME column is not available

</td>
</tr>
<tr>
<td valign="top">

ENCRYPTION\_ROOT\_KEYS

</td>
<td valign="top">

ROOT\_KEY\_VERSION column is not available

</td>
</tr>
<tr>
<td valign="top">

FLEXIBLE\_TABLES

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

FULLTEXT\_INDEXES

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

FUNCTIONS

</td>
<td valign="top">

IS\_UNICODE column is not available

</td>
</tr>
<tr>
<td valign="top">

GEOCODE\_INDEXES

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

GRANTED\_PRIVILEGES

</td>
<td valign="top">

COLUMN NAME column is not available

</td>
</tr>
<tr>
<td valign="top">

GRAPH\_WORKSPACES

</td>
<td valign="top">

EDGE\_SCHEMA\_NAME, EDGE\_TABLE\_NAME, EDGE\_SOURCE\_COLUMN\_NAME, EDGE\_TARGET\_COLUMN\_NAME, EDGE\_KEY\_COLUMN\_NAME, VERTEX\_SCHEMA\_NAME, VERTEX\_TABLE\_NAME, VERTEX\_KEY\_COLUMN\_NAME columns are not available

</td>
</tr>
<tr>
<td valign="top">

INDEXES

</td>
<td valign="top">

KEY\_LENGTH, BTREE\_SPLIT\_TYPE, BTREE\_SPLIT\_POSITION, STORAGE\_TYPE

</td>
</tr>
<tr>
<td valign="top">

LCM\_

</td>
<td valign="top">

All views starting with LCM are not available \(Life Cycle Management \(LCM\) is not supported\)

</td>
</tr>
<tr>
<td valign="top">

PROCEDURES

</td>
<td valign="top">

IS\_UNICODE column is not available

</td>
</tr>
<tr>
<td valign="top">

SERIES\_KEY\_COLUMNS

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

SERIES\_TABLES

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

TABLES

</td>
<td valign="top">

IS\_SYSTEM\_TABLE, IS\_TENANT\_SHARED\_DATA, IS\_TENANT\_SHARED\_METADATA, SESSION\_TYPE columns are not available

</td>
</tr>
<tr>
<td valign="top">

TABLE\_COLUMNS

</td>
<td valign="top">

COLLATION, MAX\_VALUE, MIN\_VALUE, CS\_DATA\_TYPE\_ID, CS\_DATA\_TYPE\_NAME columns are not available

</td>
</tr>
<tr>
<td valign="top">

TABLE\_PARTITIONS

</td>
<td valign="top">

STORAGE\_TYPE column is not available

</td>
</tr>
<tr>
<td valign="top">

TEXT\_CONFIGURATIONS

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

TRANSACTION\_HISTORY

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

USERS

</td>
<td valign="top">

IS\_SAP\_LOGON\_TICKET\_ENABLED, IS\_SAP\_ASSERTION\_TICKET\_ENABLED, PASSWORD\_CHANGE\_TIME columns are not available

</td>
</tr>
<tr>
<td valign="top">

VIEWS

</td>
<td valign="top">

IS\_UNICODE, IS\_TENANT\_SHARED\_METADATA, CACHE\_RETENTION, CACHE\_FILTER, IS\_CACHE\_FORCED columns are not available

</td>
</tr>
<tr>
<td valign="top">

VIEW\_COLUMNS

</td>
<td valign="top">

COLLATION, MAX\_VALUE, MIN\_VALUE, CS\_DATA\_TYPE\_ID, CS\_DATA\_TYPE\_NAME columns are not available

</td>
</tr>
<tr>
<td valign="top">

VIRTUAL\_FUNCTION\_PACKAGES

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

M\_ACTIVE\_STATEMENTS

</td>
<td valign="top">

USED\_MEMORY\_SIZE column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_ASYNCHRONOUS\_TABLE\_REPLICAS

</td>
<td valign="top">

Not available. Use M\_TABLE\_REPLICAS instead.

</td>
</tr>
<tr>
<td valign="top">

M\_ASYNCHRONOUS\_TABLE\_REPLICAS\_RESET

</td>
<td valign="top">

Not available. Use M\_TABLE\_REPLICAS\_RESET instead.

</td>
</tr>
<tr>
<td valign="top">

M\_BACKUP\_CATALOG

</td>
<td valign="top">

ES\_ENCRYPTION\_CHANGE\_ENABLED column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_BACKUP\_CONFIGURATION

</td>
<td valign="top">

LOG\_REPLAY\_STEP\_SIZE column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_BLOCKED\_TRANSACTIONS

</td>
<td valign="top">

WAITING\_TABLE\_NAME column is not available. Use WAITING\_OBJECT\_NAME instead.

</td>
</tr>
<tr>
<td valign="top">

M\_CONNECTIONS

</td>
<td valign="top">

IS\_HISTORY\_SAVED column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_CONTAINER\_DIRECTORY

</td>
<td valign="top">

CNT\_CONTAINERS column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_CONTAINER\_NAME\_DIRECTORY

</td>
<td valign="top">

CNT\_CONTAINERS column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_CONTEXT\_MEMORY / M\_CONTEXT\_MEMORY\_RESET

</td>
<td valign="top">

MALLOC\_PROXY\_CACHE\_MISSES column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_CS\_ALL\_COLUMNS

</td>
<td valign="top">

UNCOMPRESSED\_SIZE and COMPRESSION\_RATIO\_IN\_PERCENTAGE columns are not available

</td>
</tr>
<tr>
<td valign="top">

M\_CS\_COLUMNS

</td>
<td valign="top">

UNCOMPRESSED\_SIZE, COMPRESSION\_RATIO\_IN\_PERCENTAGE columns are not available

</td>
</tr>
<tr>
<td valign="top">

M\_CS\_LOADS

</td>
<td valign="top">

IS\_HISTORY column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_CS\_MVCC

</td>
<td valign="top">

IS\_HISTORY column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_CS\_PARTITIONS

</td>
<td valign="top">

Not available. Use TABLE\_PARTITIONS instead.

</td>
</tr>
<tr>
<td valign="top">

M\_CS\_RECORD\_LOCK\_STATISTICS

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

M\_CS\_TABLES

</td>
<td valign="top">

MEMORY\_SIZE\_IN\_HISTORY\_MAIN, MEMORY\_SIZE\_IN\_HISTORY\_DELTA, RAW\_RECORD\_COUNT\_IN\_HISTORY\_MAIN, and RAW\_RECORD\_COUNT\_IN\_HISTORY\_DELTA columns are not available

</td>
</tr>
<tr>
<td valign="top">

M\_DELTA\_MERGE\_STATISTICS

</td>
<td valign="top">

HISTORY column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_ES\_...

</td>
<td valign="top">

All views starting with M\_ES\_ are not available \(Extended Storage is not supported\)

</td>
</tr>
<tr>
<td valign="top">

M\_EXPORT\_BINARY\_STATUS

</td>
<td valign="top">

Not available: consider M\_JOB\_PROGRESS instead.

</td>
</tr>
<tr>
<td valign="top">

M\_EXTRACTORS

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

M\_FULLTEXT\_...

</td>
<td valign="top">

All system views starting with M\_FULLTEXT\_ are not available

</td>
</tr>
<tr>
<td valign="top">

M\_HEAP\_MEMORY / M\_HEAP\_MEMORY\_RESET

</td>
<td valign="top">

MALLOC\_PROXY\_CACHE\_MISSES column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_HISTORY\_INDEX\_LAST\_COMMIT\_ID

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

M\_HOST\_AGENT\_INFORMATION

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

M\_HOST\_AGENT\_METRICS

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

M\_IMPORT\_BINARY\_STATUS

</td>
<td valign="top">

Not available. Consider M\_JOB\_PROGRESS instead.

</td>
</tr>
<tr>
<td valign="top">

M\_INDEXING\_QUEUES

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

M\_LANDSCAPE\_HOST\_CONFIGURATION

</td>
<td valign="top">

FAILOVER\_GROUP column is not available. Use FAILOVER\_...\_GROUP columns instead.

STORAGE\_PARTITION column is not available. Use STORAGE\_...\_PARTITION columns instead.

</td>
</tr>
<tr>
<td valign="top">

M\_LICENSE

</td>
<td valign="top">

PRODUCT\_LIMIT, PRODUCT\_USAGE, ENFORCED, USAGE, MEASUREMENT\_XML columns are not available

</td>
</tr>
<tr>
<td valign="top">

M\_LICENSES

</td>
<td valign="top">

PRODUCT\_LIMIT, PRODUCT\_LIMIT\_DESCRIPTION, PRODUCT\_USAGE, MEASUREMENT\_INTERVAL, ENFORCED columns are not available

</td>
</tr>
<tr>
<td valign="top">

M\_LICENSE\_MEASUREMENTS

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

M\_LICENSE\_MEASUREMENT\_STATISTICS

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

M\_LICENSE\_USAGE\_HISTORY

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

M\_LIVECACHE\_...

</td>
<td valign="top">

All views starting with M\_LIVECACHE\_ are not available \(LiveCache is not supported\)

</td>
</tr>
<tr>
<td valign="top">

M\_MEMORY

</td>
<td valign="top">

Not available. Use M\_SERVICE\_MEMORY instead.

</td>
</tr>
<tr>
<td valign="top">

M\_MONITOR\_COLUMNS

</td>
<td valign="top">

COLLATION column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_PERSISTENCE\_ENCRYPTION\_STATUS

</td>
<td valign="top">

USED\_ROOT\_KEY\_VERSION column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_PREPARED\_STATEMENTS

</td>
<td valign="top">

USED\_MEMORY\_SIZE column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_QUERY\_CACHED\_PLANS

</td>
<td valign="top">

Not available. Use M\_SQL\_PLAN\_CACHE instead.

</td>
</tr>
<tr>
<td valign="top">

M\_RS\_INDEXES

</td>
<td valign="top">

INSERT\_COUNT, REMOVE\_COUNT, FULL\_KEY\_REFERENCE\_COUNT columns are not available

</td>
</tr>
<tr>
<td valign="top">

M\_RS\_TABLE\_VERSION\_STATISTICS

</td>
<td valign="top">

IS\_SYSTEM\_TABLE column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_SECURESTORE

</td>
<td valign="top">

Not available. Use ENCRYPTION\_ROOT\_KEYS instead.

</td>
</tr>
<tr>
<td valign="top">

M\_SERVICE\_STATISTICS

</td>
<td valign="top">

REQUESTS\_PER\_SEC, RESPONSE\_TIME, FINISHED\_NON\_INTERNAL\_REQUEST\_COUNT, ALL\_FINISHED\_REQUEST\_COUNT, ACTIVE\_REQUEST\_COUNT, PENDING\_REQUEST\_COUNT, ACTIVE\_THREAD\_COUNT, and THREAD\_COUNT columns are not available

</td>
</tr>
<tr>
<td valign="top">

M\_STREAMING\_...

</td>
<td valign="top">

All views starting with M\_STREAMING\_ are not available \(SAP HANA Streaming is not supported\)

</td>
</tr>
<tr>
<td valign="top">

M\_TABLE\_LOCKS

</td>
<td valign="top">

Not available. Use OBJECT\_LOCKS instead.

</td>
</tr>
<tr>
<td valign="top">

M\_TABLE\_PARTITIONS

</td>
<td valign="top">

STORAGE\_TYPE column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_TABLE\_PERSISTENCE\_LOCATIONS

</td>
<td valign="top">

IS\_HISTORY column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_TABLE\_PRUNING\_STATISTICS

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

M\_TABLE\_VIRTUAL\_FILES

</td>
<td valign="top">

IS\_HISTORY column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_TEMPORARY\_TABLES

</td>
<td valign="top">

IS\_SYSTEM\_TABLE, IS\_TENANT\_SHARED\_DATA, IS\_TENANT\_SHARED\_METADATA, and SESSION\_TYPE columns are not available.

</td>
</tr>
<tr>
<td valign="top">

M\_TEMPORARY\_TABLE\_COLUMNS

</td>
<td valign="top">

COLLATION, MAX\_VALUE, MIN\_VALUE, CS\_DATA\_TYPE\_ID, and CS\_DATA\_TYPE\_NAME columns are not available.

</td>
</tr>
<tr>
<td valign="top">

M\_TEMPORARY\_VIEWS

</td>
<td valign="top">

IS\_UNICODE and IS\_TENANT\_SHARED columns are not available

</td>
</tr>
<tr>
<td valign="top">

M\_TEMPORARY\_VIEW\_COLUMNS

</td>
<td valign="top">

COLLATION, MAX\_VALUE, MIN\_VALUE, CS\_DATA\_TYPE\_ID, and CS\_DATA\_TYPE\_NAME columns are not available

</td>
</tr>
<tr>
<td valign="top">

M\_TEXT\_ANALYSIS\_LANGUAGES

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

M\_TEXT\_ANALYSIS\_MIME\_TYPES

</td>
<td valign="top">

Not available

</td>
</tr>
<tr>
<td valign="top">

M\_TRANSACTIONS

</td>
<td valign="top">

VOLUME\_ID column is now the ORIGIN\_VOLUME\_ID column, the PRIMARY\_TRANSACTION\_ID column is now the ORIGIN\_TRANSACTION\_ID, and the END\_TIME column is now the FINALIZE\_START\_TIME column.

Additionally, the following columns are not available: TRANSACTION\_SEQUENCE, CREATED\_VERSION\_COUNT, ALLOCATED\_VERSION\_SIZE, LOG\_SIZE, CURRENT\_STATEMENT\_SEQUENCE, ALLOCATED\_MEMORY\_SIZE, ACQUIRED\_METALOCK\_INDEX, LOG\_PARTITION\_ID, REDO\_LOG\_AMOUNT, UNDO\_LOG\_AMOUNT, MIN\_MVCC\_SNAPSHOT\_TIMESTAMP, LAST\_COMMIT\_ID, ACTIVE\_STATEMENT\_COUNT, ISOLATION\_LEVEL, LOG\_FLUSH\_ENABLED, LOGGING\_ENABLED

</td>
</tr>
<tr>
<td valign="top">

M\_TRANS\_TOKENS

</td>
<td valign="top">

ES\_SNAPSHOT\_COUNT, ES\_SNAPSHOTS columns are not available

</td>
</tr>
<tr>
<td valign="top">

M\_VOLUME\_...

</td>
<td valign="top">

All views starting with M\_VOLUME\_ are not available, including the M\_VOLUME\_IO views. Use M\_VOLUME\_IO\_TOTAL\_STATISTICS instead.

</td>
</tr>
<tr>
<td valign="top">

M\_VOLUMES

</td>
<td valign="top">

LIVECACHE\_STORE column is not available

</td>
</tr>
<tr>
<td valign="top">

M\_XS\_...

</td>
<td valign="top">

All views starting with M\_XS\_ are not available \(SAP HANA XS is not supported\)

</td>
</tr>
<tr>
<td valign="top">

VIRTUAL\_FUNCTION\_PACKAGES

</td>
<td valign="top">

Not available. Use VIRTUAL\_PACKAGES instead.

</td>
</tr>
</table>

**Related Information**  


[Compatibility with Other SAP HANA Versions](https://help.sap.com/viewer/3c53bc7b58934a9795b6dd8c7e28cf05/hanacloud/en-US/11cc86c44d0b4dd3bf70e16870d9d4df.html)

[System Views Reference](../020-System-Views-Reference/system-views-reference-20cbb10.md "SAP HANA includes information about the system views and monitoring views provided in the public SYS schema.")

