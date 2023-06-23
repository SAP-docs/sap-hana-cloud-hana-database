<!-- loioacd0ac9f709247068dbe72b52d1f6a34 -->

# VIRTUAL\_PROCEDURES System View

Provides the list of virtual procedures.



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

Displays the schema name of the virtual procedure.



</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the virtual procedure.



</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the object ID of the virtual procedure.



</td>
</tr>
<tr>
<td valign="top">

REMOTE\_SOURCE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the remote source name used in the procedure.



</td>
</tr>
<tr>
<td valign="top">

ADAPTER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the remote source adapter.



</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_CONFIGURATION



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the virtual procedure configuration.



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

Displays whether the virtual procedure is valid: TRUE/FALSE.



</td>
</tr>
</table>

**Related Information**  


[Procedures](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/d43d91578c3b42b3bacfd89aacf0d62f.html "") :arrow_upper_right:

