<!-- loio7ecd0ce9b48c4f10ad480cd5da1ac8fb -->

# Grant HDI-Container Schema Privileges to a Selected User or User Role

Configure access to the schema of an HDI container for selected users or user roles.



<a name="loio7ecd0ce9b48c4f10ad480cd5da1ac8fb__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project you created in the previous tutorial is available.
-   The application project contains a database module called *db*.



## Context

The SAP HANA Native Application extension's project explorer provides a Wizard that guides you through the process of granting a selected user or user role the privileges required to access an HDI container's schema. This is useful when, for example, you already have a dedicated database user with a set of privileges that you now want to use to check if a calculation view is being correctly executed in a particular HDI container. The dedicated database user needs privileges on the HDI container in order to be able access the calculation view, and these privileges can be granted by using the privilege-assignment Wizard.

A user may also want to grant access to an HDI container to enable another developer to check some issues or to provided temporary access to the development container to check whether an object hierarchy will work in production.

To grant HDI-container schema privileges to a specific user or user role, perform the following steps:



## Procedure

1.  Open the SAP HANA project explorer in SAP Business Application Studio.

    In the SAP HANA project explorer, locate the application database module \(`db`\) that is bound to the HDI container that you want to enable additional users or roles to access, for example, *FlightReservation/db*.

2.  Start the grant-HDI-privileges Wizard.

    In the SAP HANA project explorer, right click the application's database module, for example, *MyApp/db* and choose *Grant HDI container privileges* in the context menu.

3.  Select the type of grantee who requires access to the HDI container.

    You can grant the schema privileges to either a user or a user role.

4.  Define details of the grantee.

    You must specify the name of the user \(or user role\) to whom you want to grant schema privileges in the target HDI container.

    > ### Tip:  
    > If you select a role as a grantee, you need to provide the name of the schema where the user role is located.

5.  Choose the privileges to grant to the target user or role.

    To specify which privileges you want to assign to the target grantee, use the check-list provided.

    > ### Caution:  
    > It is recommended to restrict the granted privileges to the minimum required to ensure that the target grantee can perform the tasks required.

6.  Save the changes.

    Choose *Grant* to assign the selected privileges to the specified user or role.

7.  Check that the selected privileges were successful granted to the selected user or user role.

    *SAP BTP Cockpit* provides the *Privilege Assignment* and *Role Management* tools, which you can use to confirm that the selected privileges have been assigned to the specified user or user role, respectively. The privileges are displayed in the *Object Privileges* tab. For more information about using these tools, see *User and Role Management* in *Related Information* below.

    > ### Tip:  
    > The HDI container view `M_GRANTED_SCHEMA_PRIVILEGES` can also be used to display the schema privileges granted to any users or any role that is not deployed to the specified container. For more information, see *Related Information* below.


**Related Information**  


[Create an HDI-Container Service Instance](create-an-hdi-container-service-instance-7074c22.md "Create a new instance of an HDI container service.")

[Export an SAP HDI Container for Support Purposes](export-an-sap-hdi-container-for-support-purposes-0e4c340.md "An HDI container administrator or database administrator can export an HDI container to a table or a file.")

[User and Role Management \(SAP HANA Cloud Database Administration Guide for SAP HANA Cockpit\)](https://help.sap.com/docs/HANA_CLOUD/9630e508caef4578b34db22014998dba/923b896cabdb415487919f28dbbc4bfd.html)

[M\_GRANTED\_SCHEMA\_PRIVILEGES View \(SAP HANA Cloud HDI Reference\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/c2cc2e43458d4abda6788049c58143dc/77bf987f41824d2ba02ccb055d4461b6.html)

