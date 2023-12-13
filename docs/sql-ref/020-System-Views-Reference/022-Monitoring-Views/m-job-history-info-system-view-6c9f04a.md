<!-- loio6c9f04ab558e4f2b837e640568498508 -->

# M\_JOB\_HISTORY\_INFO System View

Provides a history of long running system operations.



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

JOB\_NAME

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the type of operation.

</td>
</tr>
<tr>
<td valign="top">

DESCRIPTION

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the job description.

</td>
</tr>
<tr>
<td valign="top">

DISPLAY\_NAME

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the recommended display name.

</td>
</tr>
<tr>
<td valign="top">

DISPLAY\_LINE\_COLOR

</td>
<td valign="top">

INTEGER\(10\)

</td>
<td valign="top">

Displays the recommended display line color as RGB.

</td>
</tr>
<tr>
<td valign="top">

DISPLAY\_LINE\_STYLE

</td>
<td valign="top">

TINYINT\(3\)

</td>
<td valign="top">

Displays the recommended display line style: 1=solid, 2=dotted, 3=dashed.

</td>
</tr>
</table>

**Related Information**  


[M\_JOB\_PROGRESS System View](m-job-progress-system-view-20b1b23.md "Provides information about current long running system operations.")

