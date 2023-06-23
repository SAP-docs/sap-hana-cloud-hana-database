<!-- loiof8618f7e753943b096e1d17da40c1e89 -->

# HDI Artifact Type and Build Plug-ins

The SAP HANA Cloud, design-time database artifact types, for example, tables and views, are mapped to an SAP HDI build plug-in.



The following table lists in alphabetical order the design-time artifacts you can develop and deploy with the SAP HANA Cloud Deployment Infrastructure \(HDI\). For more information about the syntax required for a particular type of design-time artifact and the configuration of the corresponding build plug-in, choose the artifact type in the following table.

Not all plug-in libraries are available by default. The list of plug-in libraries that are available by default in an HDI container must be configured by the HDI Container administrator, as described in *Maintaining HDI Containers* in the *SAP HANA Cloud Deployment Infrastructure \(HDI\) Reference*. For more details, see *Related Information* below.

> ### Note:  
> Some of the HDI plug-ins available for database development in SAP HANA on-premise are not available in SAP HANA Cloud, for example, SAP HANA CDS \(`.hdbcds`\). For more information about which plug-ins are not available for use in SAP HANA Cloud, see *Design-time Content Compatibility* in *Related Information* below.

**HDI Design-Time Artifact Types and Run-Time Plug-Ins**


<table>
<tr>
<th valign="top">

Artifact Type



</th>
<th valign="top">

Artifact Suffix



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

text, copy only



</td>
<td valign="top">

.? \(.txt, …\)



</td>
<td valign="top">

Transform an arbitrary design-time resource into a deployed object



</td>
</tr>
<tr>
<td valign="top">

Analytic Privilege



</td>
<td valign="top">

 `.hdbanalyticprivilege` 



</td>
<td valign="top">

Transform a design-time XML-based analytic-privileges resource into a analytic-privileges object in the database



</td>
</tr>
<tr>
<td valign="top">

Application Time-Period Table



</td>
<td valign="top">

 `.hdbapplicationtime` 



</td>
<td valign="top">

Transform a design-time application time-period table into a database table object with application-time period



</td>
</tr>
<tr>
<td valign="top">

Calculation View



</td>
<td valign="top">

 `.hdbcalculationview` 



</td>
<td valign="top">

Transform a design-time calculation view description into a set of view database objects



</td>
</tr>
<tr>
<td valign="top">

Constraint



</td>
<td valign="top">

 `.hdbconstraint` 



</td>
<td valign="top">

Transform a design-time constraint into a constraint on database tables



</td>
</tr>
<tr>
<td valign="top">

CSV



</td>
<td valign="top">

\-



</td>
<td valign="top">

Source file containing comma-separated values \(CSV\) for data import with `.hdbtabledata` 



</td>
</tr>
<tr>
<td valign="top">

Document Store Collection



</td>
<td valign="top">

 `.hdbcollection` 



</td>
<td valign="top">

Transforms a design-time document-store collection resource into a JSON collection database object



</td>
</tr>
<tr>
<td valign="top">

Document Store Collection Index



</td>
<td valign="top">

 `.hdbcollectionindex` 



</td>
<td valign="top">

Transforms a design-time document-store, collection-index resource into a JSON collection-index database object



</td>
</tr>
<tr>
<td valign="top">

Drop/Create Table



</td>
<td valign="top">

 `.hdbdropcreatetable` 



</td>
<td valign="top">

Transforms a design-time table resource into a table database object. See also `.hdbtable` 



</td>
</tr>
<tr>
<td valign="top">

Flowgraph



</td>
<td valign="top">

 `.hdbflowgraph` 



</td>
<td valign="top">

Transform a design-time flowgraph description into a corresponding set of database procedure or task objects



</td>
</tr>
<tr>
<td valign="top">

Function



</td>
<td valign="top">

 `.hdbfunction` 



</td>
<td valign="top">

Transform a design-time function resource into a function database object



</td>
</tr>
<tr>
<td valign="top">

Graph Workspace



</td>
<td valign="top">

 `.hdbgraphworkspace` 



</td>
<td valign="top">

Transform a design-time graph-workspace resource into a graph-workspace object in the database



</td>
</tr>
<tr>
<td valign="top">

Index



</td>
<td valign="top">

 `.hdbindex` 



</td>
<td valign="top">

Transform a design-time index resource into an index on a database table



</td>
</tr>
<tr>
<td valign="top">

Library



</td>
<td valign="top">

 `.hdblibrary` 



</td>
<td valign="top">

Transform a design-time library resource into a library database object



</td>
</tr>
<tr>
<td valign="top">

Logical Schema



</td>
<td valign="top">

 `.hdblogicalschema` 



</td>
<td valign="top">

Transforms a design-time logical-schema definition into database objects that can be consumed by synonyms and so on.



</td>
</tr>
<tr>
<td valign="top">

Migration Table



</td>
<td valign="top">

 `.hdbmigrationtable` 



</td>
<td valign="top">

Transform a design-time table resource into a table database object for migration purposes



</td>
</tr>
<tr>
<td valign="top">

Procedure



</td>
<td valign="top">

 `.hdbprocedure` 



</td>
<td valign="top">

Transform a design-time procedure resource into a procedure database object



</td>
</tr>
<tr>
<td valign="top">

Projection View



</td>
<td valign="top">

 `.hdbprojectionview` 



</td>
<td valign="top">

Transforms a design-time projection-view definition into a database object



</td>
</tr>
<tr>
<td valign="top">

Projection View Configuration



</td>
<td valign="top">

 `.hdbprojectionviewconfig` 



</td>
<td valign="top">

An explicit configuration of the projection view's target. A projection view configuration file can contain multiple configurations



</td>
</tr>
<tr>
<td valign="top">

\(Table Data\) Properties



</td>
<td valign="top">

 `.properties` 



</td>
<td valign="top">

Insert data from files referenced in the “.properties” file format into database tables which are managed by SAP HANA HDI. See also CSV and Table Data



</td>
</tr>
<tr>
<td valign="top">

Public Synonym



</td>
<td valign="top">

 `.hdbpublicsynonym` 



</td>
<td valign="top">

Create public synonyms that refer to database objects located in the target schema of the current container



</td>
</tr>
<tr>
<td valign="top">

Replication Task



</td>
<td valign="top">

 `.hdbreptask` 



</td>
<td valign="top">

Transform a design-time replication task description into a corresponding set of database procedure or task operations



</td>
</tr>
<tr>
<td valign="top">

Result Cache



</td>
<td valign="top">

 `.hdbresultcache` 



</td>
<td valign="top">

Transform a DDL-based definition of a result cache into the corresponding catalog object



</td>
</tr>
<tr>
<td valign="top">

Role Configuration



</td>
<td valign="top">

 `.hdbrole` 



</td>
<td valign="top">

Transform a design-time role resource into a run-time role object.



</td>
</tr>
<tr>
<td valign="top">

Search Rule Set



</td>
<td valign="top">

 `.hdbsearchruleset` 



</td>
<td valign="top">

Creates search configurations that can be consumed with a built-in database procedure



</td>
</tr>
<tr>
<td valign="top">

Sequence



</td>
<td valign="top">

 `.hdbsequence` 



</td>
<td valign="top">

Transforms a design-time sequence resource into a sequence database object



</td>
</tr>
<tr>
<td valign="top">

SQL View



</td>
<td valign="top">

 `.hdbview` 



</td>
<td valign="top">

Transforms a design-time view resource into an SQL view database object.



</td>
</tr>
<tr>
<td valign="top">

Statistics



</td>
<td valign="top">

 `.hdbstatistics` 



</td>
<td valign="top">

Transforms a design-time statistics resource into a statistics object on a database table.



</td>
</tr>
<tr>
<td valign="top">

Structured Privilege



</td>
<td valign="top">

 `.hdbstructuredprivilege` 



</td>
<td valign="top">

Transforms a design-time DDL-based structured privilege resource into a structured privilege object



</td>
</tr>
<tr>
<td valign="top">

Synonym



</td>
<td valign="top">

 `.hdbsynonym` 



</td>
<td valign="top">

Transforms a design-time synonym definition into a database synonym object.



</td>
</tr>
<tr>
<td valign="top">

Synonym Configuration



</td>
<td valign="top">

 `.hdbsynonymconfig` 



</td>
<td valign="top">

An explicit \(but optional\) configuration of the synonym’s target; the configuration can also be included in the synonym definition \(.`hdbsynonym`\).



</td>
</tr>
<tr>
<td valign="top">

System Version Table



</td>
<td valign="top">

 `.hdbsystemversioning` 



</td>
<td valign="top">

Transforms a design-time, system-versioned table that refers to a current and history table into a system-versioned table database object



</td>
</tr>
<tr>
<td valign="top">

Table



</td>
<td valign="top">

 `.hdbtable` 



</td>
<td valign="top">

Transforms a design-time table resource into a table database object. See also `dropcreatetable`.



</td>
</tr>
<tr>
<td valign="top">

Table Data



</td>
<td valign="top">

 `.hdbtabledata` 



</td>
<td valign="top">

Insert data from other files \(for example, CSV, `.properties`, or `.tags` files\) into database tables.



</td>
</tr>
<tr>
<td valign="top">

Table Data Properties



</td>
<td valign="top">

 `.properties` 



</td>
<td valign="top">

Insert data from files referenced in the “.properties” file format into database tables which are managed by SAP HANA HDI. See also `.hdbtabledata` and `.tags`.



</td>
</tr>
<tr>
<td valign="top">

Table Type



</td>
<td valign="top">

 `.hdbtabletype` 



</td>
<td valign="top">

Transforms a design-time table type resource into a table type database object.



</td>
</tr>
<tr>
<td valign="top">

Tags



</td>
<td valign="top">

 `.tags` 



</td>
<td valign="top">

Insert data from other files \(for example, CSV, `.properties`, or `.tags` files\) into database tables.



</td>
</tr>
<tr>
<td valign="top">

Trigger



</td>
<td valign="top">

 `.hdbtrigger` 



</td>
<td valign="top">

Transforms a design-time trigger resource into a trigger on a database table.



</td>
</tr>
<tr>
<td valign="top">

View



</td>
<td valign="top">

 `.hdbview` 



</td>
<td valign="top">

Transforms a design-time view resource into an SQL view database object.



</td>
</tr>
<tr>
<td valign="top">

Virtual Function



</td>
<td valign="top">

 `.hdbvirtualfunction` 



</td>
<td valign="top" rowspan="2">

Transform a design-time virtual function resource into a virtual function database object



</td>
</tr>
<tr>
<td valign="top">

Virtual Function Configuration



</td>
<td valign="top">

 `.hdbvirtualfunctionconfig` 



</td>
</tr>
<tr>
<td valign="top">

Virtual Package



</td>
<td valign="top">

 `.hdbvirtualpackage` 



</td>
<td valign="top">

Transform a design-time Hadoop Map Reduce Job \(`.hdbvirtualpackagehadoop`\) or SparkSQL resource \(`.hdbvirtualpackagesparksql`\) into a virtual-package database object



</td>
</tr>
<tr>
<td valign="top">

Virtual Procedure



</td>
<td valign="top">

 `.hdbvirtualprocedure` 



</td>
<td valign="top" rowspan="2">

Transform a design-time virtual-procedure resource into a virtual-procedure database object



</td>
</tr>
<tr>
<td valign="top">

Virtual Procedure Configuration



</td>
<td valign="top">

 `.hdbvirtualprocedureconfig` 



</td>
</tr>
<tr>
<td valign="top">

Virtual Table



</td>
<td valign="top">

 `.hdbvirtualtable` 



</td>
<td valign="top" rowspan="2">

Transform a design-time virtual table resource into a virtual table database object



</td>
</tr>
<tr>
<td valign="top">

Virtual Table Configuration



</td>
<td valign="top">

 `.hdbvirtualtableconfig` 



</td>
</tr>
</table>

> ### Note:  
> \*\* CSV: Comma-separated-values file

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_2_QRC/en-US/9789224788a34d93a86080cab993575c.html "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.") :arrow_upper_right:

[SAP HANA Cloud, SAP HANA Database Deployment Infrastructure Reference](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_2_QRC/en-US/4077972509f5437c85d6a03e01509417.html "Set up and maintain the deployment infrastructure for the SAP HANA Cloud, SAP HANA database service.") :arrow_upper_right:

[Design-time Content Compatibility \(SAP HANA Cloud Migration Guide\)](https://help.sap.com/viewer/3c53bc7b58934a9795b6dd8c7e28cf05/hanacloud/en-US/9c8656d9c1a34c829fab426cb77b4639.html)

