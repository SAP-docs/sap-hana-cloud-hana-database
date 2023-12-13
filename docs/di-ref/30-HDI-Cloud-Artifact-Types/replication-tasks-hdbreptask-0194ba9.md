<!-- loio0194ba9e421148dd9712400e449fc61f -->

# Replication Tasks \(.hdbreptask\)

Transform a design-time replication task description into a corresponding set of database procedure or task operations.



A replication task retrieves data from one or more objects in a single remote source and populates one or more tables in SAP HANA.

> ### Tip:  
> For more information about creating `.hdbreptask` artifacts, see the *Modeling Guide for SAP HANA Smart Data Integration and SAP HANA Smart Data Quality* in *Related Information* below.

The file format uses an XML-based syntax.



<a name="loio0194ba9e421148dd9712400e449fc61f__section_oz1_jyh_1hb"/>

## Example Artifact Code

The following code shows a simple example of a design-time definition of a replication-task for HDI:

> ### Code Syntax:  
> `/src/A.hdbreptask`
> 
> ```xml
> <RepTask Name="file:/VTT_Demo/A.hdbreptask:workspace" Description="" Type="REALTIME" RepVersion="2.1">
>   <SourceObjects SourceType="REMOTE_OBJ" TTFullyQualifiedName="false" VTFullyQualifiedName="false" RemoteSourceName="AHanaSource" VirtualTableSchema="SYSTEM">
>     <SourceObject RemoteObjectUniqueName="&quot;IM_SERVICES&quot;.&quot;INPUT_PRIM_KEY&quot;" SourceDisplayName="INPUT_PRIM_KEY">
>     </SourceObject>
>   </SourceObjects>
>   <TargetObjects SchemaName="SYSTEM">
>     <TargetObject Type="TABLE" ObjectName="IM_SERVICES_INPUT_PRIM_KEY" DropTargetTableIfExists="TRUE">
>       <TargetColumns>
>         <TargetColumn Name="PRIM_KEY" Datatype="VARCHAR" Length="6" Precision="6" Scale="0" Nullable="FALSE" PartOfPrimaryKey="TRUE">
>         </TargetColumn>
>         <TargetColumn Name="ADDRESS" Datatype="VARCHAR" Length="100" Precision="100" Scale="0" Nullable="TRUE" PartOfPrimaryKey="FALSE">
>         </TargetColumn>
>         <TargetColumn Name="PERSON" Datatype="VARCHAR" Length="100" Precision="100" Scale="0" Nullable="TRUE" PartOfPrimaryKey="FALSE">
>         </TargetColumn>
>       </TargetColumns>
>     </TargetObject>
>   </TargetObjects>
>   <Mappings>
>     <Mapping ObjectName="IM_SERVICES_INPUT_PRIM_KEY" RemoteObjectUniqueName="&quot;IM_SERVICES&quot;.&quot;INPUT_PRIM_KEY&quot;" FilterExpression="" ReplicationBehavior="InitLoadOnly" VTObjectName="IM_SERVICES_INPUT_PRIM_KEY">
>       <TargetColumns>
>         <TargetColumn Name="PRIM_KEY" ProjectionExpression="&quot;PRIM_KEY&quot;">
>         </TargetColumn>
>         <TargetColumn Name="ADDRESS" ProjectionExpression="&quot;ADDRESS&quot;">
>         </TargetColumn>
>         <TargetColumn Name="PERSON" ProjectionExpression="&quot;PERSON&quot;">
>         </TargetColumn>
>       </TargetColumns>
>     </Mapping>
>   </Mappings>
> </RepTask>
> 
> ```



<a name="loio0194ba9e421148dd9712400e449fc61f__section_qx1_3yh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbreptask" : {
>    "plugin_name"   : "com.sap.hana.di.reptask"
> }
> 
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

[Modelling Guide for SAP HANA Smart Data Integration and SAP HANA Smart Data Quality](https://help.sap.com/docs/HANA_SMART_DATA_INTEGRATION/cc7ebd3f344a4cdda20966a7617f52d8/458f9f6d981c48d2817ad93f8ac50d66.html?version=LATEST)

