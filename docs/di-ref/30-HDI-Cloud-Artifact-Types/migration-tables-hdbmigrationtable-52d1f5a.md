<!-- loio52d1f5acfa754a7887e21226641eb261 -->

# Migration Tables \(.hdbmigrationtable\)

The migration-table plugin transforms a design-time table resource into a table database object.



In contrast to the table plug-in \(`.hdbtable`\), the migration-table plug-in \(`.hdbmigrationtable`\) uses explicit versioning and migration tasks, which means that the modifications of the database table are explicitly specified in the design-time file and carried out on the database table exactly as specified, without incurring the cost of an internal table-copy operation such as the one performed by the `.hdbtable` plug-in. This behavior makes the `.hdbmigrationtable` plug-in especially useful for tables that contain a lot of data. When a new version of an already existing table is deployed, the plug-in performs the migration statements that are missing for the new version.

> ### Note:  
> It is possible to migrate from `.hdbtable` to `.hdbmigrationtable`. However, the latest deployed definition of the `.hdbtable` file must match the definition of either version one \(1\) or the current version of the `.hdbmigrationtable` file. If no structural difference exists between the two table definitions, the table will be treated as the current version, which means that no migrations are started. For more information about how to switch formats, see *Switching from `.hdbtable` to `.hdbmigrationtable`* below.



### Switching from `.hdbtable` to `.hdbmigrationtable`

The following high-level steps show how to switch from `.hdbtable` to `.hdbmigrationtable`:

1.  Add a new design-time table artifact \(`hdbmigrationtable`\) to your database application project.
2.  Ensure that the new table artifact \(`hdbmigrationtable`\) has the same content as the existing `hdbtable` artifact in the application project.
3.  Add the name of \(and path to\) the `hdbtable` artifact to the undeploy allow list \(`undeploy.json`\).
4.  Delete the old design-time `hdbtable` artifact from the application project.
5.  Deploy the application.

For more information about the undeploy allow list \(`undeploy.json`\), see *Related Information* below.



<a name="loio52d1f5acfa754a7887e21226641eb261__section_emr_3xg_1hb"/>

## Migrations

The migration-table file format uses a syntax that is similar in style to the Data Definition Language \(DDL\); the file combines the most recent definition of the table and the migration statements required per table version to transform the table from the previous version to the new \(migrated\) version. Versions with the same definition as the previous version can be omitted. Only `ALTER TABLE`, `RENAME COLUMN`, `INSERT`, `DELETE`, `UPDATE`, `UPSERT`, and `COMMENT ON [TABLE|COLUMN]` statements are supported for the migrations. The migration-table plug-in does not support any of the following statements:

-   `ALTER TABLE ... [PARTITION ] ... LOADABLE`

-   `ALTER TABLE ... OWNER TO`

-   `ALTER TABLE ... MOVE TO`

-   `ALTER TABLE ... ENABLE|DISABLE TRIGGER` 


> ### Restriction:  
> Changes to partitioning must be placed before any DML statements in the `.hdbmigrationtable` file. This is also the case for different migrations of one table when the partitioning and DML statements are performed in the same deployment.

The initial deployment of a migration-table file creates the table in the most recent version but does not perform any migration. When deploying a new version of an existing file, the migration steps are performed to update the table to the most recent version.

After finishing the migrations, the migration-table plug-in checks whether the migrated table matches the new definition.



<a name="loio52d1f5acfa754a7887e21226641eb261__section_sbl_fxg_1hb"/>

## Development Versions and Development Mode

For development purposes, it is possible to specify a development version with a separate definition, which is used as the base for the current migration development. During deployment in a development system, the migration-table plug-in \(running in development mode\) drops the existing table and creates the development version. Then the plug-in runs the migration starting at the development version instead. The development version is only considered if the build parameter `development_mode` is set to “true”.

> ### Note:  
> In development mode all data stored in the table is lost.



<a name="loio52d1f5acfa754a7887e21226641eb261__section_ih1_hxg_1hb"/>

## General Limitations

It is important to bear in mind the following requirements and limitations:

-   Table types are limited to `ROW` and `COLUMN`, and specifying the type is mandatory.

