<!-- loio7ecc1cc0e5d34d0dbc646fe26f8fffe5 -->

# M\_TABLE\_PLACEMENT\_LOCATIONS System View

Provides table placement location monitoring information.



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

LOCATION\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the location.



</td>
</tr>
<tr>
<td valign="top">

SYSTEM\_DEFINED\_VOLUME\_IDS



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the volume IDs, which are received from the topology.



</td>
</tr>
<tr>
<td valign="top">

INCLUDE



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the list of volume IDs or synonyms which are added to the location name.



</td>
</tr>
<tr>
<td valign="top">

EXCLUDE



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the list of volume IDs or synonyms which are removed from the location name.



</td>
</tr>
<tr>
<td valign="top">

EFFECTIVE\_VOLUME\_IDS



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the calculated volume IDs for the location name.



</td>
</tr>
</table>

**Related Information**  


[ALTER SYSTEM ALTER TABLE PLACEMENT Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-alter-table-placement-statement-system-management-0715b97.md "Changes table classification and placement settings for table groups.")

[TABLE\_PLACEMENT System View](../021-System-Views/table-placement-system-view-522cc8e.md "Provides table placement information.")

[M\_EFFECTIVE\_TABLE\_PLACEMENT System View](m-effective-table-placement-system-view-f3f74ec.md "Provides information about effective placement of tables.")

[TABLE\_PLACEMENT\_LOCATIONS System View](../021-System-Views/table-placement-locations-system-view-9e74012.md "Provides table placement location information.")

[M\_TABLE\_PLACEMENT\_LOCATIONS System View](m-table-placement-locations-system-view-7ecc1cc.md "Provides table placement location monitoring information.")

[CREATE TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

[ALTER TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[Table Placement Rules for Replicas](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/266f9d2a727148f586d7bfb2a0cc4df8.html "The following SQL commands create table placement rules for replica schema, which can be used to create or add replica tables.") :arrow_upper_right:

[M\_TABLE\_LOCATIONS System View](m-table-locations-system-view-20c65d5.md "Provides information about tables and their logical location. Physical locations are shown in M_TABLE_PERSISTENCE_LOCATIONS.")

