<!-- loio4b06066848a248509336bdc534dbeb21 -->

# What's New for SQL Compatibility

Lists SQL features that were previously unavailable in SAP HANA Cloud, SAP HANA Cloud database but that are now available.


<dl>
<dt><b>

QRC 4/2021

</b></dt>
<dd>

-   \{ CREATE | ALTER \} LDAP PROVIDER... ENABLE USER CREATION FOR LDAP clause. See [CREATE LDAP PROVIDER Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/create-ldap-provider-statement-access-control-3b72203.md), and [ALTER LDAP PROVIDER Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/alter-ldap-provider-statement-access-control-ae9ba28.md).

-   [ALTER SYSTEM \{ADD | REMOVE\} ABSTRACT SQL PLAN FILTER \(System Management\)](../010-SQL-Reference/012-SQL-Statements/alter-system-add-remove-abstract-sql-plan-filter-system-management-9c6ac16.md)
-   [ALTER SYSTEM \{START | STOP\} CAPTURE ABSTRACT SQL PLAN \(System Management\)](../010-SQL-Reference/012-SQL-Statements/alter-system-start-stop-capture-abstract-sql-plan-system-management-dc46271.md)
-   [ALTER SYSTEM \{ENABLE | DISABLE | REMOVE\} ABSTRACT SQL PLAN \(System Management\)](../010-SQL-Reference/012-SQL-Statements/alter-system-enable-disable-remove-abstract-sql-plan-system-management-031158f.md)
-   [ALTER SYSTEM \{START | STOP\} APPLY ABSTRACT SQL PLAN \(System Management\)](../010-SQL-Reference/012-SQL-Statements/alter-system-start-stop-apply-abstract-sql-plan-system-management-935ecd1.md)
-   In the CREATE TABLE statement, the TEMPORARY ROW TABLE clause is now available. See [CREATE TABLE Statement \(Data Definition\)](../010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md).




</dd><dt><b>

QRC 3/2021

</b></dt>
<dd>

-   In the ALTER TABLE statement, the AT LOCATION subclause of the PARTITION BY clause is now available for use. See [ALTER TABLE Statement \(Data Definition\)](../010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md).




</dd><dt><b>

QRC 2/2021

</b></dt>
<dd>

-   The following partitioning properties are now available in the PARTITION BY clause of the [ALTER TABLE Statement \(Data Definition\)](../010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md):

    -   partition-level GROUP NAME, GROUP TYPE and GROUP SUBTYPE

    -   NUMA node preference

    -   INSERT ON/OFF options





</dd><dt><b>

QRC 1/2021

</b></dt>
<dd>

-   [CREATE LDAP PROVIDER Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/create-ldap-provider-statement-access-control-3b72203.md)
-   [ALTER LDAP PROVIDER Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/alter-ldap-provider-statement-access-control-ae9ba28.md)
-   [DROP LDAP PROVIDER Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/drop-ldap-provider-statement-access-control-340e913.md)
-   [VALIDATE LDAP PROVIDER Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/validate-ldap-provider-statement-access-control-4181217.md)



</dd><dt><b>

QRC 04/2020

</b></dt>
<dd>

-   [ALTER SAML PROVIDER Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/alter-saml-provider-statement-access-control-20d04f7.md)
-   [DROP SAML PROVIDER Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/drop-saml-provider-statement-access-control-20d76c8.md)
-   ALTER/DROP/REFEFERENCES SAML PROVIDER privileges \([GRANT Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md)\)
-   [ALTER JWT PROVIDER Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/alter-jwt-provider-statement-access-control-61863f6.md)
-   [DROP JWT PROVIDER Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/drop-jwt-provider-statement-access-control-e3caf68.md)
-   ALTER/DROP/REFERENCES JWT PROVIDER privileges \([GRANT Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md)\)
-   [JSON Document Store Statements](../010-SQL-Reference/012-SQL-Statements/json-document-store-statements-2282aef.md)
-   [CREATE X509 PROVIDER Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/create-x509-provider-statement-access-control-3b3163d.md)
-   [ALTER X509 PROVIDER Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/alter-x509-provider-statement-access-control-4f7e59d.md)
-   [DROP X509 PROVIDER Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/drop-x509-provider-statement-access-control-f7a37e8.md)



</dd><dt><b>

QRC 03/2020

</b></dt>
<dd>

-   CREATE JWT PROVIDER privilege \([GRANT Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md)\)
-   [CREATE JWT PROVIDER Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/create-jwt-provider-statement-access-control-bfe3daf.md)
-   CREATE SAML PROVIDER privilege \([GRANT Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md)\)
-   [CREATE SAML PROVIDER Statement \(Access Control\)](../010-SQL-Reference/012-SQL-Statements/create-saml-provider-statement-access-control-20d4cca.md)



</dd><dt><b>

QRC 02/2020

</b></dt>
<dd>

-   Ability to import and export data using these statements: [IMPORT Statement \(Data Import Export\)](../010-SQL-Reference/012-SQL-Statements/import-statement-data-import-export-20f75ad.md), and [EXPORT Statement \(Data Import Export\)](../010-SQL-Reference/012-SQL-Statements/export-statement-data-import-export-20da0be.md).
-   [SAP HANA Automated Predictive Library \(APL\)](https://help.sap.com/viewer/product/apl/latest/en-US)



</dd>
</dl>

**Related Information**  


[Compatibility with Other SAP HANA Versions](https://help.sap.com/viewer/3c53bc7b58934a9795b6dd8c7e28cf05/hanacloud/en-US/11cc86c44d0b4dd3bf70e16870d9d4df.html)

