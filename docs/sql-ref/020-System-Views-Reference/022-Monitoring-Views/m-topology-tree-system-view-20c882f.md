<!-- loio20c882f975191014af059f9ee0f0a2e5 -->

# M\_TOPOLOGY\_TREE System View

Provides information about SAP HANA nameserver topology content.



<a name="loio20c882f975191014af059f9ee0f0a2e5___m__t_o_p_o_l_o_g_y__t_r_e_e_1struct_M_TOPOLOGY_TREE"/>

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

PATH



</td>
<td valign="top">

NVARCHAR\(1024\)



</td>
<td valign="top">

Displays the path to the key.



</td>
</tr>
<tr>
<td valign="top">

NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the key name.



</td>
</tr>
<tr>
<td valign="top">

VALUE



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the key value.



</td>
</tr>
<tr>
<td valign="top">

LEAF



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays the leaf flag: TRUE/FALSE.



</td>
</tr>
</table>



<a name="loio20c882f975191014af059f9ee0f0a2e5___m__t_o_p_o_l_o_g_y__t_r_e_e_1fulldesc_M_TOPOLOGY_TREE"/>

## Additional Information

Use '/' as the root path. For deeper paths, use PATH+'/'+NAME. If NAME contains '/', then you must enclose it in CHR\(1\), For example:

```
SELECT * FROM M_TOPOLOGY_TREE WHERE PATH='/index/'||CHR(1)||'SYSTEM:A/B'||CHR(1)||'#15046'
```

To change topology tree values, use ALTER SYSTEM ALTER CONFIGURATION \('topology.ini','system'\) SET \(PATH,NAME\)=VALUE.

To delete values use ALTER SYSTEM ALTER CONFIGURATION \('topology.ini','system'\) UNSET \(PATH,NAME\).

**Related Information**  


[Partitioning Consistency Checks](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/7b1e7a1577cc4e05bb4c05b4189c5b2f.html "A number of table consistency checks are available to check the validity of partitioned tables.") :arrow_upper_right:

