<!-- loio20ac192575191014aaec9f34d973c509 -->

# M\_CONTAINER\_DIRECTORY System View

Provides container directory statistics.



<a name="loio20ac192575191014aaec9f34d973c509___m__c_o_n_t_a_i_n_e_r__d_i_r_e_c_t_o_r_y_1struct_M_CONTAINER_DIRECTORY"/>

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

HOST

</td>
<td valign="top">

NVARCHAR\(64\)

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

Displays the internal port number.

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

Displays the number of creates.

</td>
</tr>
<tr>
<td valign="top">

CNT\_CREATE\_ROLLBACK

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of rolled back creates.

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

Displays the number of failed removes.

</td>
</tr>
<tr>
<td valign="top">

CNT\_REMOVE\_ROLLBACK

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of rolled back removes.

</td>
</tr>
<tr>
<td valign="top">

CNT\_MOVE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of moves.

</td>
</tr>
<tr>
<td valign="top">

CNT\_GET\_PHYSICALSIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of getPhysicalSize.

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

Displays the number of used iterators.

</td>
</tr>
<tr>
<td valign="top">

CNT\_ITERATED

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of iterated containers.

</td>
</tr>
<tr>
<td valign="top">

CNT\_CACHEHIT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of cache hits.

</td>
</tr>
<tr>
<td valign="top">

CNT\_CACHEMISS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of cache misses.

</td>
</tr>
</table>

**Related Information**  


[M\_CONTAINER\_NAME\_DIRECTORY System View](m-container-name-directory-system-view-20ac40b.md "Provides ContainerNameDirectory statistics.")

[CONTAINS Predicate](../../010-SQL-Reference/contains-predicate-20f9524.md "Matches a search string with the results of a subquery.")

[Logic Container](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/2d84158c530941b898b2b88316ea7649.html "The following types of logic containers are available in SQLScript: Procedure, Anonymous Block, User-Defined Function, and User-Defined Library.") :arrow_upper_right:

