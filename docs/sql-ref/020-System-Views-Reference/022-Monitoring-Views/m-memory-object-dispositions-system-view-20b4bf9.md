<!-- loio20b4bf907519101481bf923fefa3f23e -->

# M\_MEMORY\_OBJECT\_DISPOSITIONS System View

Displays the disposition-specific memory object statistics.



<a name="loio20b4bf907519101481bf923fefa3f23e___m__m_e_m_o_r_y__o_b_j_e_c_t__d_i_s_p_o_s_i_t_i_o_n_s_1struct_M_MEMORY_OBJECT_DISPOSITIONS"/>

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

TYPE

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the object statistic type.

</td>
</tr>
<tr>
<td valign="top">

CATEGORY

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the allocator category, the corresponding allocator, and some of its sub-allocators that were used to allocate the memory objects.

</td>
</tr>
<tr>
<td valign="top">

TEMPORARY\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of temporary objects.

</td>
</tr>
<tr>
<td valign="top">

PAGE\_LOADABLE\_COLUMNS\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of page loadable column objects.

</td>
</tr>
<tr>
<td valign="top">

EARLY\_UNLOAD\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of early unload objects.

</td>
</tr>
<tr>
<td valign="top">

INTERNAL\_SHORT\_TERM\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of internal short term objects.

</td>
</tr>
<tr>
<td valign="top">

SHORT\_TERM\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of short term objects.

</td>
</tr>
<tr>
<td valign="top">

MID\_TERM\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of mid term objects.

</td>
</tr>
<tr>
<td valign="top">

LONG\_TERM\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of long term objects.

</td>
</tr>
<tr>
<td valign="top">

NON\_SWAPPABLE\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of non-swappable objects.

</td>
</tr>
<tr>
<td valign="top">

TEMPORARY\_OBJECT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the temporary objects in bytes.

</td>
</tr>
<tr>
<td valign="top">

PAGE\_LOADABLE\_COLUMNS\_OBJECT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of page loadable column objects in bytes.

</td>
</tr>
<tr>
<td valign="top">

EARLY\_UNLOAD\_OBJECT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the early unload objects in bytes.

</td>
</tr>
<tr>
<td valign="top">

INTERNAL\_SHORT\_TERM\_OBJECT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the internal short term objects in bytes.

</td>
</tr>
<tr>
<td valign="top">

SHORT\_TERM\_OBJECT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the short term objects in bytes.

</td>
</tr>
<tr>
<td valign="top">

MID\_TERM\_OBJECT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the mid term objects in bytes.

</td>
</tr>
<tr>
<td valign="top">

LONG\_TERM\_OBJECT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the long term objects in bytes.

</td>
</tr>
<tr>
<td valign="top">

NON\_SWAPPABLE\_OBJECT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the non swappable objects in bytes.

</td>
</tr>
<tr>
<td valign="top">

SHRINKABLE\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of shrinkable objects.

</td>
</tr>
<tr>
<td valign="top">

SHRINKABLE\_OBJECT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the shrinkable objects in bytes.

</td>
</tr>
</table>



<a name="loio20b4bf907519101481bf923fefa3f23e___m__m_e_m_o_r_y__o_b_j_e_c_t__d_i_s_p_o_s_i_t_i_o_n_s_1fulldesc_M_MEMORY_OBJECT_DISPOSITIONS"/>

## Additional Information

The number and the size of the resources in the resource container are shown depending on their specific disposition \(whether the memory objects are short, mid, long term, or non-swappable\). For each type of resource that is specified by the resource statistic, which is currently in the resource container, one row is added to this view. The tree structure of the resource statistics is not considered here, therefore the values are not aggregated.

Reading this view may take some time as the entire resource container must be traversed to generate this view.

**Related Information**  


[M\_MEMORY\_OBJECTS System View](m-memory-objects-system-view-20b4e47.md "Returns memory object statistics.")

[M\_MEMORY\_OBJECTS\_RESET System View](m-memory-objects-reset-system-view-20b508b.md "Provides values accumulated since the last reset of the main view M_MEMORY_OBJECTS.")

[Managing Memory by Object Usage](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/815fd19868d84c13962852faa3b1ee85.html "You can use the Unused Retention Period feature to automatically unload objects from memory which are not being used.") :arrow_upper_right:

