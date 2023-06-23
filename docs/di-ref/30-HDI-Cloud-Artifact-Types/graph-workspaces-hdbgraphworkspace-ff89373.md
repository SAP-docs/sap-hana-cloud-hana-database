<!-- loioff893731c8514b098223e4a47a6d5f39 -->

# Graph Workspaces \(.hdbgraphworkspace\)

Transform a design-time graph-workspace resource into a graph-workspace object in the database.



The graph workspace plug-in transforms a design-time graph workspace resource \(described in a `.hdbgraphworkspace` artifact\) into a graph workspace object in the database. The file format required for the `.hdbgraphworkspace` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL command `CREATE GRAPH WORKSPACE`, without the leading “`CREATE`”.



<a name="loioff893731c8514b098223e4a47a6d5f39__section_vfc_swh_1hb"/>

## Example Artifact Code

The following code shows a simple example of a design-time graph workspace definition for HDI:

> ### Code Syntax:  
> `/src/my_graph_workspace.hdbgraphworkspace`
> 
> ```sql
> GRAPH WORKSPACE MY_GRAPH_WORKSPACE 
> EDGE TABLE THE_EDGE_TABLE 
>   SOURCE COLUMN SOURCE TARGET COLUMN TARGET KEY COLUMN EDGE_ID 
> VERTEX TABLE THE_VERTEX_TABLE 
>   KEY COLUMN VERTEX_ID
> ```



<a name="loioff893731c8514b098223e4a47a6d5f39__section_ij5_qwh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbgraphworkspace" : {
>    "plugin_name" : "com.sap.hana.di.graphworkspace"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

