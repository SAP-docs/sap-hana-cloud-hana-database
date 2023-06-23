<!-- loioc248d55857a14ab0b14a2f7a04d6dcf4 -->

# Enabling the SAP HDI Administrators

Create the users required to adminstrate and maintain the SAP HANA Deployment Infrastructure \(HDI\) services.

SAP HDI provides its services using a separate database process, `diserver`. HDI is enabled by default in the database of your SAP HANA Cloud instance.

Enabling HDI administrator users typically involves the following tasks:

-   Create an HDI administrator

-   Revoke HDI administrator privileges


> ### Note:  
> The `DBADMIN` user is required to create an initial HDI administrator, who can then configure HDI and create additional HDI administrators if required. If the `DBADMIN` user is deactivated \(recommended\), you will need to reactivate it temporarily to create the first HDI administrator, for example, with the SQL statement: `ALTER USER DBADMIN ACTIVATE USER NOW`. After you have completed these HDI user setup, you can deactivate the `DBADMIN` user again and use the newly created HDI administrator user to perform further HDI-related setup tasks.

**Related Information**  


[Create an SAP HDI Administrator](create-an-sap-hdi-administrator-9a6bf8d.md "The HDI administrator is responsible for configuring general SAP HDI parameters, creating and dropping HDI container groups, moving HDI containers between groups, and managing the privileges of HDI container-group administrators.")

[Revoke the SAP HDI Administrator Privileges](revoke-the-sap-hdi-administrator-privileges-84b472a.md "Revoke the SAP HDI administrator privileges from a specified user.")

