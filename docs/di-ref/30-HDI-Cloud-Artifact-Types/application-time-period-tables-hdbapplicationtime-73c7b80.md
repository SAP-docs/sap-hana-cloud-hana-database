<!-- loio73c7b80318ba4405a8769e6ceb41ec64 -->

# Application Time-Period Tables \(.hdbapplicationtime \)

Transforms a design-time application time-period table into a database table object with application-time period.



The Application-Time Period Table plug-in adds an `APPLICATION_TIME` period over the specified "`validfrom`" and "`validto`" columns of a column-store table, which adds an implicit constraint "`validfrom < validto`". After adding the time period to the table, temporal features such as `UPDATE FOR PORTION OF` are enabled.

> ### Tip:  
> For more information about application-time period tables, see the SAP HANA SQL Reference Guide, in *Related Information* below, and in particular the section describing the <code><i class="varname">&lt;application_time_period_configuration&gt;</i></code> in *CREATE TABLE Statement \(Data Definition\)*, as indicated in *Related Information* below, where you can also find a link to information about the HDI plug-in for system version tables.



<a name="loio73c7b80318ba4405a8769e6ceb41ec64__section_iz3_s5c_bhb"/>

## Example Artifact Code

The following code shows a simple example of an application time-period table definition for HDI:

> ### Code Syntax:  
> `/src/CUSTOMERS.hdbapplicationtime`
> 
> ```sql
> APPLICATION TIME "CUSTOMERS"(validfrom, validto) 
> ```



<a name="loio73c7b80318ba4405a8769e6ceb41ec64__section_u4d_pth_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbapplicationtime" : {
>    "plugin_name" : "com.sap.hana.di.applicationtime"
> }
> ```

**Related Information**  


[CREATE TABLE Statement \(SAP HANA Cloud SQL Reference Guide\)](https://help.sap.com/viewer/c1d3f60099654ecfb3fe36ac93c121bb/cloud/en-US/20d58a5f75191014b2fe92141b7df228.html)

[System Versioning Tables \(.hdbsystemversioning\)](system-versioning-tables-hdbsystemversioning-5794b34.md "Transforms a design-time, system-versioned table that refers to a current and history table into a system-versioned table database object.")

[Application-Time Period Tables \(SAP HANA Cloud, SAP HANA Database Administration Guide\)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/latest/en-US/2e37d6a82f7b48ccbfcc5a1a6ce490f5.html)

