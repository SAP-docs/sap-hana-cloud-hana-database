<!-- loiobcd6e27173464d9eb6a5ff9e53275240 -->

# Maintaining SAP HDI Containers

An HDI container administrator configures and controls access to a SAP HDI container.

The SAP HANA Deployment Infrastructure \(HDI\) provides a service that enables you to deploy database development artifacts to so-called containers. This service includes a family of consistent design-time artifacts for all key SAP HANA platform database features which describe the target \(run-time\) state of SAP HANA database artifacts, for example: tables, views, or procedures. These artifacts are modeled, staged \(uploaded\), built, and deployed into SAP HANA.

The SAP HANA service broker is used to create and destroy HDI containers; each HDI container comprises a design-time container \(DTC\), which is an isolated environment used to store design-time files, and a run-time container \(RTC\), which is used to store deployed objects built according to the specification stored in the corresponding design-time artifacts.

The deployment process populates the database run-time with the specified catalog objects. In addition to database artifacts, HDI also enables you to import and export table content such as business configuration data and translatable texts.

> ### Restriction:  
> HDI enables you to deploy database objects only; it is not possible \(or necessary\) to deploy application-layer artifacts such as JavaScript programs or OData objects.

The HDI container administrator manages one or more containers assigned by the container-group administrator. The role of the container-manager focuses primarily on configuring and controlling access to the HDI containers used to store the database objects deployed by the SAP HANA Deployment Infrastructure deploy service and repairing any problems that occur with run-time objects in the assigned HDI containers. An HDI container administrator can manage one or more containers in one HDI container group or multiple containers distributed across multiple container groups.

The configuration of HDI containers also involves the creation and configuration of the following design-time artifacts:

-   Container deployment configuration \(`.hdiconfig`\)

    A JSON file containing a list of the bindings between database artifact types \(for example, sequence, procedure, table\) and the corresponding deployment plug-in \(and version\).

-   Run-time container namespace rules \(`.hdinamespace`\)

    A JSON file containing a list of design-time file suffixes and the naming rules for the corresponding run-time locations.


> ### Tip:  
> The APIs of a container named “C” are in the schema `C#DI`.



<a name="loiobcd6e27173464d9eb6a5ff9e53275240__section_vxh_nz3_p2b"/>

## HDI-Container Maintenance Tasks

To manage an HDI container group, the administrator performs the following common tasks:

-   Grant and revoke container administrator privileges

-   Grant and revoke access to the container development API

-   Grant and revoke access to a container's schema

-   Grant and revoke a user role from the container's schema

-   List all currently configured build plug-in libraries available to a container

-   Configure the default set of build plug-in libraries available to a container

-   Configure a custom set of build plug-in libraries available to a container

-   Configure container parameters


**Related Information**  


[Maintaining SAP HDI Container Groups](../14-HDI-Cloud-Admin-Maintain-Container-Groups/maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Maintaining the SAP HDI](../13-HDI-Cloud-Admin-Maintain-HDI/maintaining-the-sap-hdi-df043e3.md "Maintenance of the SAP HANA Deployment infrastructure (HDI) is the responsibility of the HDI administrator, who must set up and configure general HDI parameters.")

[SAP HANA Deployment Infrastructure in the Cloud](../../sap-hana-deployment-infrastructure-in-the-cloud-3ef0ee9.md "Understand the benefits of using the SAP HANA Deployment Infrastructure (HDI).")

