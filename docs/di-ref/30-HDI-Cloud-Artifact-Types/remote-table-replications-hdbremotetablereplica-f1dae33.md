<!-- loiof1dae33e88d54a7aa079cf6ba3ef5665 -->

# Remote Table Replications \(.hdbremotetablereplica\)

Transforms a design-time remote-table replication that refers to a current virtual table into a remote-table-replication database object.



HDI remote-table replication is designed for use with the the SAP HANA Smart Data Access \(SDA\) adapter "`hanaodbc`". For this reason, HDI remote-table replication does not work with the SAP HANA Smart Data Integration \(SDI\) "`HanaAdapter`". The file format uses a custom syntax that is parsed by the `hdbremotetablereplica` build plug-in.

> ### Tip:  
> For more information about remote-table replication and remote sources, see *Replicating Tables from Remote Sources* in the *SAP HANA Cloud, SAP HANA Database Access Guide* as indicated in *Related Information* below.



<a name="loiof1dae33e88d54a7aa079cf6ba3ef5665__section_ucf_rbw_byb"/>

## Example Artifact Code

The following code shows a simple example of a design-time definition of a remote table replication for SAP HDI:

> ### Code Syntax:  
> `/src/rtr.hdbremotetablereplica`
> 
> ```xml
> REMOTE TABLE REPLICA "TARGET_TABLE" ON "VIRTUAL_TABLE" 
> ```

The `"TARGET_TABLE"` and the `"VIRTUAL_TABLE"` are in the same HDI container. The target table is the new replication table created by the build plug-in, and the virtual table must already exist in the container. For more information about virtual tables, see *Related Information* below.



<a name="loiof1dae33e88d54a7aa079cf6ba3ef5665__section_lxd_sbw_byb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbremotetablereplica" : {
>    "plugin_name"   : "com.sap.hana.di.remotetablereplica"
> }
> 
> ```

**Related Information**  


[Replicating Tables from Remote Sources \(SAP HANA Cloud, SAP HANA Database Data Access Guide\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/477aa413a36c4a95878460696fcc8896/2937dc0404e04f91be3aff16ebd7acaa.html)

[Virtual Tables \(.hdbvirtualtable and .hdbvirtualtableconfig\)](virtual-tables-hdbvirtualtable-and-hdbvirtualtableconfig-0819114.md "Transform a design-time virtual table resource into a virtual table database object.")

