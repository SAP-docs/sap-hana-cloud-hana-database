<!-- loio0ba5fa2968cc4503b3aef32748ed9470 -->

# Data Storage Security in SAP HDI

Security mechanisms are applied to protect critical data managed by the SAP HDI.

Since SAP HDI is a service layer on top of the SAP HANA database, it adheres to all the rules and regulations that apply to the SAP HANA database itself and described in detail in the *Data Storage Security in SAP HANA* section of the *SAP HANA Security Guide*.

Database objects \(tables, views, procedures, and so on\) have an owner: the user who created the object. When the owner of a database object is deleted, all objects owned by the deleted user are removed from the database, too. In addition, if application objects are created by end-users, the objects are deleted when the end-user is deleted, for example when the employee leaves the organization. HDI ensures that during deployment all database objects are created by a container-specific **technical user**, which is never deleted as long as the container exists.

**Related Information**  


[SAP HDI Security](sap-hdi-security-d9e5051.md "An overview of the tools used to configure and ensure security in the SAP HANA Deployment Infrastructure (HDI).")

[SAP HANA Cloud, SAP HANA Database Security Guide](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_2_QRC/en-US/c3d9889e3c9843bdb834e9eb56f1b041.html#loioc3d9889e3c9843bdb834e9eb56f1b041 "The SAP HANA Cloud, SAP HANA Database Security Guide is the entry point for all information relating to the secure operation and configuration of SAP HANA Cloud, SAP HANA database.") :arrow_upper_right:

