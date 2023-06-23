<!-- loio20b6e99275191014a861df9fb6abb5f5 -->

# M\_PASSWORD\_POLICY System View

Defines effective password policy settings.



<a name="loio20b6e99275191014a861df9fb6abb5f5___m__p_a_s_s_w_o_r_d__p_o_l_i_c_y_1struct_M_PASSWORD_POLICY"/>

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

PROPERTY



</td>
<td valign="top">

NVARCHAR\(128\)



</td>
<td valign="top">

Displays the configuration property. The following describes the contents of the individual lines of the monitor view \(***VALUE***\), as identified by ***PROPERTY***:


<dl>
<dt><b>

force\_first\_password\_change

</b></dt>
<dd>

Displays if a user is forced to change their administrator-given password before being allowed to work any further. This property is only applicable to users connecting using their SAP HANA database user name and password.



</dd><dt><b>

last\_used\_passwords

</b></dt>
<dd>

Displays the number of recently used passwords of a user, which they cannot reuse.



</dd><dt><b>

maximum\_invalid\_connect\_attempts

</b></dt>
<dd>

Displays the maximum number of allowed invalid connect attempts before a user is locked out.



</dd><dt><b>

maximum\_password\_lifetime

</b></dt>
<dd>

Displays the number of days that a password stays valid.



</dd><dt><b>

maximum\_unused\_initial\_password\_lifetime

</b></dt>
<dd>

Displays the number of days that an unused administrator-given password stays valid.

> ### Note:  
> In SAP HANA 1.0 SP 12 and earlier, the parameter name is `maximum_unused_initial_password_lifetime` \(note the missing 'i' in 'initial'\). Use of the previous spelling is supported, but it is recommended that you update your configuration to use the correct spelling.



</dd><dt><b>

maximum\_unused\_productive\_password\_lifetime

</b></dt>
<dd>

Displays the number of days that an unused user-given password stays valid.



</dd><dt><b>

minimal\_password\_length

</b></dt>
<dd>

Displays the minimum number of characters required by a valid password.



</dd><dt><b>

minimum\_password\_lifetime

</b></dt>
<dd>

Displays the minimum number of days before a user-given password can be changed by that user.



</dd><dt><b>

password\_expire\_warning\_time

</b></dt>
<dd>

Displays that warnings about nearly expired passwords are shown at the configured number of days before expiration.



</dd><dt><b>

password\_layout

</b></dt>
<dd>

Describes the kind\(s\) of characters that the password must consist of.



</dd><dt><b>

password\_lock\_time

</b></dt>
<dd>

Displays the number of minutes the user is locked out after too many invalid connect attempts.



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

VALUE



</td>
<td valign="top">

NVARCHAR\(128\)



</td>
<td valign="top">

Displays the value.



</td>
</tr>
</table>

**Related Information**  


[Password Policy Configuration Options](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/61662e3032ad4f8dbdb5063a21a7d706.html "The password policy of the database is defined by parameters in the password policy section of the indexserver.ini configuration file. The initial password policy of a user group is a copy of the database password policy.") :arrow_upper_right:

[CREATE USERGROUP Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-usergroup-statement-access-control-9869125.md "Creates a usergroup.")

[ALTER USERGROUP Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-usergroup-statement-access-control-aa94ca8.md "Alters a usergroup.")

[M\_EFFECTIVE\_PASSWORD\_POLICY System View](m-effective-password-policy-system-view-388378c.md "Provides information about password policy parameters for database users.")