-   A table must be self-contained and cannot reference another table. For this reason, it is not possible to define a table “like” another table \(`TABLE A LIKE B`\), or a table based on a query \(`TABLE A AS SELECT … FROM B`\).

-   Flexible tables \(using the `WITH SCHEMA FLEXIBILITY` clause\) and `HISTORY` tables are not supported.

-   Named constraints are not supported.

-   Client-side encryption \(`CLIENTSIDE ENCRYPTION`\) is not supported.

-   Virtual tables are handled by the virtual-table build plug-in \(`hdbvirtualtable`\).

-   Foreign-key constraints are handled by the constraint build plug-in \(`hdbconstraint`\).


Table and column comments can be defined in-place by using the `COMMENT` keyword. Tables also support forward declarations for database-level associations using the `WITH ASSOCIATIONS` clause. In this scenario, the table plug-ins creates an additional intermediate "validate" artifact as part of the deployment, which positions itself between the table artifact, the artifacts which are referenced in the `WITH ASSOCIATIONS` clause, and the artifacts which consume the table artifact. The "validate" artifact performs a validation of the forward declared associations and issues a warning if an association is not valid.

> ### Note:  
> It is not possible to use the migration-table plug-in to set up a system-versioned table or an application-time-period table; separate plug-ins are available for these purposes. For more details, see *Related Information* below.

The following options are available concerning the management of table partitions:

-   Make changes in the run-time version of the migration-table :

    In this case, users with the \``PARTITION ADMIN`\` privilege can manage the partitions only by altering the run-time object. However, an initial partitioning can set in the design-time version of the migration-table.

    > ### Note:  
    > Administrators with the `PARTITION ADMIN` privilege can perform administrative actions using SQL statements pertaining to partitioning even though they have not been explicitly granted the \``ALTER`\` privilege. In such cases, however, to ensure that any alterations and changes do not cause loss of data, structural changes to the table, or allow implicit \(or explicit\) access to the data itself, only a restricted set of `ALTER TABLE` commands is available. For example, it is not possible to run either `[<drop_partition_clauses>]` or `[<merge_partition_clauses>]`.

-   Make changes in the design-time version of the migration-table:

    In this case, alterations to the partition are not allowed in the run-time object. Users must put partition change statements in the design-time version of the artifact, instead.


For security reasons, it is not possible to use the HDI API to grant the `ALTER` privilege to a database user. However, you can use a role-definition that specifies the `ALTER` privilege as an object privilege of `"type":"TABLE"` for any user to whom the role is assigned. The user can then run the `ALTER TABLE` statements required to do the partitioning. For more information about the syntax requirements for HDI role definitions, see *Roles \(.hdbrole\)* in *Related Information* below.

> ### Note:  
> If you want to assign the `ALTER` privilege directly to the HDI container's run-time access user \(`*_RT`\), you can customize the `default_access_role`. For more information about the `default_access_role`, see *SAP HDI Security in the Context of Cloud Foundry* in *Related Information* below.



<a name="loio52d1f5acfa754a7887e21226641eb261__section_wfy_cxg_1hb"/>

## Example Artifact Code

The following examples show how the table definition changes over time and how the different versions are considered in the migration process:



### Initial Version

```sql
== version = 1 
COLUMN table PERSON (
	FIRSTNAME varchar(100), 
	NAME varchar(100)
	) 
```



### Patched Version

For new HDI containers created during the deployment of this patch, the table created will have the structure defined in `== version = 2`.

> ### Note:  
> In the following code example, changes to the previous version of the table structure are displayed in **bold** font type.

```sql
== version = 2 
COLUMN table PERSON ( 
     FIRSTNAME varchar(100), 
     LASTNAME varchar(100), 
     STREET varchar(100), 
     CITY varchar(100) 
) 

