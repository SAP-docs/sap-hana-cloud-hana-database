<!-- loio57e2fe608bb042d48b799d41a8d121a7 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# User Preferences for SAP HANA Native Application Development Tools

Customize the SAP HANA Native Application project workspace by setting or modifying user preferences.



You can set user preferences to customize the way you start and use selected tools and features provided by the SAP HANA Native Application extension for SAP Business Application Studio.

To open the *Preferences* pane in SAP Business Application Studio, start the development workspace, choose <span class="SAP-icons"></span> \(Settings\)and then choose *Open Preferences*.

In the SAP HANA Native Application extension, you can set user preferences for the following components:

-   [SAP HANA Database Artifacts](user-preferences-for-sap-hana-native-application-development-tools-57e2fe6.md#loio57e2fe608bb042d48b799d41a8d121a7__section_xvp_t44_nsb)
-   [SAP HANA Database Explorer](user-preferences-for-sap-hana-native-application-development-tools-57e2fe6.md#loio57e2fe608bb042d48b799d41a8d121a7__section_n13_n44_nsb)
-   [SAP HANA Project Explorer](user-preferences-for-sap-hana-native-application-development-tools-57e2fe6.md#loio57e2fe608bb042d48b799d41a8d121a7__section_n2h_q44_nsb)
-   [SAP HANA SQLScript LSP](user-preferences-for-sap-hana-native-application-development-tools-57e2fe6.md#loio57e2fe608bb042d48b799d41a8d121a7__section_es5_r44_nsb)
-   [Calculation View Editor](user-preferences-for-sap-hana-native-application-development-tools-57e2fe6.md#loio57e2fe608bb042d48b799d41a8d121a7__section_t43_v44_nsb)



<a name="loio57e2fe608bb042d48b799d41a8d121a7__section_xvp_t44_nsb"/>

## SAP HANA Database Artifacts

To display the user preferences that you can set for the creation and management of SAP HANA database artifacts, open the *Preferences* tab, enter ***SAP HANA*** in the filter box, and select the extension *SAP HANA Database Artifacts* in the list of results displayed.

The following table lists the user preferences you can set to customize the tools used in the creation of SAP HANA database artifacts:

<a name="loio57e2fe608bb042d48b799d41a8d121a7__table_kfq_4t4_nsb"/>SAP HANA Database Artifacts: User Preferences


<table>
<tr>
<th valign="top">

User Preference



</th>
<th valign="top">

Details



</th>
</tr>
<tr>
<td valign="top">

 *Display SAP Web Analytics Startup Notification* 



</td>
<td valign="top">

Display a notification during start up which informs the user about the collection and analysis of data.

> ### Note:  
> Only available in Visual Studio Code, not in SAP Business Application Studio.



</td>
</tr>
<tr>
<td valign="top">

 *Last Selected Target Path* 



</td>
<td valign="top">

The path that was last selected when creating a database artifact; it is used as the default path when creating a new database artifact. The value must be a valid file path, otherwise it will be ignored.



</td>
</tr>
<tr>
<td valign="top">

 *Remember Last Selected Target Path* 



</td>
<td valign="top">

If selected, the design-time artifacts-creation Wizard for SAP HANA remembers \(and uses\) the last selected target path.



</td>
</tr>
</table>



<a name="loio57e2fe608bb042d48b799d41a8d121a7__section_n13_n44_nsb"/>

## SAP HANA Database Explorer

To display the user preferences that you can set for the *SAP HANA Database Explorer* in the *SAP HANA Native Application* extension, open the *Preferences* tab, enter ***SAP HANA*** in the filter box, and select *SAP HANA Database Explorer* in the list of results displayed.

The following table lists the user preferences you can set to customize the embedded *SAP HANA Database Explorer*:

<a name="loio57e2fe608bb042d48b799d41a8d121a7__table_r1d_dr4_nsb"/>SAP HANA Database Explorer: User Preferences


<table>
<tr>
<th valign="top">

User Preference



</th>
<th valign="top">

Details



</th>
</tr>
<tr>
<td valign="top">

 *Database List* 



</td>
<td valign="top">

Display the list of manually added databases. You can also edit the list to add, modify, or remove individual list entries.

> ### Note:  
> Only available in Visual Studio Code, not in SAP Business Application Studio.



</td>
</tr>
<tr>
<td valign="top">

 *Display SAP Web Analytics Startup Notification* 



</td>
<td valign="top">

Display a notification during start up which informs the user about the collection and analysis of data.

> ### Note:  
> Only available in Visual Studio Code, not in SAP Business Application Studio.



</td>
</tr>
<tr>
<td valign="top">

 *Show Database Explorer Connections* 



</td>
<td valign="top">

Show the list of database connections managed by the SAP HANA Database Explorer in addition to the local connections.

> ### Note:  
> Only available in Visual Studio Code, not in SAP Business Application Studio.



</td>
</tr>
<tr>
<td valign="top">

 *Logging: Level* 



</td>
<td valign="top">

Specified the verbosity of logging information collected according to the following order: trace \> debug \> info \> warn \> error \> fatal \> off.



</td>
</tr>
<tr>
<td valign="top">

 *Logging: Source Location Tracking* 



</td>
<td valign="top">

Add the source-code location to the log entries.

> ### Note:  
> Enabling this setting might slow down the extension. We recommend you use it only when debugging.



</td>
</tr>
<tr>
<td valign="top">

 *Max Sql Result Size* 



</td>
<td valign="top">

Specifies the maximum number of SQL results returned by any queries.



</td>
</tr>
<tr>
<td valign="top">

 *URL* 



</td>
<td valign="top">

Specifies the URL of the SAP HANA Database Explorer instance to use. The following pattern is required for the URL:

```
https://hana-cockpit.cfapps.<region>.hana.ondemand.com/sap/hana/cst/catalog/index.html. 
```

You need to replace <code><i class="varname">&lt;region&gt;</i></code> with the Cloud region of your database, for example, "***eu10***".



</td>
</tr>
</table>



<a name="loio57e2fe608bb042d48b799d41a8d121a7__section_n2h_q44_nsb"/>

## SAP HANA Project Explorer

To display the user preferences that you can set for the *SAP HANA Project* explorer in the *SAP HANA Native Application* extension, open the *Preferences* tab, enter ***SAP HANA*** in the filter box, and select *SAP HANA Project Explorer* in the list displayed.

The following table lists the user preferences you can set to customize the *SAP HANA Project Explorer*:

<a name="loio57e2fe608bb042d48b799d41a8d121a7__table_rzq_gv4_nsb"/>SAP HANA Project Explorer: User Preferences


<table>
<tr>
<th valign="top">

User Preference



</th>
<th valign="top">

Details



</th>
</tr>
<tr>
<td valign="top">

 *Auto Reveal* 



</td>
<td valign="top">

Select edited files and reveal their location in the *SAP HANA Projects* explorer.



</td>
</tr>
<tr>
<td valign="top">

 *Bind: Bind user-provided services to target containers* 



</td>
<td valign="top">

Allow a user-provided service to be bound to the target container of a database module. If you disable this option, only "hdi-shared" services can be bound to target containers..



</td>
</tr>
<tr>
<td valign="top">

 *Bind: Confirm automatic undeployment* 



</td>
<td valign="top">

Ask whether automatic undeployment should be disabled when binding a module to an existing service.



</td>
</tr>
<tr>
<td valign="top">

 *Bind: Confirm existing service* 



</td>
<td valign="top">

Display a confirmation message before binding a database module to an existing Cloud Foundry service. Warning: binding a project to an existing service can lead to data loss if the database module does not match the content of the existing service.



</td>
</tr>
<tr>
<td valign="top">

 *Deploy: Auto clean deployment log* 



</td>
<td valign="top">

Clear the deployment log before starting a new deployment.



</td>
</tr>
<tr>
<td valign="top">

 *Deploy: Keep default-env file* 



</td>
<td valign="top">

Retain the `default-env.json` file in the workspace after deployment.

> ### Caution:  
> This file might contain sensitive information. We recommend you use this option only for debugging.



</td>
</tr>
<tr>
<td valign="top">

 *Logging: Level* 



</td>
<td valign="top">

The verbosity of logging according to the following order: trace \> debug \> info \> warn \> error \> fatal \> off.



</td>
</tr>
<tr>
<td valign="top">

 *Logging: Source Location Tracking* 



</td>
<td valign="top">

Add the source-code location to the log entries.

> ### Note:  
> Enabling this setting might slow down the extension. We recommend you use it only when debugging.



</td>
</tr>
<tr>
<td valign="top">

 *Unbind: Unbind all services if the Cloud Foundry space changes* 



</td>
<td valign="top">

Enable this option, if you want all services of all database modules to be automatically unbound when an application project’s Cloud Foundry space is changed.



</td>
</tr>
</table>



<a name="loio57e2fe608bb042d48b799d41a8d121a7__section_es5_r44_nsb"/>

## SAP HANA SQLScript LSP

To display the user preferences that you can set for SAP HANA SQLScript language services \(LSP\) in the *SAP HANA Native Application* extension, open the *Preferences* tab, enter ***SAP HANA*** in the filter box, and select *SAP HANA SQLScript LSP* in the list of results displayed.

The following table lists the user preferences you can set to customize the use of SAP HANA SQLScript LSP:

<a name="loio57e2fe608bb042d48b799d41a8d121a7__table_jqv_cw4_nsb"/>SAP HANA SQLScript LSP: User Preferences


<table>
<tr>
<th valign="top">

User Preference



</th>
<th valign="top">

Details



</th>
</tr>
<tr>
<td valign="top">

 *Max Number Of Problems* 



</td>
<td valign="top">

Controls the maximum number of problems produced by the server.

Default: 100



</td>
</tr>
<tr>
<td valign="top">

 *Trace: Server* 



</td>
<td valign="top">

Traces the communication between VS Code and the language server. Possible values: "off", "messages", "verbose".

Default: Verbose



</td>
</tr>
<tr>
<td valign="top">

 *URL* 



</td>
<td valign="top">

This configuration is intended for internal purpose. Please do not change this.



</td>
</tr>
</table>



<a name="loio57e2fe608bb042d48b799d41a8d121a7__section_t43_v44_nsb"/>

## Calculation View Editor

To display the user preferences that you can set for the calculation-view editor in the *SAP HANA Native Application* extension, open the *Preferences* tab, enter ***calculation view*** in the filter box, and select *Extensions* \> *Watt Feature* in the list of results displayed.

The following table lists the user preferences you can set to customize the use of the calculation-view editor:

<a name="loio57e2fe608bb042d48b799d41a8d121a7__table_fmv_x1p_nsb"/>SAP HANA Calculation Views: User Preferences


<table>
<tr>
<th valign="top">

User Preference



</th>
<th valign="top">

Details



</th>
</tr>
<tr>
<td valign="top">

 *Data Preview: Require Manual Refresh For Raw Data* 



</td>
<td valign="top">

Require the manual refresh of data when opening a table or view, and when visualizing data in the *Analysis* tab



</td>
</tr>
<tr>
<td valign="top">

 *Mapping Pane* 



</td>
<td valign="top">

Set the required preference to customize the columns displayed in the mapping panes



</td>
</tr>
<tr>
<td valign="top">

 *Performance Analysis Always On* 



</td>
<td valign="top">

Display a warning icon next to the names of tables that have more rows than the set threshold

Default: 0 \(Zero\)



</td>
</tr>
<tr>
<td valign="top">

 *Shortcuts: \[Add | Edit | Create | Open | Show\] *<element\>** 



</td>
<td valign="top">

In SAP Business Application Studio, keyboard shortcuts for calculation views use the following format: [ctrl+\], [alt+\], [option+\], [shift+\] and a key; or [insert\]; or [F1\]-[F12\], for example:

-   Add an input parameter:  [ctrl\] + [shift\] + [i\] 
-   Create a join node:  [alt\] + [shift\] + [f1\] 
-   Create a calculated column:  [alt\] + [shift\] + [u\] 
-   Add a variable:  [ctrl\] + [shift\] + [v\] 
-   Create a data preview:  [alt\] + [shift\] + [d\]  

> ### Note:  
> For more information about keyboard shortcuts for the calculation view editor, see *Related Information* below.



</td>
</tr>
</table>

**Related Information**  


[Keyboard Shortcuts for the Calculation View Editor \(SAP HANA Cloud, SAP HANA Database Modeling Guide for SAP Business App Studio\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/d625b46ef0b445abb2c2fd9ba008c265/0972b5a1002944c5aae9a1f242f1a3c3.html)

[View Database Objects with the Database Explorer](view-database-objects-with-the-database-explorer-0e5ac0b.md "Check the contents of your database with SAP HANA Database Explorer.")

