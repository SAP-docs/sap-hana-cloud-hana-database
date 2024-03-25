<!-- loioc55fb25569fa4c019370632da3b46f74 -->

# LIST\_CONFIGURED\_LIBRARIES

Display which build plug-in libraries are available in an HDI container.



The SAP HDI Container API includes the `LIST_CONFIGURED_LIBRARIES` command, which enables you to display a list the build plug-ins that are available for use in a specified HDI container.



<a name="loioc55fb25569fa4c019370632da3b46f74__section_ylt_tjw_f2b"/>

## Signature

> ### Sample Code:  
> ```sql
> 
> ```



<a name="loioc55fb25569fa4c019370632da3b46f74__section_gg2_zfw_f2b"/>

## Parameters

The following parameters can be used with `IN`LIST\_CONFIGURED\_LIBRARIES and `OUT` parameters in the `LIST_CONFIGURED_LIBRARIES` command:

> ### Tip:  
> For more information about all available SAP HANA HDI parameters, see *Available SAP HDI Parameters* in *Related Information* below.



### RETURN\_CODE \[OUT\]

The return code indicates if the procedure executed successfully. For more details about which codes are returned, see *The SQL API for SAP HDI* in *Related Information*.



### REQUEST\_ID \[OUT\]

A unique ID is generated for each HDI container API call. For more details about which IDs are generated for API calls, see *The SQL API for SAP HDI* in *Related Information*.



### MESSAGES \[OUT\]

A table is used to display messages that contain information logged during \(and about\) the execution of the procedure. For more details about which codes are returned, see *The SQL API for SAP HDI* in *Related Information*.



### RESULT \[OUT\]

Returns a list of the build plug-in libraries that have been configured for the container by the container's administrator.

**\_SYS\_DI.c**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

LIBRARY\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The name of the build plug-in library domain where the build plug-in is located

</td>
</tr>
<tr>
<td valign="top">

LIBRARY\_VERSION

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

The version number of the build plug-in library

</td>
</tr>
<tr>
<td valign="top">

PLUGIN\_ID

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The identifying name of the build plug-in

</td>
</tr>
<tr>
<td valign="top">

PLUGIN\_VERSION

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

The version number of the build plug-in

</td>
</tr>
</table>



<a name="loioc55fb25569fa4c019370632da3b46f74__section_ozt_kyj_dfb"/>

## Examples

The following example shows an excerpt from the response to the call `LIST_CONFIGURED_LIBRARIES` for the container "C" including information about the configured libraries:

> ### Sample Code:  
> Call `#DI.LIST_CONFIGURED_LIBRARIES`
> 
> ```sql
> CALL <container name>#DI.LIST_CONFIGURED_LIBRARIES(_SYS_DI.T_NO_PARAMETERS, ?, ?, ?, ?);
> ```

> ### Note:  
> For reasons of space, the example command output displayed below is occasionally incomplete \(`[...]`\); the example output is provided here for illustration purposes only.

> ### Output Code:  
> Call `#DI.LIST_CONFIGURED_LIBRARIES` 
> 
> ```sql
> 
> LIBRARY_                          LIBRARY_  PLUGIN_                            PLUGIN_
> NAME                              VERSION   ID                                 VERSION
> ---------------------------------------------------------------------------------------
> com.sap.hana.di.afllangprocedure  0.0       com.sap.hana.di.afllangprocedure   2.0.30.0
> com.sap.hana.di.analyticprivilege 0.0       com.sap.hana.di.analyticprivilege  2.0.30.0
> com.sap.hana.di.calculationview   0.0       com.sap.hana.di.calculationview    2.0.30.0
> com.sap.hana.di.cds               0.0       com.sap.hana.di.cds                2.0.30.0
> com.sap.hana.di.collection        0.0       com.sap.hana.di.collection         2.0.30.0
> ...
> ```

**Related Information**  


[The HDI Container API](the-hdi-container-api-40ba784.md "Maintain HDI containers and container content using the HDI container API.")

[The SQL API for SAP HANA Deployment Infrastructure \(HDI\)](../the-sql-api-for-sap-hana-deployment-infrastructure-hdi-035dbbe.md "An SQL application programming interface (API) is available to help maintain the SAP HANA Deployment Infrastructure (HDI).")

[Available SAP HDI Parameters](https://help.sap.com/docs/HANA_CLOUD_DATABASE/c2cc2e43458d4abda6788049c58143dc/e2d3e543067e4f3282bf6dbf880c6b2d.html?version=2023_3_QRC#available-sap-hdi-parameters)

