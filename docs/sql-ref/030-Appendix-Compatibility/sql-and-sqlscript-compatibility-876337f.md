<!-- loio876337f374c043b8b00d08a14a109352 -->

# SQL and SQLScript Compatibility

Lists SQL and SQLScript features in other versions of SAP HANA that are not available in SAP HANA Cloud.



## Introduction

Many of the SQL features in this list are associated with larger features that are not available in SAP HANA Cloud. For the list of larger features not available in SAP HANA Cloud, see the feature compatibility topic at the beginning of this guide.

If your solution uses any of the items listed here and you are migrating to SAP HANA Cloud, then you may need to make changes.

-   [SQL Statements](sql-and-sqlscript-compatibility-876337f.md#loio876337f374c043b8b00d08a14a109352__compatibility_guide_unavailable_sql)

-   [Reserved Keywords](sql-and-sqlscript-compatibility-876337f.md#loio876337f374c043b8b00d08a14a109352__compatibility_guide_reserved_keywords)

-   [Data Types](sql-and-sqlscript-compatibility-876337f.md#loio876337f374c043b8b00d08a14a109352__compatibility_guide_unavailable_data_types)

-   [Privileges](sql-and-sqlscript-compatibility-876337f.md#loio876337f374c043b8b00d08a14a109352__compatibility_guide_unavailable_privileges)

-   [Hints](sql-and-sqlscript-compatibility-876337f.md#loio876337f374c043b8b00d08a14a109352__compatibility_guide_unavailable_hints)

-   [Built-in Functions](sql-and-sqlscript-compatibility-876337f.md#loio876337f374c043b8b00d08a14a109352__compatibility_guide_unavailable_functions)

-   [Stored Procedures](sql-and-sqlscript-compatibility-876337f.md#loio876337f374c043b8b00d08a14a109352__compatibility_guide_unavailable_procedures)

-   [SQLScript](sql-and-sqlscript-compatibility-876337f.md#loio876337f374c043b8b00d08a14a109352__compatibility_guide_unavailable_sqlscript)




<a name="loio876337f374c043b8b00d08a14a109352__compatibility_guide_unavailable_sql"/>

## SQL Statements


<dl>
<dt><b>

Entire statements

</b></dt>
<dd>

-   ALTER SYSTEM ALTER DATAVOLUME \{ ADD | DROP \} PARTITION
-   ALTER SYSTEM BACKUP ENCRYPTION
-   ALTER SYSTEM ENCRYPTION CONFIGURATION
-   ALTER SYSTEM \{ INITIALIZE | UNINITIALIZE \} SERVICE 'etsserver'
-   ALTER SYSTEM LOG ENCRYPTION
-   ALTER SYSTEM \{ START | STOP \} DATABASE
-   ALTER SYSTEM \{ REGISTER | UNREGISTER \} SYSTEM REPLICATION SITE
-   ALTER SYSTEM \{ ENABLE | DISABLE \} SYSTEM REPLICATION
-   ALTER SYSTEM LOGGING
-   ALTER SYSTEM PERSISTENCE ENCRYPTION
-   ALTER SYSTEM SET ENCRYPTION ROOT KEYS BACKUP PASSWORD
-   ALTER SYSTEM VALIDATE ENCRYPTION ROOT KEYS BACKUP PASSWORD
-   BACKUP CHECK
-   \{ BACKUP | RECOVER \} DATA
-   \{ BACKUP | RECOVER \} ENCRYPTION ROOT KEYS
-   \{ BACKUP | RECOVER \} LIST DATA
-   \{ CREATE | ALTER | DROP \} CLIENTSIDE ENCRYPTION COLUMN KEY
-   \{ CREATE | ALTER | DROP \} CLIENTSIDE ENCRYPTION KEYPAIR
-   \{ CREATE | ALTER | DROP \} EXTENDED STORAGE
-   \{ CREATE | ALTER | DROP \} EXTENDED ROW STORAGE
-   \{ CREATE | ALTER | DROP | RENAME \} DATABASE
-   \{ CREATE | ALTER | DROP \} GEOCODE INDEX
-   \{ CREATE | ALTER | DROP \} STATISTICS ... FOR \{ DEFAULT | EXTENDED \} STORAGE
-   \{ CREATE | ALTER | DROP \} FULLTEXT INDEX
-   CREATE TYPE
-   CREATE HISTORY \[ COLUMN \] TABLE
-   DELETE HISTORY FROM
-   MERGE HISTORY DELTA OF
-   RECOVER DATABASE
-   \{ SET | UNSET \} SYSTEM LICENCE



</dd><dt><b>

CREATE TABLE statement clauses

</b></dt>
<dd>

-   \{ ENABLE | DISABLE \} SCHEMA FLEXIBILITY
-   PARTITION ... IS CURRENT
-   NO LOGGING RETENTION
-   WITHOUT HISTORY
-   PARTITION BY ... RANGE\( *<column\>* \) \( USING \{ DEFAULT | EXTENDED \} STORAGE …\)
-   \{ WITH | WITHOUT \} SCHEMA FLEXIBILITY
-   FOR DEFAULT STORAGE \{ PAGE | COLUMN \} LOADABLE
-   SERIES \(…\)



</dd><dt><b>

ALTER TABLE statement clauses

</b></dt>
<dd>

-   \{ ENABLE | DISABLE \} DELTA LOG
-   \{ ADD | ALTER \} PARTITION USING \{ DEFAULT | EXTENDED \} STORAGE \(...\)
-   FOR DEFAULT STORAGE \{ ALL PARTITIONS | NON CURRENT PARTITIONS \} \{ PAGE | COLUMN \} LOADABLE
-   \{ CREATE | DROP \} HISTORY
-   \{ ENABLE | ALTER | DISABLE \} SCHEMA FLEXIBLITY
-   FOR DEFAULT STORAGE \{ PAGE | COLUMN \} LOADABLE



</dd><dt><b>

CREATE USER statement

</b></dt>
<dd>

-   WITH IDENTITY FOR SAP \{ LOGON | ASSERTION \} TICKET



</dd><dt><b>

ALTER USER statement

</b></dt>
<dd>

-   RSERVE REMOTE SOURCES
-   WITH IDENTITY FOR SAP \{ LOGON | ASSERTION \} TICKET



</dd><dt><b>

CREATE REMOTE SOURCE statement

</b></dt>
<dd>

-   Creation of RSERVE and HADOOP adapters



</dd><dt><b>

IMPORT/EXPORT statements

</b></dt>
<dd>

-   EXPORT ... WITH \{ SCRAMBLE ... | STRIP \}
-   IMPORT FROM ... \{ WITH TABLE LOCK | TABLE LOCK | WITHOUT TYPE CHECK | NO TYPE CHECK \}
-   IMPORT FROM ... COLUMN LIST ... WITH SCHEMA FLEXIBILITY
-   IMPORT ... WITH \{ SCRAMBLE ... | STRIP \}



</dd><dt><b>

LOAD statement

</b></dt>
<dd>

-   HISTORY
-   WITH DELTA



</dd><dt><b>

SELECT statement

</b></dt>
<dd>

-   FROM *<hierarchy\_column\_view\>*
-   WHERE CONTAINS ... LINGUISTIC
-   WHERE CONTAINS ... FULLTEXT\( \{ ON | OFF | AUTOMATIC \}\)
-   GROUP BY \{ GROUPING SETS | ROLLUP | CUBE \} TEXT\_FILTER *<string\>* FILL UP SORT MATCHES TO TOP.
-   AS OF \{ COMMIT ID | UTCTIMESTAMP \}
-   WITH RANGE\_RESTRICTION
-   WITH HINT \( \) use in subqueries
-   WITH DATAPROVISIONING PARAMETERS
-   /\*+ *<comment style hint\>* \*/



</dd><dt><b>

SET statement

</b></dt>
<dd>

-   SESSION GROUP
-   HISTORY SESSION TO



</dd><dt><b>

UPDATE statement

</b></dt>
<dd>

-   UPDATE FROM \(updating columns by another result set\) is not supported. However, the MERGE INTO syntax added as of SAP HANA 2.0 \(on-premise\) can be used for any update scenario that was previously implemented using UPDATE FROM syntax. Helpful information about using MERGE INTO as a workaround can be found in the following SAP Note:[2241598 - Changed UPDATE FROM syntax can cause 'invalid table name' error](https://me.sap.com/notes/2241598 - Changed UPDATE FROM syntax can cause 'invalid table name' error)

-   UPDATE *<table\_name\>* **MERGE DELTA INTO HISTORY INDEX**



</dd><dt><b>

Subqueries

</b></dt>
<dd>

-   WITH HINT or WITH DATAPROVISIONING PARAMETER clause in a subquery enclosed by parentheses - in this case, the clause should appear only once and at the end, outside of the parentheses.



</dd>
</dl>



<a name="loio876337f374c043b8b00d08a14a109352__compatibility_guide_reserved_keywords"/>

## Reserved Keywords

Be sure to review the list of reserved words for SAP HANA Cloud found here: [Reserved Words](../010-SQL-Reference/reserved-words-28bcd6a.md).



<a name="loio876337f374c043b8b00d08a14a109352__compatibility_guide_unavailable_data_types"/>

## Data Types

-   ALPHANUM
-   BINTEXT
-   CHAR \(available but only as an alias of NCHAR\)
-   CLOB \(available but only as an alias of NCLOB\)
-   CS\_ALPHANUM
-   CS\_DATE
-   CS\_DECIMAL\_FLOAT
-   CS\_DOUBLE
-   CS\_FIXED
-   CS\_FIXEDSTRING
-   CS\_FLOAT
-   CS\_GEOMETRY
-   CS\_INT
-   CS\_LONGDATE
-   CS\_POINT
-   CS\_POINTZ
-   CS\_RAW
-   CS\_SDFLOAT
-   CS\_SECONDDATE
-   CS\_SECONDTIME
-   CS\_SHORTTEXT
-   CS\_STRING
-   CS\_TEXT
-   CS\_TEXT\_AE
-   CS\_TIME
-   DDIC\_ALNM
-   SHORTTEXT
-   ST\_DISK\_LOB
-   ST\_MEMORY\_LOB
-   TEXT
-   VARCHAR \(supported only as an alias of NVARCHAR\)



<a name="loio876337f374c043b8b00d08a14a109352__compatibility_guide_unavailable_privileges"/>

## User Privileges

-   APPLICATION PRIVILEGE
-   CREATE R SCRIPT
-   DATA ADMIN
-   EXTENDED STORAGE ADMIN
-   TENANT ADMIN
-   USER ADMIN



<a name="loio876337f374c043b8b00d08a14a109352__compatibility_guide_unavailable_hints"/>

## Hints

-   Inline SQL hints \(consider using WITH HINT instead\)
-   /\*+ *<comment style hint\>* +\*/
-   MIXED\_INVERTED\_INDEX\_JOIN
-   NO\_MIXED\_INVERTED\_INDEX\_JOIN
-   OPTIMIZE\_METAMODEL
-   NO\_OPTIMIZE\_METAMODEL



<a name="loio876337f374c043b8b00d08a14a109352__compatibility_guide_unavailable_functions"/>

## Built-in Functions

-   DOCUMENT\_OBJECT
-   HIGHLIGHTED
-   INDEXING\_ERROR\_CODE
-   INDEXING\_ERROR\_MESSAGE
-   INDEXING\_STATUS
-   LANGUAGE
-   LOCALTOUTC and UTCTOLOCAL - These functions are still supported. However, accessing dataset 'sap' without a dataset in place now returns an error.
-   MIMETYPE
-   PLAINTEXT
-   SNIPPETS
-   TEXT\_FILTER
-   TM\_GET\_RELATED\_TERMS
-   TM\_GET\_RELEVANT\_TERMS
-   TM\_GET\_SUGGESTED\_TERMS
-   TM\_GET\_RELATED\_DOCUMENTS
-   TM\_GET\_RELEVANT\_DOCUMENTS
-   TM\_CATEGORIZE\_KNN



<a name="loio876337f374c043b8b00d08a14a109352__compatibility_guide_unavailable_procedures"/>

## Stored Procedures

-   BASKETANALYSIS - available, but the FILTER parameter is now called FILTER\_STRING
-   BW\_CONVERT\_CLASSIC\_TO\_IMO\_CUBE
-   BW\_F\_FACT\_TABLE\_COMPRESSION
-   BW\_PRECHECK\_ACQUIRE\_LOCK
-   BW\_PRECHECK\_ACQUIRE\_LOCK\_WITH\_TYPE
-   BW\_PRECHECK\_RELEASE\_LOCK
-   CDS\_SCHEMA\_LAST\_MODIFIED\_TIME
-   CHECK\_ES
-   CHECK\_PLATFORM
-   CONVERT\_CLASSIC\_TO\_IMO\_CUBE
-   DISABLE\_OBJECT\_VERSION\_VALIDATION
-   DSO\_ACTIVATE
-   DSO\_CREATECHANGELOG
-   DSO\_MIGRATE
-   DSO\_MIGRATE\_SIMPLE
-   DSO\_REHASH
-   DSO\_ROLLBACK
-   ENABLE\_OBJECT\_VERSION\_VALIDATION
-   ES\_REBUILD\_INDEX
-   ETS\_ADMIN\_CONSOLE\_PROC
-   EXPOSE\_NODE
-   IS\_OBJECT\_VERSION\_VALIDATION\_ENABLED
-   RETRY\_DOCUMENT\_INDEXING
-   RPROC\_MOVE\_RTABLE\_TO\_DB, RPROC\_MOVE\_RTABLE\_TO\_DBM\_FULLTEXT\_QUEUES
-   SEARCH\_CATALOG\_CLEANUP
-   TA\_ANALYZE
-   TM\_CATEGORIZE\_KNN
-   TM\_GET\_RELATED\_TERMS
-   TM\_GET\_RELEVANT\_TERMS
-   TM\_GET\_SUGGESTED\_TERMS
-   TM\_GET\_RELATED\_DOCUMENTS
-   TM\_GET\_RELEVANT\_DOCUMENTS
-   TEXT\_CONFIGURATION\_CLEAR
-   TEXT\_CONFIGURATION\_CREATE
-   TEXT\_CONFIGURATION\_DROP
-   TREXViaDBSL
-   TREXviaDBSLWithParameter
-   UPDATE\_TRANS\_TOKEN\_HISTORY



<a name="loio876337f374c043b8b00d08a14a109352__compatibility_guide_unavailable_sqlscript"/>

## SQLScript

-   CREATE PROCEDURE ... LANGUAGE RLANG
-   CREATE PROCEDURE ... WITH RESULT VIEW *<name\>*
-   ALTER PROCEDURE ... RECOMPILE
-   CALL *<procedure\>* ... WITH VERSION VALIDATION
-   CALL *<procedure\>* ... WITH OVERVIEW
-   Inside a function or procedure body definition \(*<statement\_body\>* clause\):
    -   TRACE\( *<param\>* \)
    -   CE\_AGGREGATION
    -   CE\_CALC\_VIEW
    -   CE\_COLUMN\_TABLE
    -   CE\_COMM2R
    -   CE\_CONVERSION
    -   CE\_FULL\_OUTER\_JOIN
    -   CE\_JOIN
    -   CE\_JOIN\_VIEW
    -   CE\_LEFT\_OUTER\_JOIN
    -   CE\_MERGE
    -   CE\_OLAP\_VIEW
    -   CE\_PARTITION
    -   CE\_PROJECTION
    -   CE\_RIGHT\_OUTER\_JOIN
    -   CE\_UNION\_ALL
    -   CE\_VERTICAL\_UNION


**Related Information**  


[Compatibility with Other SAP HANA Versions](https://help.sap.com/viewer/3c53bc7b58934a9795b6dd8c7e28cf05/hanacloud/en-US/11cc86c44d0b4dd3bf70e16870d9d4df.html)

[SQL Reference](../010-SQL-Reference/sql-reference-20ff532.md "")

[SAP HANA Cloud, SAP HANA SQLScript Reference](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/28f2d64d4fab4e789ee0070be418419d.html "This reference describes how to use the SQL extension SAP HANA SQLScript to embed data-intensive application logic into SAP HANA.") :arrow_upper_right:

[SAP Note 2868742](https://me.sap.com/notes/2868742 "Differences between SAP HANA Cloud and SAP HANA Platform for SQL, SQLScript and SAP HDI (SAP HANA Deployment Infrastructure")

