<!-- loio9789224788a34d93a86080cab993575c -->

# SAP HDI Artifact Types and Build Plug-ins Reference

The SAP HANA Cloud, SAP HANA database deployment infrastructure \(HDI\) supports a wide variety of database artifact types, for example, tables, indexes, and views.



In SAP HDI, design-time artifacts are distinguished by means of a unique file suffix that must be mapped to a corresponding build plug-in to enable deployment to an HDI container. The following example of an abbreviated HDI configuration file \(`.hdiconfig`\) illustrates how the design-time artifact types `.hdbsynonym`, `.hdbview`, `.hdbcalculationview`, and `.hdbprocedure` are mapped to their corresponding HDI build plug-in:

> ### Code Syntax:  
> The HDI Container Configuration File \(`.hdiconfig`\)
> 
> ```json
> {
>   "minimum_feature_version": 1000,  // optional
>   "file_suffixes" : {
>     "hdbsynonym" : { 
>       "plugin_name" : "com.sap.hana.di.synonym"},
>     "hdbview" : { 
>       "plugin_name" : "com.sap.hana.di.view"}, 
>     "hdbcalculationview" : { 
>       "plugin_name" : "com.sap.hana.di.calculationview"},
>     "hdbprocedure" : { 
>       "plugin_name" : "com.sap.hana.di.procedure"},
>     "<file suffix 2>" : {
>       "plugin_name"   : "com.sap.hana.di.<plugin name>"
>    }
> }
> ```

> ### Restriction:  
> All “hdi\*” file-suffixes \(for example, “`.hdiconfig`” or “`.hdinamespace`”\) are reserved by the SAP HANA Deployment Infrastructure \(HDI\) and cannot be \(re\)configured.



<a name="loio9789224788a34d93a86080cab993575c__section_vnz_glc_yfb"/>

## HDI Minimum Feature Version

For Cloud versions of HANA DI \(HDI\) build plug-ins, the minimum-feature version is optional. As illustrated in the example above, you can use the global `"minimum_feature_version"` parameter, if you want to specify that an application requires a certain minimum version of a feature. This is useful if you know that a particular feature version includes required updates or an important bug fix.

The value of `"minimum_feature_version"` is a number that indicates the minimum feature version of SAP HDI on the SAP HANA Cloud database that will be required for the design-time artifacts. The value defaults to `1000` and does not need to be set unless required.

To display the current HDI feature version of an SAP HANA Cloud database, use the following SQL statement:

```
SELECT FEATURE_VERSION FROM M_FEATURES WHERE COMPONENT_NAME = 'DI' AND FEATURE_NAME = 'VERSION';
```



<a name="loio9789224788a34d93a86080cab993575c__section_own_dlc_yfb"/>

## HDI Plug-in Types

The following table lists in alphabetical order the design-time artifacts you can develop and deploy with the SAP HANA Deployment Infrastructure \(HDI\). For more information about the syntax required for a particular type of design-time artifact and the configuration of the corresponding build plug-in, choose the artifact type in the following table.

> ### Note:  
> Some plug-in libraries are not available by default, for example, for public synonyms. The list of plug-in libraries that are available by default in an HDI container must be configured by the HDI Container administrator, as described in *Maintaining HDI Containers*. For more information, see *Related Information* below.

**Design-Time HDI Artifact Types**


<table>
<tr>
<th valign="top">

A - L

</th>
<th valign="top">

M - S

</th>
<th valign="top">

S - Z

</th>
</tr>
<tr>
<td valign="top">

[CSV](table-data-hdbtabledata-35c4dd8.md) \*

</td>
<td valign="top">

[Migration Table](migration-tables-hdbmigrationtable-52d1f5a.md) 

</td>
<td valign="top">

[System Versioning Table](system-versioning-tables-hdbsystemversioning-5794b34.md) 

</td>
</tr>
<tr>
<td valign="top">

[.? \(txt, copy only\)](copy-only-txt-64459f1.md) 

</td>
<td valign="top">

[Procedure](procedures-hdbprocedure-93de88b.md) 

</td>
<td valign="top">

[Scheduler Job](scheduler-jobs-hdbschedulerjob-f92e31d.md) 

</td>
</tr>
<tr>
<td valign="top">

[Analytic Privilege](analytic-privileges-hdbanalyticprivilege-2d30563.md) 

</td>
<td valign="top">

[Projection View](projection-views-hdbprojectionview-and-hdbprojectionviewconfig-d8a3392.md) 

</td>
<td valign="top">

[Table](tables-hdbtable-and-hdbdropcreatetable-453d48e.md) 

</td>
</tr>
<tr>
<td valign="top">

[App. Time-Period Table](application-time-period-tables-hdbapplicationtime-73c7b80.md) 

</td>
<td valign="top">

[Projection View Configuration](projection-views-hdbprojectionview-and-hdbprojectionviewconfig-d8a3392.md) 

</td>
<td valign="top">

[Table Data](table-data-hdbtabledata-35c4dd8.md) 

</td>
</tr>
<tr>
<td valign="top">

[Calculation View](calculation-views-hdbcalculationview-3db2a35.md) 

</td>
<td valign="top">

[Public Synonym](public-synonyms-hdbpublicsynonym-d131415.md) 

</td>
<td valign="top">

[Table Data Properties](table-data-properties-properties-f4da218.md) 

</td>
</tr>
<tr>
<td valign="top">

[Constraint](constraints-hdbconstraint-bda5470.md) 

</td>
<td valign="top">

[Remote Table Replications](remote-table-replications-hdbremotetablereplica-f1dae33.md) 

</td>
<td valign="top">

[Table Data Tags](table-data-properties-properties-f4da218.md) 

</td>
</tr>
<tr>
<td valign="top">

[Document Store Collection](document-store-collections-hdbcollection-fe16b63.md) 

</td>
<td valign="top">

[Replication Task](replication-tasks-hdbreptask-0194ba9.md) 

</td>
<td valign="top">

[Table Type](table-types-hdbtabletype-83275bd.md) 

</td>
</tr>
<tr>
<td valign="top">

[Document Store Collection Index](document-store-collection-indexes-hdbcollectionindex-b4b1b5c.md) 

</td>
<td valign="top">

[Result Cache](result-caches-hdbresultcache-a3e2b70.md) 

</td>
<td valign="top">

[Trigger](triggers-hdbtrigger-bbd06f5.md) 

</td>
</tr>
<tr>
<td valign="top">

[Drop/Create Table](tables-hdbtable-and-hdbdropcreatetable-453d48e.md) 

</td>
<td valign="top">

[Role](roles-hdbrole-and-hdbroleconfig-625d773.md) 

</td>
<td valign="top">

[View](sql-views-hdbview-2bf9a6f.md) 

</td>
</tr>
<tr>
<td valign="top">

[Enterprise Search Configuration](enterprise-search-configurations-hdbeshconfig-eb019bb.md) 

</td>
<td valign="top">

[Role Configuration](roles-hdbrole-and-hdbroleconfig-625d773.md) 

</td>
<td valign="top">

[Virtual Table](virtual-tables-hdbvirtualtable-and-hdbvirtualtableconfig-0819114.md) 

</td>
</tr>
<tr>
<td valign="top">

[Flowgraph](flowgraphs-hdbflowgraph-6d4fc4a.md) 

</td>
<td valign="top">

[Search Rule Set](search-rule-sets-hdbsearchruleset-e9d52ba.md) 

</td>
<td valign="top">

[Virtual Table Configuration](virtual-tables-hdbvirtualtable-and-hdbvirtualtableconfig-0819114.md) 

</td>
</tr>
<tr>
<td valign="top">

[Function](functions-hdbfunction-cbf1369.md) 

</td>
<td valign="top">

[Sequence](sequences-hdbsequence-b295c2e.md) 

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

[Graph Workspace](graph-workspaces-hdbgraphworkspace-ff89373.md) 

</td>
<td valign="top">

[Synonym](synonyms-hdbsynonym-and-hdbsynonymconfig-aad1653.md) 

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

[Index](indexes-hdbindex-58fdf2d.md) 

</td>
<td valign="top">

[Synonym Configuration](synonyms-hdbsynonym-and-hdbsynonymconfig-aad1653.md) 

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

[Library](libraries-hdblibrary-7475cf4.md) 

</td>
<td valign="top">

[Statistics](statistics-hdbstatistics-435423d.md) 

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

[Logical Schema Definition](logical-schemas-hdblogicalschema-and-hdblogicalschemaconfig-fa9cda8.md) 

</td>
<td valign="top">

[Structured Privilege](structured-privileges-hdbstructuredprivilege-c3827df.md) 

</td>
<td valign="top">

\-

</td>
</tr>
</table>

> ### Note:  
> **\*** CSV: Comma-separated-values file

**Related Information**  


[The SAP HDI Container Configuration File](../20-HDI-Cloud-Content-Development/the-sap-hdi-container-configuration-file-6400400.md "Bind design-time file types to the corresponding build plug-in required in the SAP HANA Deployment Infrastructure (HDI).")

[Run-Time Name Spaces in SAP HDI](../20-HDI-Cloud-Content-Development/run-time-name-spaces-in-sap-hdi-a53bf96.md "SAP HDI defines a strict separation between the naming of run-time objects and the organization of design-time files.")

[Maintaining SAP HDI Containers](../10-HDI-Cloud-Administration/15-HDI-Cloud-Admin-Maintain-Containers/maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

