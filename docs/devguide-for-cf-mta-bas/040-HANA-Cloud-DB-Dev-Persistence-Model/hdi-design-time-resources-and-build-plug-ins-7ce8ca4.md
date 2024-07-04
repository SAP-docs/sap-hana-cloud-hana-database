<!-- loio7ce8ca4a12d54f7a91d8daaad909126b -->

# HDI Design-Time Resources and Build Plug-ins

Database design-time resources must be mapped to a build plug-in for deployment purposes.



In the SAP HANA deployment infrastructure \(HDI\), design-time artifacts are distinguished by means of a unique file suffix that must be mapped to an HDI build plug-in. The following example of an abbreviated HDI configuration file \(`.hdiconfig`\) file illustrates how the design-time artifact types `.hdbcalculationview` and `.hdbtable` are mapped to their corresponding HDI build plug-in:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbtable" : {
>    "plugin_name" : "com.sap.hana.di.table", 
>    "plugin_version": "4.0.0.0" 
> },
> "hdbview" : {
>    "plugin_name" : "com.sap.hana.di.view", 
>    "plugin_version": "4.0.0.0" 
> },
> "hdbcalculationview" : {
>    "plugin_name" : "com.sap.hana.di.calculationview", 
>    "plugin_version": "4.0.0.0" 
> }
> ```

The following table lists in alphabetical order the design-time artifacts you can develop and deploy with the SAP HANA Deployment Infrastructure \(HDI\) and describes the artifact's scope. The table also indicates which build plug-in is required to ensure successful deployment of the artifact. For more information about the individual artifact types and the configuration of the corresponding build plug-in, see *Related Information* below.

**Mappings Default File-Suffix to HDI Build Plug-ins**


<table>
<tr>
<th valign="top">

Artifact Suffix

</th>
<th valign="top">

Description/Content

</th>
<th valign="top">

Build Plug-in

</th>
</tr>
<tr>
<td valign="top">

`csv` 

</td>
<td valign="top">

Source data for a table-import operation \(also `hdbtabledata`\)

</td>
<td valign="top">

`com.sap.hana.di.tabledata.source` 

</td>
</tr>
<tr>
<td valign="top">

`.? (txt, copy only)` 

</td>
<td valign="top">

An arbitrary design-time resource

</td>
<td valign="top">

`com.sap.hana.di.copyonly` 

</td>
</tr>
<tr>
<td valign="top">

`hdbapplicationtime` 

</td>
<td valign="top">

Transforms a design-time application time-period table into a database table object with application-time period

</td>
<td valign="top">

`com.sap.hana.di.applicationtime` 

</td>
</tr>
<tr>
<td valign="top">

`hdbanalyticprivilege` 

</td>
<td valign="top">

Definition of an XML-based analytic privilege

</td>
<td valign="top">

`com.sap.hana.di.analyticprivilege` 

</td>
</tr>
<tr>
<td valign="top">

`hdbcalculationview` 

</td>
<td valign="top">

Definition of a calculation view

</td>
<td valign="top">

`com.sap.hana.di.calculationview` 

</td>
</tr>
<tr>
<td valign="top">

`hdbconstraint` 

</td>
<td valign="top">

Transforms a design-time constraint into a constraint on database tables

</td>
<td valign="top">

`com.sap.hana.di.constraint` 

</td>
</tr>
<tr>
<td valign="top">

`hdbcollection` 

</td>
<td valign="top">

Transforms a design-time document-collection resource into a collection database object

</td>
<td valign="top">

`com.sap.hana.di.collection` 

</td>
</tr>
<tr>
<td valign="top">

`hdbcollectionindex` 

</td>
<td valign="top">

Transforms a design-time resource for a document collection index into a collection-index database object

</td>
<td valign="top">

`com.sap.hana.di.collection.index` 

</td>
</tr>
<tr>
<td valign="top">

`hdbeshconfig` 

</td>
<td valign="top">

Creates and deploys a search configuration with the SAP HANA database's deployment infrastructure \(HDI\)

</td>
<td valign="top">

`com.sap.hana.di.eshconfig` 

</td>
</tr>
<tr>
<td valign="top">

`hdbfabricvirtualtable` 

</td>
<td valign="top">

Adds a system-owned replica to a virtual table from a fabric virtual table

</td>
<td valign="top">

`com.sap.hana.di.sharedreplica` 

</td>
</tr>
<tr>
<td valign="top">

`hdbdropcreatetable` 

</td>
<td valign="top">

Transforms a design-time table resource into a table database object

</td>
<td valign="top">

`com.sap.hana.di.dropcreatetable` 

</td>
</tr>
<tr>
<td valign="top">

`hdbflowgraph` 

</td>
<td valign="top">

Transforms a design-time flow-graph description into a corresponding set of database procedure or task objects

</td>
<td valign="top">

`com.sap.hana.di.flowgraph` 

</td>
</tr>
<tr>
<td valign="top">

`hdbfunction` 

</td>
<td valign="top">

Database function definition

</td>
<td valign="top">

`com.sap.hana.di.function` 

</td>
</tr>
<tr>
<td valign="top">

`hdbgraphworkspace` 

</td>
<td valign="top">

Definition of a graph work space resource

</td>
<td valign="top">

`com.sap.hana.di.graphworkspace` 

</td>
</tr>
<tr>
<td valign="top">

`hdbindex` 

</td>
<td valign="top">

Table index definition

</td>
<td valign="top">

`com.sap.hana.di.index` 

</td>
</tr>
<tr>
<td valign="top">

`jar` 

</td>
<td valign="top">

Optional mapping, if you want direct access to Hadoop files

</td>
<td valign="top">

`com.sap.hana.di.virtualfunctionpackage.hadoop` 

</td>
</tr>
<tr>
<td valign="top">

`hdblibrary` 

</td>
<td valign="top">

A design-time library resource

</td>
<td valign="top">

`com.sap.hana.di.library` 

</td>
</tr>
<tr>
<td valign="top">

`hdblogicalschema` 

</td>
<td valign="top">

Transforms a design-time logical-schema definition into database objects that can be consumed by synonyms etc.

</td>
<td valign="top">

`com.sap.hana.di.logicalschema` 

</td>
</tr>
<tr>
<td valign="top">

`hdbmigrationtable` 

</td>
<td valign="top">

Transforms a design-time table resource into a table database object

</td>
<td valign="top">

`com.sap.hana.di.table.migration` 

</td>
</tr>
<tr>
<td valign="top">

`hdbprocedure` 

</td>
<td valign="top">

Definition of a database procedure

</td>
<td valign="top">

`com.sap.hana.di.procedure` 

</td>
</tr>
<tr>
<td valign="top">

`hdbprojectionview` 

</td>
<td valign="top">

Definition of a projection view

</td>
<td valign="top">

`com.sap.hana.di.projectionview` 

</td>
</tr>
<tr>
<td valign="top">

`hdbprojectionviewconfig` 

</td>
<td valign="top">

Configuration file for a projection view

</td>
<td valign="top">

`com.sap.hana.di.projectionview.config` 

</td>
</tr>
<tr>
<td valign="top">

`hdbpublicsynonym` 

</td>
<td valign="top">

Definition of a public database synonym

</td>
<td valign="top">

`com.sap.hana.di.publicsynonym` 

</td>
</tr>
<tr>
<td valign="top">

`hdbremotetablereplica` 

</td>
<td valign="top">

Transforms a design-time remote-table replication that refers to a current virtual table into a remote-table-replication database object

</td>
<td valign="top">

`com.sap.hana.di.remotetablereplica` 

</td>
</tr>
<tr>
<td valign="top">

`hdbreptask` 

</td>
<td valign="top">

Transform a design-time replication task description into a corresponding set of database procedure or task operations

</td>
<td valign="top">

`com.sap.hana.di.reptask` 

</td>
</tr>
<tr>
<td valign="top">

`hdbresultcache` 

</td>
<td valign="top">

Definition of a result cache

</td>
<td valign="top">

`com.sap.hana.di.resultcache` 

</td>
</tr>
<tr>
<td valign="top">

`hdbrole` 

</td>
<td valign="top">

Definition of a database roles

</td>
<td valign="top">

`com.sap.hana.di.role` 

</td>
</tr>
<tr>
<td valign="top">

`hdbroleconfig` 

</td>
<td valign="top">

Configuration of database privileges \(and other roles\) to be included in a database role

</td>
<td valign="top">

`com.sap.hana.di.roleconfig` 

</td>
</tr>
<tr>
<td valign="top">

`hdbschedulerjob` 

</td>
<td valign="top">

Transforms a design-time scheduler-job resource into a scheduler job on a database procedure.

</td>
<td valign="top">

`com.sap.hana.di.schedulerjob` 

</td>
</tr>
<tr>
<td valign="top">

`hdbsearchruleset` 

</td>
<td valign="top">

Definition of search configurations for built-in search procedure

</td>
<td valign="top">

`com.sap.hana.di.searchruleset` 

</td>
</tr>
<tr>
<td valign="top">

`hdbsequence` 

</td>
<td valign="top">

Definition of a database sequence

</td>
<td valign="top">

`com.sap.hana.di.sequence` 

</td>
</tr>
<tr>
<td valign="top">

`hdbstatistics` 

</td>
<td valign="top">

Statistics definition file

</td>
<td valign="top">

`com.sap.hana.di.statistics` 

</td>
</tr>
<tr>
<td valign="top">

`hdbstructuredprivilege` 

</td>
<td valign="top">

Definition of analytic or structured privileges

</td>
<td valign="top">

`com.sap.hana.di.structuredprivilege` 

</td>
</tr>
<tr>
<td valign="top">

`hdbsynonym` 

</td>
<td valign="top">

Database synonym definition

</td>
<td valign="top">

`com.sap.hana.di.synonym` 

</td>
</tr>
<tr>
<td valign="top">

`hdbsynonymconfig` 

</td>
<td valign="top">

Configuration file for a database synonym

</td>
<td valign="top">

`com.sap.hana.di.synonym.config` 

</td>
</tr>
<tr>
<td valign="top">

`hdbsystemversioning` 

</td>
<td valign="top">

Transforms a design-time, system-versioned table that refers to a current and history table into a system-versioned table database object

</td>
<td valign="top">

`com.sap.hana.di.systemversioning` 

</td>
</tr>
<tr>
<td valign="top">

`hdbtable` 

</td>
<td valign="top">

Table operations

</td>
<td valign="top">

`com.sap.hana.di.table` 

</td>
</tr>
<tr>
<td valign="top">

`hdbtabledata` 

</td>
<td valign="top">

Definition of a data-import operation for a database table \(also `csv`\)

</td>
<td valign="top">

`com.sap.hana.di.tabledata` 

</td>
</tr>
<tr>
<td valign="top">

`hdbtabletype` 

</td>
<td valign="top">

Definition of a table type

</td>
<td valign="top">

`com.sap.hana.di.tabletype` 

</td>
</tr>
<tr>
<td valign="top">

`hdbtrigger` 

</td>
<td valign="top">

Database trigger definition

</td>
<td valign="top">

`com.sap.hana.di.trigger` 

</td>
</tr>
<tr>
<td valign="top">

`hdbview` 

</td>
<td valign="top">

View definition file

</td>
<td valign="top">

`com.sap.hana.di.view` 

</td>
</tr>
<tr>
<td valign="top">

`hdbvirtualtable` 

</td>
<td valign="top">

Definition of a virtual table

</td>
<td valign="top">

`com.sap.hana.di.virtualtable` 

</td>
</tr>
<tr>
<td valign="top">

`hdbvirtualtableconfig` 

</td>
<td valign="top">

Virtual table configuration file

</td>
<td valign="top">

`com.sap.hana.di.virtualtable.config` 

</td>
</tr>
<tr>
<td valign="top">

`properties`

`tags`

</td>
<td valign="top">

Properties file for a table-import operation

</td>
<td valign="top">

`com.sap.hana.di.tabledata.properties` 

</td>
</tr>
</table>

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2024_3_QRC/en-US/9789224788a34d93a86080cab993575c.html "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.") :arrow_upper_right:

[The SAP HDI Container Configuration File](the-sap-hdi-container-configuration-file-6400400.md "Bind design-time file types to the corresponding build plug-in required in the SAP HANA Deployment Infrastructure (HDI).")

[SAP HDI Container Configuration File Syntax](sap-hdi-container-configuration-file-syntax-c1df57a.md "In SAP HANA Deployment Infrastructure (HDI), the JSON syntax is used to format the content of the HDI container-configuration file (.hdiconfig).")

[Creating Data Persistence Artifacts with SQL DDL](creating-data-persistence-artifacts-with-sql-ddl-a216fd8.md "You can use SQL DDL to define the underlying database objects that store and provide data for your application, for example, tables and views.")

