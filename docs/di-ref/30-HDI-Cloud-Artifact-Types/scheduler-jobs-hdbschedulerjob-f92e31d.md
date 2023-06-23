<!-- loiof92e31d2a23f4470829ab300dcce850e -->

# Scheduler Jobs \(.hdbschedulerjob\)

Transforms a design-time scheduler-job resource into a scheduler job on a database table.



The scheduler-job plug-in transforms a design-time scheduler-job resource \(defined in a `.hdbschedulerjob` artifact\) into a scheduler job on a database table. The file format required for the `.hdbschedulerjob` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL command `CREATE SCHEDULER JOB`, but without the leading `CREATE`.



<a name="loiof92e31d2a23f4470829ab300dcce850e__section_a3z_fzh_1hb"/>

## Example Artifact Code

The following code shows a simple example of a scheduler-job definition of a sequence for SAP HDI:

> ### Code Syntax:  
> `/src/SCHEDULER_JOB_A.hdbschedulerjob`
> 
> ```sql
> SCHEDULER JOB "com.sap.hana.example::SCHEDULER_JOB_A"
> CRON ‘* * * * * * 0’ ENABLE PROCEDURE "com.sap.hana.example::PROCEDURE_A" 
> PARAMETERS PI = 42
> ```



<a name="loiof92e31d2a23f4470829ab300dcce850e__section_mz5_2zh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbschedulerjob" : {
>    "plugin_name" : "com.sap.hana.di.schedulerjob"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

