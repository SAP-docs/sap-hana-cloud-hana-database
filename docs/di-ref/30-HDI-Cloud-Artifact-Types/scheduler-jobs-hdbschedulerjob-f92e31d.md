<!-- loiof92e31d2a23f4470829ab300dcce850e -->

# Scheduler Jobs \(.hdbschedulerjob\)

Transforms a design-time scheduler-job resource into a scheduler job on a database procedure.



The scheduler-job plug-in transforms a design-time scheduler-job resource \(defined in a `.hdbschedulerjob` artifact\) into a scheduler job on a database procedure.

> ### Note:  
> It is not possible to define multiple job schedules in a single `.hdbschedulerjob` artifact.

The file format required for the `.hdbschedulerjob` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL command `CREATE SCHEDULER JOB`, but without the leading `CREATE`.



<a name="loiof92e31d2a23f4470829ab300dcce850e__section_a3z_fzh_1hb"/>

## Example Artifact Code

The following code shows a simple example of a scheduler-job definition for SAP HDI:

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

[CREATE SCHEDULER JOB Statement \(SAP HANA SQL Reference Guide for SAP HANA Platform\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/c1d3f60099654ecfb3fe36ac93c121bb/d7d43d818366460dae1328aab5d5df4f.html)

