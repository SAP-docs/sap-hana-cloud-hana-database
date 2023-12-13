<!-- loio20ab00a275191014a1c7a1c04a7547e6 -->

# M\_COMPACTION\_THREAD System View

Provides compaction thread statistics.



<a name="loio20ab00a275191014a1c7a1c04a7547e6___m__c_o_m_p_a_c_t_i_o_n__t_h_r_e_a_d_1struct_M_COMPACTION_THREAD"/>

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

NUM\_COMPACTION\_COLLISIONS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of memory compaction collisions, which includes other threads currently in compaction and unforced compactions.

</td>
</tr>
<tr>
<td valign="top">

NUM\_COMPACTIONS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of compaction requests.

</td>
</tr>
<tr>
<td valign="top">

LAST\_SIZE\_COMPACTION\_REQUESTS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size in bytes of the last compaction request.

</td>
</tr>
<tr>
<td valign="top">

MAX\_SIZE\_COMPACTION\_REQUESTS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum sized compaction request in bytes.

</td>
</tr>
<tr>
<td valign="top">

MIN\_SIZE\_COMPACTION\_REQUESTS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum sized compaction request in bytes.

</td>
</tr>
<tr>
<td valign="top">

SUM\_SIZE\_COMPACTION\_REQUESTS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of compaction requests in bytes.

</td>
</tr>
<tr>
<td valign="top">

AVG\_SIZE\_COMPACTION\_REQUESTS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average size of compaction requests in bytes.

</td>
</tr>
<tr>
<td valign="top">

LAST\_SIZE\_FREEABLE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size in bytes compacted by the last at compaction call.

</td>
</tr>
<tr>
<td valign="top">

MAX\_SIZE\_FREEABLE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size in bytes compacted by the maximum compaction call.

</td>
</tr>
<tr>
<td valign="top">

MIN\_SIZE\_FREEABLE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size in bytes compacted by the minimum compaction call.

</td>
</tr>
<tr>
<td valign="top">

SUM\_SIZE\_FREEABLE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size in bytes compacted by all compaction calls \(total\).

</td>
</tr>
<tr>
<td valign="top">

AVG\_SIZE\_FREEABLE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size in bytes compacted by the average compaction call.

</td>
</tr>
<tr>
<td valign="top">

LAST\_SIZE\_FREED\_BY\_GARBAGE\_COLLECTION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size in bytes compacted by the last memory garbage collection \(defragmentation\).

</td>
</tr>
<tr>
<td valign="top">

MAX\_SIZE\_FREED\_BY\_GARBAGE\_COLLECTION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size in bytes compacted by the largest memory garbage collection \(defragmentation\).

</td>
</tr>
<tr>
<td valign="top">

MIN\_SIZE\_FREED\_BY\_GARBAGE\_COLLECTION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size in bytes compacted by the smallest memory garbage collection \(defragmentation\).

</td>
</tr>
<tr>
<td valign="top">

SUM\_SIZE\_FREED\_BY\_GARBAGE\_COLLECTION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size in bytes compacted by all memory garbage collections \(defragmentation\) \(total\).

</td>
</tr>
<tr>
<td valign="top">

AVG\_SIZE\_FREED\_BY\_GARBAGE\_COLLECTION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size in bytes compacted by the average memory garbage collection \(defragmentation\).

</td>
</tr>
<tr>
<td valign="top">

LAST\_COMPACTION\_RESULT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last compaction result in bytes. This is the difference of allocated bytes before and after compaction and may be influenced by other factors than compaction.

</td>
</tr>
<tr>
<td valign="top">

MAX\_COMPACTION\_RESULT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the largest compaction result in bytes. This is the difference of allocated bytes before and after compaction and may be influenced by other factors than compaction.

</td>
</tr>
<tr>
<td valign="top">

MIN\_COMPACTION\_RESULT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the smallest compaction result in bytes. This is the difference of allocated bytes before and after compaction and may be influenced by other factors than compaction.

</td>
</tr>
<tr>
<td valign="top">

SUM\_COMPACTION\_RESULT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total of all compaction results in bytes. This is the difference of allocated bytes before and after compaction and may be influenced by other factors than compaction.

</td>
</tr>
<tr>
<td valign="top">

AVG\_COMPACTION\_RESULT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average compaction result in bytes. This is the difference of allocated bytes before and after compaction and may be influenced by other factors than compaction.

</td>
</tr>
</table>



<a name="loio20ab00a275191014a1c7a1c04a7547e6___m__c_o_m_p_a_c_t_i_o_n__t_h_r_e_a_d_1fulldesc_M_COMPACTION_THREAD"/>

## Additional Information

The compaction thread automatically calls for memory reduction \(including for the resource container\) if memory gets low, but is not already exhausted. The compaction thread also executes the memory reduction requests triggered by other processes \(inter-process memory management\). This view displays some information about the compaction requests and the compacted sizes.

