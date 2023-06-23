<!-- loio20cc29b0751910149c6da55983753a8a -->

# PRIVILEGES System View

Provides information about available privileges.



<a name="loio20cc29b0751910149c6da55983753a8a___p_r_i_v_i_l_e_g_e_s_1struct_PRIVILEGES"/>

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

NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the privilege name.



</td>
</tr>
<tr>
<td valign="top">

TYPE



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the privilege type: SYSTEMPRIVILEGE, OBJECTPRIVILEGE, PACKAGEPRIVILEGE, or APPLICATIONPRIVILEGE



</td>
</tr>
</table>

**Related Information**  


[Privileges](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/fb0f9b103d6940f28f3479b533c351e9.html "Several privilege types are used in SAP HANA (system, object, and analytic).") :arrow_upper_right:

[Object Privileges](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/d6311b15a7e74e01b3f660f7d175b318.html "Object privileges are SQL privileges that are used to allow access to and modification of database objects.") :arrow_upper_right:

[System Privileges](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/cadbcfc38b084808b80b3551b1cd756e.html "System privileges control general system activities.") :arrow_upper_right:

[Analytic Privileges](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/db08ea0cbb571014a386f851122958b2.html "Analytic privileges grant different users access to different portions of data in the same view based on their business role. Within the definition of an analytic privilege, the conditions that control which data users see is defined using SQL.") :arrow_upper_right:

[Managing User Privileges](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/20fc276e8f22423fb6eba66f03f541e1.html "Various privileges are required to manage remote sources, virtual tables, and linked database.") :arrow_upper_right:

[GRANTED\_PRIVILEGES System View](granted-privileges-system-view-20a5958.md "Provides information about privileges and roles granted to users.")

[OBJECT\_PRIVILEGES System View](object-privileges-system-view-47764eb.md "Provides information about the types of objects and privileges that can be granted to those types of objects.")

[GRANT Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md "Grants various types of privileges to users and roles.")

[SQLSCRIPT_LOGGING Privilege](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/804d96051c14464d8596d2aa9b5ca3c6.html "") :arrow_upper_right:

