<!-- loio2102bf28751910149d0a817a65699956 -->

# VIEWS System View

Lists available views.



<a name="loio2102bf28751910149d0a817a65699956___v_i_e_w_s_1struct_VIEWS"/>

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

Displays the schema name.

</td>
</tr>
<tr>
<td valign="top">

VIEW\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the view name.

</td>
</tr>
<tr>
<td valign="top">

VIEW\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the view.

</td>
</tr>
<tr>
<td valign="top">

IS\_READ\_ONLY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether this view is read-only: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_DDL\_ONLY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether users can query the view and modify the underlying table.

</td>
</tr>
<tr>
<td valign="top">

HAS\_CHECK\_OPTION

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether this view has an updatable view condition: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

HAS\_COLUMN\_ALIASES

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the view has a columns alias: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

DEFINITION

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the view definition.

</td>
</tr>
<tr>
<td valign="top">

COMMENTS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the view description.

</td>
</tr>
<tr>
<td valign="top">

IS\_COLUMN\_VIEW

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether this view is a column view: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

VIEW\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the type of view: ROW, OLAP, JOIN, HIERARCHY, or CALC.

</td>
</tr>
<tr>
<td valign="top">

IS\_VALID

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the view is valid or not. This value is FALSE when its base objects are changed or dropped: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

HAS\_MASKED\_COLUMNS

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the view has a mask definition for at least one column: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

MASK\_MODE

</td>
<td valign="top">

NVARCHAR\(12\)

</td>
<td valign="top">

Displays the mask mode to be applied if the view has masked columns: DEFAULT or SESSION USER; otherwise NULL.

</td>
</tr>
<tr>
<td valign="top">

HAS\_PARAMETERS

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the view has parameters defined: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

HAS\_ANONYMIZATION

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the view is defined as anonymized: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

HAS\_CACHE

</td>
<td valign="top">

NVARCHAR\(36\)

</td>
<td valign="top">

Displays the result cache type for the view: STATIC or DYNAMIC.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the creation time.

</td>
</tr>
</table>



<a name="loio2102bf28751910149d0a817a65699956__section_arb_m11_fzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CREATE VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-view-statement-data-definition-20d5fa9.md "Creates a view on the database.")

[ALTER VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-view-statement-data-definition-3bc8951.md "Alters the definition, restrictions, or options on a view.")

[DROP VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-view-statement-data-definition-20d9c05.md "Removes a view from the database.")

[ANONYMIZATION\_VIEWS System View](anonymization-views-system-view-2992220.md "Provides information about anonymized views in the SAP HANA database.")

[VIEW\_COLUMNS System View](view-columns-system-view-21028f1.md "Lists available view columns.")

[VIEW\_EXPRESSION\_MACROS System View](view-expression-macros-system-view-d163421.md "Describes the expression macros defined for views.")

[VIEW\_PARAMETERS System View](view-parameters-system-view-45b86e8.md "Provides information about view parameters.")

[System Views for Monitoring Partitions](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/9d829883639d445884cc0d9210f14394.html "A number of system views allow you to monitor your partitions.") :arrow_upper_right:

