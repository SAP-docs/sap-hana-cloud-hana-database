<!-- loio3abb2714091d495b9eb277ce6f9daa07 -->

# CS\_VIEW\_PARAMETERS System View

Provides a list of parameters of the objects in the SAP HANA database. Only calculation views are considered. The parameters of a view are parsed from the definition of the underlying scenario.



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

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema in which the object is deployed.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the object. Only the calculation views are listed. The calculation views are not shown if the underlying calculation scenario has no parameter.

</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the parameter. If a parameter is referenced by different views, then the parameters are listed for each view separately. Normally, the parameters in a calculation view begins and ends with “$$” character. For example: `$$VAR$$`.

</td>
</tr>
<tr>
<td valign="top">

IS\_MANDATORY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether a parameter is mandatory or not: TRUE/FALSE. If TRUE, the value of the parameter should be provided either by setting the default value or through the SQL query. If FALSE, setting the value of the parameter is optional.

</td>
</tr>
<tr>
<td valign="top">

DEFAULT\_VALUE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the default value of the parameter. This column is set to an empty string when the parameter has no default value.

</td>
</tr>
<tr>
<td valign="top">

EVALUATED\_DEFAULT\_VALUE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the result of the evaluation of the expression in the DEFAULT\_VALUE column.

</td>
</tr>
<tr>
<td valign="top">

IS\_DEFAULT\_VALUE\_VOLATILE

</td>
<td valign="top">

BOOLEAN

</td>
<td valign="top">

Displays whether or not the default value is volatile: TRUE/FALSE.

</td>
</tr>
</table>



<a name="loio3abb2714091d495b9eb277ce6f9daa07__section_kh4_1t1_x2b"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.



<a name="loio3abb2714091d495b9eb277ce6f9daa07__section_sr1_xsj_nzb"/>

## Additional Information

Executing a SELECT statement on this monitoring view can be very expensive since the scenarios that have not been cached are fetched from the repository, parsed, and their parameters are extracted. However, providing SCHEMA\_NAME and OBJECT\_NAME columns can significantly decrease the amount of query time.

**Related Information**  


[VIEW\_PARAMETERS System View](view-parameters-system-view-45b86e8.md "Provides information about view parameters.")

[CS\_ALL\_COLUMNS System View](cs-all-columns-system-view-813f1ae.md "Provides information from all columns of column tables, including internal ones.")

[CS\_BO\_VIEWS System View](cs-bo-views-system-view-209fd90.md "Provides information about business object views for column store join views.")

[CS\_CONCAT\_COLUMNS System View](cs-concat-columns-system-view-02fb9ca.md "Provides information on concat columns in the database.")

[CS\_FREESTYLE\_COLUMNS System View](cs-freestyle-columns-system-view-20a0065.md "Provides freestyle search columns for column store join views.")

[CS\_JOIN\_CONDITIONS System View](cs-join-conditions-system-view-20a034d.md "Provides join conditions for column store join views.")

[CS\_JOIN\_CONSTRAINTS System View](cs-join-constraints-system-view-20a06e5.md "Provides join constraints for column store join views.")

[CS\_JOIN\_PATHS System View](cs-join-paths-system-view-20a09ec.md "Provides join paths for column store join views.")

[CS\_JOIN\_TABLES System View](cs-join-tables-system-view-20a0cc3.md "Provides information about the physical tables referred to by column store join views.")

[CS\_KEY\_FIGURES System View](cs-key-figures-system-view-20a0f88.md "Provides information about the key figures defined for column store join views.")

[CS\_VIEW\_COLUMNS System View](cs-view-columns-system-view-20a1288.md "Provides information about the columns defined for column store join views.")

[Memory Management in the Column Store](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/bd6e6be8bb5710149e34e14608e07b76.html "The column store is the part of the SAP HANA database that manages data organized in columns in memory. Tables created as column tables are stored here.") :arrow_upper_right:

[SELECT Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

[Procedure Parameters](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/3809c45287c44908a3d45a4db1514a55.html "") :arrow_upper_right:

[Function Parameters](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/58106d8f4fb44120b76fc6fb1f4a0bcc.html "") :arrow_upper_right:

[Table Parameter](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/9bd0c03743164aa7a87a93f9afb253b1.html "") :arrow_upper_right:

[Array Parameters for Procedures and Functions](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/dcffe459010546bd981d3b74b3798962.html "You can create procedures and functions with array parameters so that array variables or constant arrays can be passed to them.") :arrow_upper_right:

