<!-- loio20ac40bf75191014882bf6234500be92 -->

# M\_CONTAINER\_NAME\_DIRECTORY System View

Provides ContainerNameDirectory statistics.



<a name="loio20ac40bf75191014882bf6234500be92___m__c_o_n_t_a_i_n_e_r__n_a_m_e__d_i_r_e_c_t_o_r_y_1struct_M_CONTAINER_NAME_DIRECTORY"/>

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

Unit

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

 

</td>
<td valign="top">

Displays the host name.

</td>
</tr>
<tr>
<td valign="top">

PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

 

</td>
<td valign="top">

Displays the internal port.

</td>
</tr>
<tr>
<td valign="top">

VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

 

</td>
<td valign="top">

Displays the persistence volume ID.

</td>
</tr>
<tr>
<td valign="top">

CNT\_CREATE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Counter

</td>
<td valign="top">

Displays the create counts.

</td>
</tr>
<tr>
<td valign="top">

CNT\_CREATE\_FAIL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Counter

</td>
<td valign="top">

Displays the number of failed creates.

</td>
</tr>
<tr>
<td valign="top">

CNT\_INITIAL\_CREATE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Counter

</td>
<td valign="top">

Displays the number of creates on the load.

</td>
</tr>
<tr>
<td valign="top">

CNT\_INITIAL\_SKIP

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Counter

</td>
<td valign="top">

Displays the number of skips on the load.

</td>
</tr>
<tr>
<td valign="top">

CNT\_REMOVE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Counter

</td>
<td valign="top">

Displays the number of removes.

</td>
</tr>
<tr>
<td valign="top">

CNT\_REMOVE\_FAIL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Counter

</td>
<td valign="top">

Displays the number of failed removes.

</td>
</tr>
<tr>
<td valign="top">

CNT\_REMOVE\_ALL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Counter

</td>
<td valign="top">

Displays the number of removeAll.

</td>
</tr>
<tr>
<td valign="top">

CNT\_RENAME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Counter

</td>
<td valign="top">

Displays the number of renames.

</td>
</tr>
<tr>
<td valign="top">

CNT\_RENAME\_FAIL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Counter

</td>
<td valign="top">

Displays the number of failed renames.

</td>
</tr>
<tr>
<td valign="top">

CNT\_EXISTS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Counter

</td>
<td valign="top">

Displays the number of checked containers.

</td>
</tr>
<tr>
<td valign="top">

CNT\_GET

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Counter

</td>
<td valign="top">

Displays the number of retrieved containers.

</td>
</tr>
<tr>
<td valign="top">

CNT\_GET\_FAIL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Counter

</td>
<td valign="top">

Displays the number of failed gets.

</td>
</tr>
<tr>
<td valign="top">

CNT\_BEGIN

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Counter

</td>
<td valign="top">

Displays the number of used iterators.

</td>
</tr>
<tr>
<td valign="top">

CNT\_ITERATE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Counter

</td>
<td valign="top">

Displays the number of iterated containers.

</td>
</tr>
</table>



<a name="loio20ac40bf75191014882bf6234500be92__section_brn_sx5_tbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_CONTAINER\_DIRECTORY System View](m-container-directory-system-view-20ac192.md "Provides container directory statistics.")

[CONTAINS Predicate](../../010-SQL-Reference/contains-predicate-20f9524.md "Matches a search string with the results of a subquery.")

[Logic Container](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/2d84158c530941b898b2b88316ea7649.html "The following types of logic containers are available in SQLScript: Procedure, Anonymous Block, User-Defined Function, and User-Defined Library.") :arrow_upper_right:

