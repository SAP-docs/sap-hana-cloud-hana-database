<!-- loio209f5020751910148fd8fe88aa4d79d9 -->

# Introduction to SQL

This chapter describes the SAP HANA database implementation of Structured Query Language \(SQL\).



-    [SQL](introduction-to-sql-209f502.md#loio209f5020751910148fd8fe88aa4d79d9___bsql_introduction_1sql_introduction_sql) 

-    [Supported languages and code pages](introduction-to-sql-209f502.md#loio209f5020751910148fd8fe88aa4d79d9___bsql_introduction_1sql_introduction_supported_languages_and_code_pages) 

-    [Comments](introduction-to-sql-209f502.md#loio209f5020751910148fd8fe88aa4d79d9___bsql_introduction_1sql_introduction_comment) 

-    [Identifiers](introduction-to-sql-209f502.md#loio209f5020751910148fd8fe88aa4d79d9___bsql_introduction_1sql_introduction_identifiers) 

-   [Identifiers and case sensitivity](introduction-to-sql-209f502.md#loio209f5020751910148fd8fe88aa4d79d9__identifiers_case)

-   [User names and passwords](introduction-to-sql-209f502.md#loio209f5020751910148fd8fe88aa4d79d9__usernames_and_passwords)

-   [Quotation marks](introduction-to-sql-209f502.md#loio209f5020751910148fd8fe88aa4d79d9___bsql_introduction_1sql_introduction_quotation_marks)




<a name="loio209f5020751910148fd8fe88aa4d79d9___bsql_introduction_1sql_introduction_sql"/>

## SQL

SQL stands for Structured Query Language. It is a standardized language for communicating with a relational database. SQL is used to retrieve, store or manipulate information in the database.

SQL statements perform the following tasks:

-   Schema definition and manipulation

-   Data manipulation

-   System management

-   Session management

-   Transaction management




<a name="loio209f5020751910148fd8fe88aa4d79d9___bsql_introduction_1sql_introduction_supported_languages_and_code_pages"/>

## Supported languages and code pages

The SAP HANA database supports Unicode to allow the use of all languages in the Unicode Standard and 7 Bit ASCII code page without restriction.



<a name="loio209f5020751910148fd8fe88aa4d79d9___bsql_introduction_1sql_introduction_comment"/>

## Comments

You can add comments to improve the readability and maintainability of your SQL statements. Comments are delimited in SQL statements as follows:

-   Double hyphens "--". Everything after the double hyphen until the end of a line is ignored by the SQL parser.

-   "/\*" and "\*/". This style of commenting is used to place comments on multiple lines. All text between the opening "/\*" and closing "\*/" is ignored by the SQL parser.




<a name="loio209f5020751910148fd8fe88aa4d79d9___bsql_introduction_1sql_introduction_identifiers"/>

## Identifiers

Identifiers are used to represent names used in SQL statement including table name, view name, synonym name, column name, index name, function name, procedure name, user name, role name, and so on. There are two kinds of identifiers, undelimited identifiers and delimited identifiers.

-   Undelimited table and column names must start with a letter and contain only letters, digits, or underscores "\_".

-   Delimited identifiers are enclosed in the delimiter, double quotes. The identifier can then contain any character including special characters. "AB$%CD" is a valid identifier name for example.

-   Limitations:

    -   "\_SYS\_" is reserved exclusively for database engine and is therefore not allowed at the beginning of schema object names.

    -   The role name and user name must be specified as undelimited identifiers.

    -   The maximum length for identifiers is 127 characters.





<a name="loio209f5020751910148fd8fe88aa4d79d9__identifiers_case"/>

## Identifiers and case sensitivity

Identifiers without double-quotes in SQL syntax are converted to upper case when processed by the server. For example, the statement `CREATE COLUMN TABLE MyTAB...` creates a table called MYTAB, whereas `CREATE COLUMN TABLE "MyTab"` creates a table called MyTab--and both tables can co-exist in the database.

Specifying identifiers without double-quotes is allowed but can cause ambiguity later when querying or performing operations on objects where casing in the identifier name is significant. A recommendation is to standardize to using double-quotes around all identifiers in SQL statements where ambiguity may be a concern.



<a name="loio209f5020751910148fd8fe88aa4d79d9__usernames_and_passwords"/>

## User names and passwords

User names may contain underscores and hyphens without requiring quotes. For a list of unpermitted characters in user names, see Unpermitted Characters in User Names topic in the *SAP HANA Cloud, SAP HANA Database Administration Guide*.

Passwords must be a minimum length of 8. For more information on passwords see the Password Policy Configuration Options topic in the *SAP HANA Cloud, SAP HANA Database Administration Guide*



<a name="loio209f5020751910148fd8fe88aa4d79d9___bsql_introduction_1sql_introduction_quotation_marks"/>

## Quotation marks

Single quotation marks are used to delimit string literals. A single quotation mark itself can be represented using two single quotation marks. Double quotation marks are used to delimit identifiers. A double quotation mark itself can be represented using two double quotation marks.

**Related Information**  


[Characters Not Permitted in User Names](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/55d3b5a01166494582cc12f70ccfa17f.html "User names can contain any Compatibility Encoding Scheme for UTF-16: 8-Bit (CESU-8) characters except for a small subset.") :arrow_upper_right:

[Password Policy Configuration Options](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/61662e3032ad4f8dbdb5063a21a7d706.html "The password policy of the database is defined by parameters in the password policy section of the indexserver.ini configuration file. The initial password policy of a user group is a copy of the database password policy.") :arrow_upper_right:

[SQL Notation Conventions](sql-notation-conventions-209e0cd.md "SQL syntax notation conventions used in this guide.")

