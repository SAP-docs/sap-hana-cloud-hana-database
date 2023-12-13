<!-- loio5619d09661434c209325ea6269534b3b -->

# M\_PLUGIN\_STATUS System View

Provides status for plugins.



## Structure


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

PLUGIN\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the subdirectory, containing executables and plugins, where the files of an AFL area are located. There can be several areas per subdirectory.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_TEXT

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the error message in case a package or AFL cannot be registered.

</td>
</tr>
<tr>
<td valign="top">

AREA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of an area.

</td>
</tr>
<tr>
<td valign="top">

AREA\_STATUS

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the status of an area: REGISTRATION SUCCESSFUL, REGISTRATION FAILED, or REGISTRATION SKIPPED.

</td>
</tr>
<tr>
<td valign="top">

PACKAGE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of a package, which is an internal representation of an AFL. There can be several packages per area.

</td>
</tr>
<tr>
<td valign="top">

PACKAGE\_STATUS

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the status of a package: REGISTRATION SUCCESSFUL, REGISTRATION FAILED, or REGISTRATION SKIPPED.

</td>
</tr>
</table>

**Related Information**  


[M\_PLUGIN\_MANIFESTS System View](m-plugin-manifests-system-view-20b7c62.md "Provides information about installed plugins.")

[Configure the Default Build Plug-in Libraries Available to an SAP HDI Container](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_4_QRC/en-US/016e9afdb7b54bfca0679c7358ccb543.html "Maintain the set of plug-in libraries available by default in an SAP HDI container.") :arrow_upper_right:

[List The Plug-in Libraries That Can Be Configured for an SAP HDI Container](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_4_QRC/en-US/b00b44d7881a46339e3ed6a25df99b67.html "You can find out which SAP HANA Deployment Infrastructure (HDI) plug-in libraries and versions are available in the database and can be configured for use in an HDI container.") :arrow_upper_right:

[Configure a Custom Set of Build Plug-in Libraries Available to an SAP HDI Container](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_4_QRC/en-US/f0557bf56f45441fb3a324a7cda07e30.html "Maintain a custom set of plug-in libraries available in an SAP HDI container.") :arrow_upper_right:

[List All Currently Configured Build Plug-in Libraries Available to an SAP HDI Container](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_4_QRC/en-US/ddb04a9bbbe645f7bcfecf38c599e279.html "Display a list of all the build plug-in libraries available for use in an SAP HDI container.") :arrow_upper_right:

