<!-- loio20ce05a3751910149c86ae812bde572e -->

# SEARCH\_RULE\_SET\_CONDITIONS System View

Shows conditions to available search rule sets.



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

SEARCH\_RULE\_SET\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the runtime schema of the search rule set.

</td>
</tr>
<tr>
<td valign="top">

SEARCH\_RULE\_SET\_PACKAGE\_ID

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the repository package of the search rule set.

</td>
</tr>
<tr>
<td valign="top">

SEARCH\_RULE\_SET\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the search rule set.

</td>
</tr>
<tr>
<td valign="top">

RULE\_NUMBER

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of the rule that contains the column.

</td>
</tr>
<tr>
<td valign="top">

RULE\_ID

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the unique ID/name of the rule that contains the column.

</td>
</tr>
<tr>
<td valign="top">

SEARCHED\_COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of a column that is used by a search rule set.

</td>
</tr>
<tr>
<td valign="top">

SEARCHED\_COLUMN\_CONDITION

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the condition: EQUALS, NOT EMPTY, or MISSING.

</td>
</tr>
<tr>
<td valign="top">

SEARCHED\_COLUMN\_VALUE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the value the user input is compared to, if condition is EQUALS.

</td>
</tr>
<tr>
<td valign="top">

SEARCHED\_COLUMN\_VALUE\_REPLACED\_BY

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the user input is replaced by this value if the action is REPLACE.

</td>
</tr>
<tr>
<td valign="top">

ACTION

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the action that is performed when the condition is true: SKIP COLUMN, SKIP RULE, or REPLACE.

</td>
</tr>
</table>



<a name="loio20ce05a3751910149c86ae812bde572e__section_msp_yrz_2zb"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[SEARCH\_RULE\_SETS System View](search-rule-sets-system-view-20ceb95.md "Shows information about available search rule sets.")

[Search in Table Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/1eb7673ed88b4aa9b2cb43959bbbbde0.html "This feature offers an efficient way to search by key value pairs in table variables.") :arrow_upper_right:

