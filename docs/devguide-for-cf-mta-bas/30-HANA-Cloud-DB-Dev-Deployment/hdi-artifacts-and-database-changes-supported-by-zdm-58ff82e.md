<!-- loio58ff82ec9aff4318ada8967dd6d76bea -->

# HDI Artifacts and Database Changes Supported by ZDM

Zero-downtime maintenance \(ZDM\) supports the HDI artifacts and database changes listed in this topic.



If you are updating a multitarget application using blue-green deployment in a zero-downtime-maintenance scenario, bear in mind the information included here about the possible impact the deployment can have on the HDI artifacts included in the application to be redeployed and any database changes required.



## Supported database Changes in ZDM

The following database changes are supported during zero-downtime maintenance of multitarget applications in SAP HANA Cloud:

-   Modifications in the analytics layer \(calculation views\)
-   Modifications of business logic \(SQLScript procedures, table functions\)
-   Modifications in database abstraction Layer \(database views\)
-   Modifications in the data model that do not require data transformation or migration, for example:
    -   Adding or removing tables
    -   Adding nullable table columns \(without the `NOT NULL` constraint\)
    -   Adding table columns with default value \(with the `DEFAULT` constraint\)
    -   Extending the length of text table columns




<a name="loio58ff82ec9aff4318ada8967dd6d76bea__section_lsb_jz4_fdb"/>

## Supported Database Artifacts in ZDM

The table *Supported HDI Artifacts* below contains a description of the modeling of the supported HDI artifacts and the target schema where they should be deployed during the upgrade of a multitarget application using zero-downtime maintenance.

The default target schema \(data/access\) is the target schema in which the artifact should be deployed most frequently \(by default\). The artifact is located in the default folder \(`src/`, `cfg/`\) of the `db` module, not into `data/` or `access/` folder and HDI Deployer applies default handling to the artifact.

<a name="loio58ff82ec9aff4318ada8967dd6d76bea__table_l44_2bj_fdb"/>Supported HDI Artifacts


<table>
<tr>
<th valign="top">

HDI Artifact Type



</th>
<th valign="top">

Default target schema \(data/access\)



</th>
<th valign="top">

Adoption guidelines



</th>
</tr>
<tr>
<td valign="top">

 `.hdbanalyticprivilege` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbapplicationtime` 



</td>
<td valign="top">

data



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbcalculationview` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbconstraint` 



</td>
<td valign="top">

data



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbflowgraph` 



</td>
<td valign="top">

access



</td>
<td valign="top">

1.  Replication tasks \(`.hdbreptask`\) and flowgraphs \(`.hdbflowgraph`\) should replicate into tables from the `data/` folder.

2.  Put replication tasks \(`.hdbreptask`\) and flowgraphs \(`.hdbflowgraph`\) into the `access/` folder, and make sure that they are not active from new and old version at the same time.




</td>
</tr>
<tr>
<td valign="top">

 `.hdbfunction` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbgraphworkspace` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.jar` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbindex` 



</td>
<td valign="top">

data



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdblibrary` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdblogicalschema` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbmigrationtable` 



</td>
<td valign="top">

data



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbprocedure` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbprojectionview` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbprojectionviewconfig` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbpublicsynonym` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbreptask` 



</td>
<td valign="top">

access



</td>
<td valign="top">

See `.hdbflowgraph.` 



</td>
</tr>
<tr>
<td valign="top">

 `.hdbresultcache` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbrole` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbroleconfig` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbsearchruleset` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbsequence` 



</td>
<td valign="top">

data



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbview` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbstatistics` 



</td>
<td valign="top">

data



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbstructuredprivilege` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbsynonym` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbsynonymconfig` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbsystemversioning` 



</td>
<td valign="top">

data



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbtable` 



</td>
<td valign="top">

data



</td>
<td valign="top">

1.  Tables \(`hdbtable`\) are usually put into the `data/` folder. In certain situations, it is valid to put them into the `access/` folder, for example, if there are corresponding `hdbtabledata` files that fill these tables with language texts that is different or incompatible between versions.

    Put CDS entities in the `data/` folder.

    > ### Caution:  
    > If you put CDS entities in the `access` schema, this would create projection views.

2.  Do not model associations for tables \(`hdbtable`\). Associations are not visible in the `access` schema because they are not exposed through the generated projection views. Do not point to objects in the `access` schema.

3.  Table name and column names should be enclosed in quotes, for example, \(`"column_name"`\).




</td>
</tr>
<tr>
<td valign="top">

 `.hdbdropcreatetable` 



</td>
<td valign="top">

data



</td>
<td valign="top">

1.  Put `hdbdropcreatetable` temporary tables into the `access/` folder because they are related to application logic \(for example, `procedures`\).

2.  If `hdbdropcreatetable` temporary tables are put into the `data/` folder, they will be deployed there but cannot be used. There is no projection view created for them in the `access` schema.




</td>
</tr>
<tr>
<td valign="top">

 `hdbtabledata` 



</td>
<td valign="top">

data



</td>
<td valign="top">

`hdbtabledata` files with language texts for calculation views must be put into the `access/` folder. If they are put into the `data/` folder, they do not do any harm, but cannot be used.



</td>
</tr>
<tr>
<td valign="top">

 `.csv` 



</td>
<td valign="top">

data



</td>
<td valign="top">

See `.hdbtabledata`.



</td>
</tr>
<tr>
<td valign="top">

 `.properties` 



</td>
<td valign="top">

data



</td>
<td valign="top">

See `.hdbtabledata`.



</td>
</tr>
<tr>
<td valign="top">

 `.tags` 



</td>
<td valign="top">

data



</td>
<td valign="top">

See `.hdbtabledata`.



</td>
</tr>
<tr>
<td valign="top">

 `.hdbtabletype` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbtrigger` 



</td>
<td valign="top">

access



</td>
<td valign="top">

Backwardly incompatible changes in triggers are not supported. Version 2 of the application has to be in read-only mode, which is not supported.



</td>
</tr>
<tr>
<td valign="top">

 `.hdbvirtualfunction` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbvirtualfunctionconfig` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbvirtualprocedure` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbvirtualprocedureconfig` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbvirtualtable` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbvirtualtableconfig` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.txt` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdiconfig` 



</td>
<td valign="top">

data and access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdinamespace` 



</td>
<td valign="top">

data and access



</td>
<td valign="top">

\-



</td>
</tr>
<tr>
<td valign="top">

 `.hdbgrants` 



</td>
<td valign="top">

access



</td>
<td valign="top">

\-



</td>
</tr>
</table>

**Related Information**  


[Deploy a Multitarget Application with Zero-Downtime Maintenance](deploy-a-multitarget-application-with-zero-downtime-maintenance-f33557b.md "Update an application that has database changes without any downtime.")

[Zero-Downtime Maintenance with Multitarget Applications](zero-downtime-maintenance-with-multitarget-applications-a7afca8.md "The deploy service supports application updates using zero-downtime maintenance (ZDM).")

