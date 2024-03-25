<!-- loio5316825b47dd4ab3acebea6bd7e47fdf -->

# Revoke Access to an SAP HDI Container from a Support User

Revoke any privileges granted to members of the support teams for temporary access to SAP HDI containers.



<a name="loio5316825b47dd4ab3acebea6bd7e47fdf__context_xhp_2zx_k1b"/>

## Context

In the event of container-related problems in SAP HANA Deployment Infrastructure \(HDI\), it might be necessary for a support user to access HDI-internal objects in a container API schema, for example, <code><i class="varname">&lt;container_name&gt;</i>#DI</code> for the container *<container\_group\_name\>*. These privileges must be temporarily granted to an explicit support user and then revoked when the support task is completed.



<a name="loio5316825b47dd4ab3acebea6bd7e47fdf__steps_yhp_2zx_k1b"/>

## Procedure

1.  In an SQL console, connect to the database with the administrator of the HDI container group *<container\_group\_name\>*.

2.  Open the SQL editor for this database.

3.  Insert the following SQL code into the editor:

    > ### Sample Code:  
    > ```sql
    > CALL _SYS_DI#<container_group_name>.REVOKE_CONTAINER_SUPPORT_PRIVILEGE( '<container_group_name>', 'SELECT', '<CONTAINER_SUPPORT_USER>', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > ```

    1.  Replace *<container\_group\_name\>* with the name of the container group in which the target HDI container is located.

    2.  Replace *<container\_name\>* with the name of the target container.

    3.  Adjust the privilege as needed.

        Possible values are `SELECT`, `UPDATE`, `INSERT`, and `DELETE`.

    4.  Replace <code><i class="varname">&lt;CONTAINER_SUPPORT_USER&gt;</i></code> with the name of the support user from whom you want to revoke container-access privileges.


4.  Execute the SQL code.

5.  \(Optional\) Confirm that the<code><i class="varname">&lt;CONTAINER_SUPPORT_USER&gt;</i></code> user can no longer access objects in the container *<container\_name\>*'s API schema <code><i class="varname">&lt;container_group_name&gt;</i>#DI</code> according to the revoked privileges.


**Related Information**  


[Maintaining SAP HDI Container Groups](maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Grant a Support User Access to an SAP HDI Container](grant-a-support-user-access-to-an-sap-hd-b460586.md "Provide members of the support teams with temporary access to an SAP HDI container.")

