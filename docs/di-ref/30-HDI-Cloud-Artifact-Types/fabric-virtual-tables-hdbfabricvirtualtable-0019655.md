<!-- loio001965588c394dadb02ee999c0d0cda7 -->

# Fabric Virtual Tables \(.hdbfabricvirtualtable\)

Adds a system-owned replica to a virtual table from a fabric virtual table.



The build plug-in for fabric virtual tables \(`.hdbfabricvirtualtable`\) adds a system-owned replica to a virtual table from a design-time fabric virtual table. The file format required for the `hdbfabricvirtualtable` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL command.

> ### Tip:  
> For more information about adding system-owned replicas to virtual tables and toggling between virtual and replica tables, see *Related Information* below.



## Example Artifact Code

The following code shows a simple example of a design-time definition of a shared replica for SAP HANA Deployment Infrastructure \(HDI\):

> ### Code Syntax:  
> `/src/FVT.hdbfabricvirtualtable`
> 
> ```sql
> SHARED [SNAPSHOT] REPLICA [PAGE|COLUMN LOADABLE] ON <virtual_table_name>
> ```

The virtual table must already exist in the HDI container. For more information about virtual tables, see *Related Information* below.



## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbfabricvirtualtable" : {
>    "plugin_name" : "com.sap.hana.di.sharedreplica"
>    "plugin_version": "4.0.0.0" 
> }
> ```

**Related Information**  


[Add a System-Owned Replica to a Virtual Table \(SAP HANA Cloud, SAP HANA Database Data Access Guide\)](https://help.sap.com/docs/hana-cloud-database/b6c0184b46cc424b9bcce8e6aae02f97/c15dd3de0e3c47b8912cb9376ef09de6.html)

[Toggling Between Virtual Tables and Replica Tables \(SAP HANA Cloud, SAP HANA Database Data Access Guide\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/b6c0184b46cc424b9bcce8e6aae02f97/f439a3c189674d82b9276c41b7a2e6ab.html)

[Virtual Tables \(.hdbvirtualtable and .hdbvirtualtableconfig\)](virtual-tables-hdbvirtualtable-and-hdbvirtualtableconfig-0819114.md "Transform a design-time virtual table resource into a virtual table database object.")

