<!-- loio0853c4b8745e46e29e078f96de713844 -->

# TASK\_PARAMETERS System View

Provides task parameter information.



<a name="loio0853c4b8745e46e29e078f96de713844__section_jvp_jmk_vhb"/>

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

Displays the schema that the task was created in.



</td>
</tr>
<tr>
<td valign="top">

TASK\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the task.



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

Displays the name of the parameter.



</td>
</tr>
<tr>
<td valign="top">

POSITION



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the position of the parameter.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_TYPE\_SCHEMA



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema that the table type was created in.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_TYPE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the table type.



</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_TYPE



</td>
<td valign="top">

NVARCHAR\(7\)



</td>
<td valign="top">

Displays the parameter type: IN/OUT.



</td>
</tr>
</table>

**Related Information**  


[M\_TASKS System View](../022-Monitoring-Views/m-tasks-system-view-5c8f947.md "Provides task monitoring information.")

[START TASK Statement \[Smart Data Integration\]](https://help.sap.com/viewer/7952ef28a6914997abc01745fef1b607/latest/en-US/f78c65499ce442219b4a302f32b5138d.html)

[CANCEL TASK Statement \[Smart Data Integration\]](https://help.sap.com/viewer/7952ef28a6914997abc01745fef1b607/latest/en-US/ea04faaf80ab41c789e72d61ab8f2056.html)

[TASKS System View \[Smart Data Integration\]](https://help.sap.com/viewer/7952ef28a6914997abc01745fef1b607/latest/en-US/60bcc7bbd2ad4fc1bb803d6926b65078.html)

[TASK\_EXECUTIONS System View \[Smart Data Integration\]](https://help.sap.com/viewer/7952ef28a6914997abc01745fef1b607/latest/en-US/2f66757d38a047b793f7041f2b1f6750.html)

