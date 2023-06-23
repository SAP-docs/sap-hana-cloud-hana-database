<!-- loio3c006c5ca4844314a233d9c8d03f1a14 -->

# Network and Communication Security with SAP HDI

An overview of the security mechanisms applied to networking and communication in the context of SAP HDI.

Security mechanisms are applied to protect the communication paths used by the SAP HANA Deployment Infrastructure \(HDI\). SAP provides network topology recommendations that enable administrators to restrict access at the network level.

The JDBC connection to the SAP HANA database is not encrypted by default. To activate JDBC TLS/SSL, it is necessary to configure custom SSL certificates as described in *SAP HDI Certificate Management* below.



<a name="loio3c006c5ca4844314a233d9c8d03f1a14__section_n5z_5ns_ngb"/>

## SAP HDI Certificate Management

The HDI administrator is responsible for the certificate management in the SAP HANA JDBC area. The SAP HDI does not encrypt the JDBC connections to SAP HANA out of the box. Therefore, custom certificates must be configured, which involves the following high-level steps:

-   Deploy the custom certificate in the SAP HANA database in order to provide the certificate to all index server instances

-   Publish of the certificate to the SAP HDI server components

-   Enable the JDBC SSL in the platform settings and restart the system


**Related Information**  


[SAP HDI Security](sap-hdi-security-d9e5051.md "An overview of the tools used to configure and ensure security in the SAP HANA Deployment Infrastructure (HDI).")

