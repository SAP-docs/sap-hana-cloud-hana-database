<!-- loioa216fd8f1b494e6f81b7bf0f80b255eb -->

# Creating Data Persistence Artifacts with SQL DDL

You can use SQL DDL to define the underlying database objects that store and provide data for your application, for example, tables and views.

As part of the process of defining the data model for your application, you create database design-time artifacts such as tables and views, for example using the SQL Data Definition Language \(DDL\). Each artifact must be defined in on DDL documents. You can find some simple examples of the syntax required for specific data artifacts in the following sections:

-   SQL DDL tables \(`.hdbtable`\)

-   SQL DDL views \(`.hdbview`\)

-   SQL DDL constraints \(`.hdbconstraint`\)

-   SQL DDL indexes \(`.hdbindex`\)

-   SAP HANA Database Roles \(`.hdbrole`\)

    Unlike the other design-time artifacts listed here, the SAP HANA database role is defined using the JavaScript Object Notation \(JSON\) syntax.

-   SQL DDL Structured Privileges \(`.hdbstructuredprivilege`\)


> ### Tip:  
> The tasks in this section create artifacts that, in some cases, are interdependent. For example, a table-data artifact is used to load initial data into two tables from which a view selects information that is visible only to users with the appropriate structured privilege. A role is also used to broaden access scope to other database users.

**Related Information**  


[Data Definition Statements \(SQL Reference\)](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/latest/en-US/209ce8cd75191014bcd59c2b379a17c9.html)

[Create a Database Table with SQL Data Definition Language](create-a-database-table-with-sql-data-definition-language-879ce23.md "Define a design-time database table using the SQL Data Definition Language (DDL) syntax.")

[Create a Database View with SQL Data Definition Language](create-a-database-view-with-sql-data-definition-language-4920a3a.md "Define a design-time database view using the SQL Data Definition Language (DDL) syntax.")

[Load Data into a Database Table with the "hdbtabledata" Artifact](load-data-into-a-database-table-with-the-hdbtabledata-artifact-91b08cc.md "Use an hdbtabledata artifact to load data external data into an existing database table.")

[Create a Structured Privilege Using SQL Data Definition Language](create-a-structured-privilege-using-sql-data-definition-language-404d6af.md "Define a structured privilege using the SQL Data Definition Language (DDL) syntax.")

[Create a Database Role](create-a-database-role-492729c.md "Define a design-time database role using the JavaScript Object Notation (JSON) syntax.")

[Create a Database Constraint with SQL Data Definition Language](create-a-database-constraint-with-sql-data-definition-language-65b61c4.md "Define a design-time database constraint using the SQL Data Definition Language (DDL) syntax.")

[Create an Index with SQL Data Definition Language](create-an-index-with-sql-data-definition-language-90de80c.md "Define a design-time database index using the SQL Data Definition Language (DDL) syntax.")

