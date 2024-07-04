<!-- loio20ab2f6975191014991e8932eb507b8f -->

# M\_CONDITIONAL\_VARIABLES System View

Provides semaphore statistics.



<a name="loio20ab2f6975191014991e8932eb507b8f___m__c_o_n_d_i_t_i_o_n_a_l__v_a_r_i_a_b_l_e_s_1struct_M_CONDITIONAL_VARIABLES"/>

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

Displays the persistence volume ID.

</td>
</tr>
<tr>
<td valign="top">

STATISTICS\_NAME

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the statistics object name.

</td>
</tr>
<tr>
<td valign="top">

STATISTICS\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the statistics object unique ID.

</td>
</tr>
<tr>
<td valign="top">

WAIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of wait calls.

</td>
</tr>
<tr>
<td valign="top">

BLOCKING\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of blocking wait calls.

</td>
</tr>
<tr>
<td valign="top">

TIMEOUT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of timeouts.

</td>
</tr>
<tr>
<td valign="top">

WAIT\_RATE

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the wait rate percentage.

</td>
</tr>
<tr>
<td valign="top">

LAST\_BLOCKING\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the latest time of blocking wait calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_BLOCKING\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time of blocking wait calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_BLOCKING\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time of blocking wait calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

SUM\_BLOCKING\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total time of blocking wait calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_BLOCKING\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time of blocking wait calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of semaphore creations \(for shared statistics only\).

</td>
</tr>
<tr>
<td valign="top">

DESTROY\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of semaphore destructions \(for shared statistics only\).

</td>
</tr>
<tr>
<td valign="top">

COMPONENT

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the component.

</td>
</tr>
</table>



<a name="loio20ab2f6975191014991e8932eb507b8f__section_sqw_zcw_rbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.



<a name="loio20ab2f6975191014991e8932eb507b8f___m__c_o_n_d_i_t_i_o_n_a_l__v_a_r_i_a_b_l_e_s_1fulldesc_M_CONDITIONAL_VARIABLES"/>

## Additional Information

This view contains information about single conditional variable objects or groups of conditional variable objects. It does not contain information about all conditional variables.

**Related Information**  


[M\_CONDITIONAL\_VARIABLES\_RESET System View](m-conditional-variables-reset-system-view-20ab646.md "Semaphore statistics (since last reset) .")

[Conditional Breakpoints](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/d68d243f71fa476787d5b5aa97fd9377.html "") :arrow_upper_right:

[Session Variables](../../010-SQL-Reference/session-variables-a16678c.md " 		 		 		 		 		 		 	")

[Conditionals](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/46e875a0d4e446ae9ab08334f13cd1aa.html "") :arrow_upper_right:

[DECLARE CONDITION](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/47eb720aed594810b8afb2885e2fa9e4.html "") :arrow_upper_right:

[Scalar Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/66b38a60ab3b475f925c224038511c51.html "") :arrow_upper_right:

[Referencing Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/605b30ed9df54f1bafb7402a4f3b77b8.html "") :arrow_upper_right:

[Table Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/c8a483c3fcc94c0ca390bd1a8776d081.html "") :arrow_upper_right:

[System Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/69e4f60575484d98a568f59e592a61bb.html "") :arrow_upper_right:

[SQL DML Statements on Table Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/226f2125b7ed4f4aabe731cfed029d7b.html "") :arrow_upper_right:

[Table Variable Type Definition](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/ea5065d06d14426799d879234d8e3e7b.html "") :arrow_upper_right:

[Array Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/cba8ef91ba944e37beb26eb8bd995c2f.html "") :arrow_upper_right:

[Global Session Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/aaef0b96852a4e1d9ce2570bbb1493c9.html "") :arrow_upper_right:

[Row-Type Variable](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/869b4b1c5c7847cba246eb8e210d72bb.html "You can declare a row-type variable, which is a collection of scalar data types, and use it to easily fetch a single row from a table.") :arrow_upper_right:

[Redirect Results to a File](https://help.sap.com/viewer/f1b440ded6144a54ada97ff95dac7adf/LATEST/en-US/18ce51f468bc4cfe9112e6be79953e93.html)

