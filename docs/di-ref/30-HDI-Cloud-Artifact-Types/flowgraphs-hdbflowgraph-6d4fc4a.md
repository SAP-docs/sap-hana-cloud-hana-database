<!-- loio6d4fc4a30e1d428bbb2b3dc5a73ab786 -->

# Flowgraphs \(.hdbflowgraph\)

Transform a design-time, flow-graph description into a corresponding set of database procedure or task objects.



A flow graph performs a configurable series of data transformation operations, such as joining, filtering, cleansing, masking, aggregating, and so on.

> ### Tip:  
> For more information about creating `.hdbflowgraph` artifacts, see the *Modeling Guide for SAP HANA Smart Data Integration and SAP HANA Smart Data Quality*.

The file format uses an XML-based syntax.



<a name="loio6d4fc4a30e1d428bbb2b3dc5a73ab786__section_rjj_yvh_1hb"/>

## Example Artifact Code

> ### Code Syntax:  
> `/src/SOURCE_TARGET.hdbflowgraph`
> 
> ```xml
> <?xml version="1.0" encoding="UTF-8"?>
> <flowgraph:ContainerNode xmlns:xmi="http://www.omg.org/XMI" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:flowgraph="http://www.sap.com/ndb/flowgraph/1.0" xmi:version="2.0" xmi:id="48c98de995349a58f789161dffecddbe" name="Sample" runtimeBehavior="BATCH_TASK">
> 	<annotations key="sap.afm.layout" xmi:id="1e9bdee19337604a2fe702f69b5602b8">
> 		<annotations xmi:id="f1eade7e1b55c09f00dee393b7a2ea0e" key="x" value="10">
> 		</annotations>
> 		<annotations xmi:id="1641fc95f79b40e0bf4bf5cb21f81bbb" key="y" value="10">
> 		</annotations>
> 		<annotations xmi:id="766ff0b1bdcb118aa9b23388e8cdfdd3" key="width" value="100">
> 		</annotations>
> 		<annotations xmi:id="2882970d6e43a4d3c8091c69a6f85d8f" key="height" value="84">
> 		</annotations>
> 	</annotations>
> 	<annotations xmi:id="de380e1c77c2bfc8d64806afa2c90dae" key="sap.afm.palette">
> 		<annotations xmi:id="64399b3a3b9f04990acc30077471df97" key="additions" value=""/>
> 	</annotations>
> 	<annotations xmi:id="d711eace8b9a9093e2960ff8a5f77907" key="sap.afm.nodeType" value="ContainerNode">
> 	</annotations>
> 	<annotations xmi:id="d1085bb9c5fb4b0ab561e8f3ea12ad34" key="sap.afm.nodeInputs">
> 	</annotations>
> 	<annotations xmi:id="40a784946ecb249542780fa272c213ce" key="sap.afm.nodeOutputs">
> 	</annotations>
> 	<tableMappings xmi:id="0d7122ab56cb9e5b25e8a9705e0a0cca" source="26ff77a7f671674044822dacec0260c4" target="1e7e63398016ec4631cdc305771a65c2">
> 		<attributeMappings xmi:id="6ecf80b841d18839a47c20e24e3c931a" source="4e3587cdc45c9261038d915014bee06e" target="30877cc439230ef4ea267db9e79cfe24">
> 		</attributeMappings>
> 		<attributeMappings xmi:id="643541c94681ac60cedceff184295921" source="6529b86aca8a98fcc9f35dbf376cb29e" target="3043f276bd90ef278e635e92797de2fd">
> 		</attributeMappings>
> 		<attributeMappings xmi:id="69c3940901d8a2604db6992ae83f35f4" source="8e795a3b4ae743a73947278478b782b8" target="247f3c3cc1f79b1f8fa99fddf4c8a083">
> 		</attributeMappings>
> 		<attributeMappings xmi:id="de651bb4a43e3e24f687036775e1b6b5" source="5876cbdaef85a0ca7d00ee3693bab1d1" target="072355443d648d4cbe94fa9566a6f513">
> 		</attributeMappings>
> 	</tableMappings>
> 	<nodes xmi:id="5afdacf9175d180411812b177312363e" name="DataSource" catalogObjectName="avijit.hdbav::qa_dept.Entity1" type="DATABASE_TABLE" xsi:type="flowgraph:DataNode" dataLayout="COLUMN">
> 		<annotations key="sap.afm.layout" xmi:id="b207966200646c7c6d93b2f1be8cbf9a">
> 			<annotations xmi:id="ea0f7461349e1f6af0e7d4db3394e15c" key="x" value="12">
> 			</annotations>
> 			<annotations xmi:id="e8a54115896fa0cf7460f822fcdcf54c" key="y" value="12">
> 			</annotations>
> 			<annotations xmi:id="db5fda29908c64f41d61e056c1b70fc6" key="width" value="120">
> 			</annotations>
> 			<annotations xmi:id="0e2701c55e90074e952edcdcb46a980a" key="height" value="115">
> 			</annotations>
> 		</annotations>
> 		<annotations xmi:id="fb0a48789c4bcb827f490dfa2284fba9" key="sap.afm.description">
> 		</annotations>
> 		<annotations xmi:id="99ad396311bf5361f547d17b23de5b00" key="sap.afm.nodeType" value="DataNode">
> 		</annotations>
> 		<annotations xmi:id="8863401ed0df9b898f8c41e2b03ace4c" key="sap.afm.nodeInputs">
> 		</annotations>
> 		<annotations xmi:id="f84979354b412a530c07410516b03183" key="sap.afm.nodeOutputs">
> 		</annotations>
> 		<annotations xmi:id="a2af10ac10cf0fbe01d0a56390868420" key="sap.afm.displayName" value="Data Source">
> 		</annotations>
> 		<annotations xmi:id="5eddebba1b0906bd1db0bd67ffab65d5" key="columns" value="[{&quot;name&quot;:&quot;DEPTNO&quot;,&quot;type&quot;:&quot;DECIMAL&quot;,&quot;length&quot;:28,&quot;nullable&quot;:&quot;false&quot;,&quot;primarykey&quot;:true},{&quot;name&quot;:&quot;DNAME&quot;,&quot;type&quot;:&quot;NVARCHAR&quot;,&quot;length&quot;:14,&quot;nullable&quot;:&quot;true&quot;},{&quot;name&quot;:&quot;LOC&quot;,&quot;type&quot;:&quot;NVARCHAR&quot;,&quot;length&quot;:14,&quot;nullable&quot;:&quot;true&quot;},{&quot;name&quot;:&quot;ST&quot;,&quot;type&quot;:&quot;NVARCHAR&quot;,&quot;length&quot;:2,&quot;nullable&quot;:&quot;true&quot;}]">
> 		</annotations>
> 		<outputs xmi:id="26ff77a7f671674044822dacec0260c4" name="DataSource">
> 			<attributes xmi:id="4e3587cdc45c9261038d915014bee06e" name="DEPTNO" type="DECIMAL" nullable="false" length="28">
> 				<annotations xmi:id="dd342f537524896cf2219533b48d3adf" key="sap.im.primaryKey" value="true"/>
> 			</attributes>
> 			<attributes xmi:id="6529b86aca8a98fcc9f35dbf376cb29e" name="DNAME" type="NVARCHAR" nullable="true" length="14">
> 			</attributes>
> 			<attributes xmi:id="8e795a3b4ae743a73947278478b782b8" name="LOC" type="NVARCHAR" nullable="true" length="14">
> 			</attributes>
> 			<attributes xmi:id="5876cbdaef85a0ca7d00ee3693bab1d1" name="ST" type="NVARCHAR" nullable="true" length="2">
> 			</attributes>
> 		</outputs>
> 	</nodes>
> 	<nodes xmi:id="fb754fcf4407048bd5f16fb1069fc611" name="DataTarget" catalogObjectName="DataTarget" type="TEMPLATE_TABLE" xsi:type="flowgraph:DataNode">
> 		<annotations key="sap.afm.layout" xmi:id="0cb7ed884bb690b9be60d8042c8c2b85">
> 			<annotations xmi:id="ed214d21c1fce72e14aad7d17cf27638" key="x" value="193">
> 			</annotations>
> 			<annotations xmi:id="a0fe6c35b6e73888cd54d8c2b559af99" key="y" value="12">
> 			</annotations>
> 			<annotations xmi:id="04e447789ef9d1e98c177274a411fe7e" key="width" value="120">
> 			</annotations>
> 			<annotations xmi:id="63f5a6ec04b1e54aece877e247259027" key="height" value="115">
> 			</annotations>
> 		</annotations>
> 		<annotations xmi:id="03ff7aba46adadd41f0d7af8fdd22382" key="sap.afm.description">
> 		</annotations>
> 		<annotations xmi:id="bd2f87dd6344e25ae338b3f46e882508" key="sap.afm.nodeType" value="DataNode">
> 		</annotations>
> 		<annotations xmi:id="58bb3d83aa10a12f684757235bf0fd09" key="sap.afm.nodeInputs">
> 		</annotations>
> 		<annotations xmi:id="1792d885b494117b8b094374ea6dea86" key="sap.afm.nodeOutputs">
> 		</annotations>
> 		<annotations xmi:id="bba0b5c651d69b745a803da7cff4a6e1" key="sap.afm.displayName" value="Data Target">
> 		</annotations>
> 		<inputs xmi:id="1e7e63398016ec4631cdc305771a65c2" name="DataTarget">
> 			<attributes xmi:id="30877cc439230ef4ea267db9e79cfe24" name="DEPTNO" type="DECIMAL" nullable="false" length="28">
> 				<annotations xmi:id="8a05e20a4791e8723346be4819eb2afd" key="sap.im.primaryKey" value="true"/>
> 			</attributes>
> 			<attributes xmi:id="3043f276bd90ef278e635e92797de2fd" name="DNAME" type="NVARCHAR" nullable="true" length="14">
> 			</attributes>
> 			<attributes xmi:id="247f3c3cc1f79b1f8fa99fddf4c8a083" name="LOC" type="NVARCHAR" nullable="true" length="14">
> 			</attributes>
> 			<attributes xmi:id="072355443d648d4cbe94fa9566a6f513" name="ST" type="NVARCHAR" nullable="true" length="2">
> 			</attributes>
> 		</inputs>
> 	</nodes>
> </flowgraph:ContainerNode>
> 
> ```



<a name="loio6d4fc4a30e1d428bbb2b3dc5a73ab786__section_uwf_xvh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbflowgraph" : {
>    "plugin_name"   : "com.sap.hana.di.flowgraph"
> }
> 
> ```

