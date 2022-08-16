<!-- loioe28abca91a004683845805efc2bf967c -->

# SAP HDI Containers

An SAP HANA HDI container consists of a design-time container and a corresponding run-time container.

The SAP HANA Deployment Infrastructure \(HDI\) uses so-called containers to store design-time artifacts and the corresponding deployed run-time \(catalog\) objects. The HDI makes a strict separation between design-time and run-time objects by introducing the following, distinct container types:

-   **Design-time** container \(DTC\)

    Provides an isolated environment for the storage of design-time files

-   **Run-time** container \(RTC\)

    Stores the deployed objects built according to the specification stored in the corresponding design-time artifacts


> ### Tip:  
> HDI uses so-called build plug-ins to create run-time objects from the corresponding design-time files, for example, a procedure object in the database catalog from a design-time definition of a stored procedure.



## Design-Time Containers

In SAP HDI, the design-time container is used to store the design-time representations of the catalog objects that you want to create during the deployment process. The design-time container does not provide direct access to its database storage; it contains meta-data that can only be accessed by means of the HDI application-programming interface \(API\). The HDI API enables access to design-time resources inside a design-time container by means of the following file systems:

-   work

    A read-write file system where developers can create, modify, and delete design-time resources. The resources in the **work** file system are not modified by HDI, so undeploying a resource from the **deployed** file system leaves the corresponding resource in the work file system untouched. This is because deployed resources are handled by the **deployed** file system.

-   deployed 

    A read-only file system containing the design-time resources that have been **deployed**. The deployed file system can only be changed by HDI during the deployment and undeployment process.


> ### Restriction:  
> For maximum isolation and increased security, content stored in a design-time container is owned by a dedicated technical user.

Build Plug-ins are used to transform a certain type of design-time file into the corresponding run-time objects. For this reason, each design-time resource type must be mapped to a build plug-in for each container that is created. It is not possible to create a catalog object from a design-time resource without having a plug-in which can read and transform this source definition during deployment.

A design-time container is always attached to a corresponding **target** run-time container.



## Run-Time Containers

In SAP HANA, the database run-time container stores the deployed objects built according to the specification stored in the corresponding design-time artifacts. During the deployment and undeployment operations, all interaction with the run-time container is performed by build plug-ins, which are mapped to distinct design-time artifact types in the container-configuration file \(`.hdiconfig`\).

A run-time container does not know about the concept of design-time containers. As a consequence, the run-time container can be identified with a standard database schema without any need for HDI meta-data.

The creation of a run-time container results in a new technical database user and a schema with the same name as the one chosen for the name of the run-time container itself. Access to content in the run-time container is controlled by database privileges, for example, by granting SELECT or EXECUTE privileges.



## Build Plug-ins

The transformation of design-time resources into corresponding run-time \(catalog\) objects as well as the extraction of dependency information is performed by so-called build plug-ins. A newly created design-time container cannot access any plug-ins; this access must be defined in the HDI configuration file \(`.hdiconfig`\). In addition, since there is no default behavior configured, it is not possible to deploy any design-time files \(except the two HDI container-configuration and name-space configuration files `.hdiconfig` and `.hdinamespace` respectively\) without configuring a build plug-in first. To configure a design-time container to use certain build plug-ins, you must set up and deploy a `.hdiconfig` container-configuration file.

> ### Tip:  
> By default, a file suffix \(for example, `.hdbprocedure`\) is not bound to a specific version of a known build plug-in. Instead, the binding is established by the contents of the `.hdiconfig` file, which must be deployed into a container.

**Related Information**  


[The SAP HDI Container Configuration File](the-sap-hdi-container-configuration-file-6400400.md "Bind design-time file types to the corresponding build plug-in required in the SAP HANA Deployment Infrastructure (HDI).")

[Managing SAP HDI Containers and Artifacts](managing-sap-hdi-containers-and-artifacts-23f1f40.md "In SAP HANA Deployment Infrastructure (HDI), database development artifacts are deployed to so-called containers.")