== migration = 2 
alter table PERSON add (STREET varchar(100)); 
alter table PERSON add (CITY varchar(100)); 
rename column PERSON.NAME to LASTNAME; 
```

For existing HDI containers used during the deployment of this patch, any tables with the structure defined in `== version = 1` will undergo the migration steps described in `== migration = 2`.



### Another Patched Version

For new HDI containers created during the deployment of this patch, the table created will have the structure defined in `== version = 3`.

> ### Note:  
> In the following code example, changes to the previous version of the table structure are displayed in **bold** font type.

```sql
== version = 3 
COLUMN table PERSON ( 
     FIRSTNAME varchar(100), 
     LASTNAME varchar(100), 
     STREET varchar(200), 
     HOUSENUMBER int, 
     CITY varchar(100) 
) 

== migration = 2 
alter table PERSON add (STREET varchar(100)); 
alter table PERSON add (CITY varchar(100)); 
rename column PERSON.NAME to LASTNAME; 

== migration = 3 
alter table PERSON alter (STREET varchar(200)); 
alter table PERSON add (HOUSENUMBER int);
```

For existing HDI containers used during the deployment of this patch, any tables created with the structure defined in `== version = 1` will undergo the steps described in `== migration = 2` and then the steps described in `== migration = 3`. Tables created with the structure defined in `== version = 2` will undergo the migration steps described in `== migration = 3`.



### N<sup>th</sup> Patched Version

```sql
== version = n 
COLUMN table PERSON ( ... most recent target structure ... ) 

== migration = 2 
alter ... from v_1 -> v_2 ... 

== migration = 3 
alter ... from v_2 -> v_3 ... 

== migration = 4 
alter ... from v_3 -> v_4 ... 

... same for 5..n-2 ... 

== migration = n-1 
alter ... from v_n-2 -> v_n-1 ... 

== migration = n 
alter ... from v_n-1 -> v_n ...
```



### Development Version

```sql
== version=28 
COLUMN TABLE "com.sap.hana.example::CUSTOMERS" ( 
  "ID" INTEGER, 
  "NAME" NVARCHAR(256), 
  "ACTIVE" TINYINT, 
  "COUNTRY" NVARCHAR(256), 
  PRIMARY KEY ("ID") 
) 

== dev-version=7 
COLUMN TABLE "com.sap.hana.example::CUSTOMERS" ( 
  "ID" INTEGER, 
  "FULLNAME" NVARCHAR(256), 
  PRIMARY KEY ("ID") 
) 

== migration=10 
ALTER TABLE "com.sap.hana.example::CUSTOMERS" ADD ("ACTIVE" INT); 
RENAME COLUMN "com.sap.hana.example::CUSTOMERS"."FULLNAME" TO "NAME"; 

== migration=19 
ALTER TABLE "com.sap.hana.example::CUSTOMERS" ADD ("COUNTRY" NVARCHAR(256));
ALTER TABLE "com.sap.hana.example::CUSTOMERS" ALTER ("ACTIVE" TINYINT);
```



<a name="loio52d1f5acfa754a7887e21226641eb261__section_ubd_bxg_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbmigrationtable" : {
>    "plugin_name" : "com.sap.hana.di.table.migration"
> }
> ```

**Related Information**  


[Application Time-Period Tables \(.hdbapplicationtime \)](application-time-period-tables-hdbapplicationtime-73c7b80.md "Transforms a design-time application time-period table into a database table object with application-time period.")

[System Versioning Tables \(.hdbsystemversioning\)](system-versioning-tables-hdbsystemversioning-5794b34.md "Transforms a design-time, system-versioned table that refers to a current and history table into a system-versioned table database object.")

[SAP HDI Security in the Context of Cloud Foundry](../10-HDI-Cloud-Administration/11-HDI-Cloud-Admin-Security/sap-hdi-security-in-the-context-of-cloud-foundry-4457f75.md "An overview of the security considerations to bear in mind when enabling SAP HDI for use in the context of Cloud Foundry.")

[Roles \(.hdbrole and .hdbroleconfig\)](roles-hdbrole-and-hdbroleconfig-625d773.md "Transform a design-time role resource (.hdbrole) into a run-time role object.")

[HDI Delta Deployment and Undeploy Allow List \(SAP HANA Cloud Database Developer Guide for Business App Studio\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/c2b99f19e9264c4d9ae9221b22f6f589/ebb0a1d1d41e4ab0a06ea951717e7d3d.html)

