<!-- loio71ed23cbded54f6297440a53d949ff06 -->

# SAP HDI Container Schemas

An SAP HANA Deployment Infrastructure \(HDI\) container makes use of multiple schemas; each of the different schemas serves different aims and tasks.



Maintaining HDI containers involves the configuration and use of the schemas listed and described in the following table:

> ### Note:  
> In the following table, the schema names are based on the assumption that the base HDI container is named “C”.

**HDI Container Schema Names and Usage**


<table>
<tr>
<th valign="top">

HDI Container Schema Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

C

</td>
<td valign="top">

Contains generated database objects that belong to a special object-owner user called `C#OO`. The database objects are generated from design-time objects in container C.

</td>
</tr>
<tr>
<td valign="top">

C\#DI

</td>
<td valign="top">

Contains the API procedures and HDI-internal data required for the container management

</td>
</tr>
<tr>
<td valign="top">

C\#OO

</td>
<td valign="top">

The schema for the user to whom the artifacts in the base container “C” belong. The user schema C\#00 is empty.

</td>
</tr>
</table>

**Related Information**  


[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

[Configure SAP HDI Parameters](../13-HDI-Cloud-Admin-Maintain-HDI/configure-sap-hdi-parameters-7c989fa.md "The SAP HANA Deployment Infrastructure (HDI) administrator can configure some general aspects of the HDI with parameters, for example, how long an HDI operation waits for a locking conflict to clear or the default behavior of HDI containers.")

[Maintaining the SAP HDI](../13-HDI-Cloud-Admin-Maintain-HDI/maintaining-the-sap-hdi-df043e3.md "Maintenance of the SAP HANA Deployment infrastructure (HDI) is the responsibility of the HDI administrator, who must set up and configure general HDI parameters.")

