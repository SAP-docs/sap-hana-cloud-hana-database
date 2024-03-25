<!-- loiobb9788e077bc474894a040970d4be097 -->

# Assign HDI-Container Roles to a Selected User or Role

Assign an HDI container role to a selected user or user role.



<a name="loiobb9788e077bc474894a040970d4be097__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project you created in the previous tutorial is available.
-   The application project contains a database module called *db*.



<a name="loiobb9788e077bc474894a040970d4be097__context_tqr_wr1_d1c"/>

## Context

The SAP HANA Native Application extension's project explorer provides a Wizard that guides you through the process of assigning a role to a selected user or user role in an HDI container. This is useful if, for example, a dedicated database user \(or user role\) needs the privileges already defined in an exisiting role.

To assign an HDI-container role to a specific user or user role, perform the following steps:



<a name="loiobb9788e077bc474894a040970d4be097__steps_uqr_wr1_d1c"/>

## Procedure

1.  Open the SAP HANA project explorer in SAP Business Application Studio.

    In the SAP HANA project explorer, locate the application database module \(`db`\) that is bound to the HDI container that you want to enable additional users or roles to access, for example, *FlightReservation/db*.

2.  Start the grant-HDI-roles Wizard.

    In the SAP HANA project explorer, right click the application's database module, for example, *MyApp/db* and choose *Grant HDI container roles* in the context menu.

3.  Select the type of grantee requiring the privileges defined in the HDI container role.

    You can choose to grant the HDI container role either to another user or to a user role.

4.  Define details of the grantee.

    You must specify the name of the user \(or user role\) to whom you want to grant the container roles in the target HDI container.

    > ### Tip:  
    > If you select a role as a grantee, you can also specify the name of the schema where the HDI container role is located.

5.  Choose the HDI-container role to grant to the target user or role.

    To specify which role you want to assign to the grantee, use the check-list provided. You can specify multiple roles.

6.  Save the changes.

    Choose *Grant* to assign the selected HDI container role to the specified user or user role.

7.  Check that the selected role was successfully granted to the specified user or user role.

    You can use the following methods to check assigned HDI-container roles:

    *SAP BTP Cockpit* provides the *Privilege Assignment* and *Role Management* tools, which you can use to confirm that the selected privileges have been assigned to the specified user or user role, respectively. The privileges are displayed in the *Object Privileges* tab. For more information about using these tools, see *User and Role Management* in *Related Information* below.

    > ### Tip:  
    > The HDI container view `M_GRANTED_SCHEMA_PRIVILEGES` can also be used to display the schema privileges granted to any users or any role that is not deployed to the specified container. For more information, see *Related Information* below.


**Related Information**  


[Grant HDI-Container Schema Privileges to a Selected User or User Role](grant-hdi-container-schema-privileges-to-a-selected-user-or-user-role-7ecd0ce.md "Configure access to the schema of an HDI container for selected users or user roles.")

