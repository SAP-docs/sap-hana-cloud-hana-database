<!-- loio5794b348711f4963999266a2d2e6f8de -->

# System Versioning Tables \(.hdbsystemversioning\)

Transforms a design-time, system-versioned table that refers to a current and history table into a system-versioned table database object.



The System Versioning Table plug-in converts the columns `validfrom` and `validto` of the current table `GENERATED ALWAYS AS ROW START` and `GENERATED ALWAYS AS ROW END` columns, respectively. In addition, the plug-in adds a `SYSTEM_TIME` period over the `validfrom` and `validto` columns in order to enforce a `validfrom` <= `validto` constraint. Last of all, the plug-in establishes the system-version link between the current and the history table.

> ### Tip:  
> For more information about system-versioned tables, see the *SAP HANA Cloud, SAP HANA Database SQL Reference Guide*, for example, the section describing *system\_versioning\_spec* in the chapter *CREATE TABLE Statement \(Data Definition\)*, as indicated in *Related Information* below, where you can also find a link to information about the HDI plug-in for application time-period tables.



<a name="loio5794b348711f4963999266a2d2e6f8de__section_vfg_s23_1hb"/>

## Example Artifact Code

The following code shows a simple example of a system-versioned table for SAP HDI:

> ### Code Syntax:  
> `/src/CUSTOMERS.hdbsystemversioning`
> 
> ```sql
> SYSTEM VERSIONING “CUSTOMERS”(validfrom, validto) HISTORY TABLE “CUSTOMERS_HISTORY” NOT VALIDATED
> ```



<a name="loio5794b348711f4963999266a2d2e6f8de__section_cyx_n23_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbsystemversioning" : { 
>    "plugin_name" : "com.sap.hana.di.systemversioning"
> }
> ```

**Related Information**  


[CREATE TABLE Statement \(SAP HANA Cloud, SAP HANA Database SQL Reference Guide\)](https://help.sap.com/viewer/c1d3f60099654ecfb3fe36ac93c121bb/latest/en-US/20d58a5f75191014b2fe92141b7df228.html)

[Application Time-Period Tables \(.hdbapplicationtime \)](application-time-period-tables-hdbapplicationtime-73c7b80.md "Transforms a design-time application time-period table into a database table object with application-time period.")

[Application-Time Period Tables \(SAP HANA Cloud, SAP HANA Database Administration Guide\)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/latest/en-US/2e37d6a82f7b48ccbfcc5a1a6ce490f5.html)

