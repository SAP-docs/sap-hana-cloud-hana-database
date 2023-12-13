<!-- loio3ef0ee9da11440e4b01708455b8497a9 -->

# SAP HANA Deployment Infrastructure in the Cloud

Understand the benefits of using the SAP HANA Deployment Infrastructure \(HDI\).

The SAP HANA Deployment Infrastructure, or HDI for short, provides a service that enables you to deploy database development artifacts to so-called containers. This service includes a family of consistent design-time artifacts for all key SAP HANA platform database features which describe the target \(run-time\) state of SAP HANA database artifacts, for example: tables, views, or procedures. These artifacts are modeled, staged \(uploaded\), built, and deployed into SAP HANA.

> ### Restriction:  
> The HDI focuses strictly on deployment; HDI does not include any version-control tools, nor does it provide any tools for life-cycle management.

HDI provides its services using a separate database process named `diserver`, which in the context of SAP HANA Cloud is enabled by default. On systems where HDI is not already enabled, the `diserver` process must usually be enabled by the database administrator before HDI can be used. If required by the usage scenario, other database process may also need to be started as well.

> ### Restriction:  
> HDI enables you to deploy database objects only; it is not possible \(or necessary\) to use HDI to deploy application-layer artifacts such as JavaScript programs or OData objects.

The System administrator is responsible for the one-time enabling of HDI, and HDI administrators are responsible for the subsequent regular maintenance tasks,which typically involve using the HDI SQL APIs. For example, an HDI administrator configures HDI, creates HDI container groups, and grants and revokes the access privileges required by HDI container-group administrators. The HDI container-group administrator can drop and create HDI containers, and grant or revoke container \(and container-group\) access privileges. HDI container administrators grant and revoke container-based access privileges, configure build plug-in libraries and general parameters, and grant and revoke access to an HDI container's schemas. Content developers with the required access permissions can deploy content to the HDI containers using the HDI container APIs, for example, `WRITE` and `MAKE`.

The configuration of HDI containers also involves the creation and configuration of the following design-time artifacts:

-   Container deployment configuration \(`.hdiconfig`\)

    A JSON file containing a list of the bindings between design-time database artifact types \(for example, sequence, procedure, table, or view\) and the corresponding plug in \(and version\) required to build and deploy the artifacts to the target run-time environment.

-   Run-time container name-space rules \(`.hdinamespace`\)

    An **optional** JSON file containing a list of design-time file suffixes and the naming rules for the corresponding run-time locations. The name-space settings can be configured to **ignore** the folder name or **append** it to the name space. For more information about name-space configuration rules, see *Run-time Name Spaces in SAP HDI* in *Related Information* below.


> ### Tip:  
> The rules defined in either the `.hdiconfig` or `.hdinamespace` configuration file apply to the folder in which the configuration file resides and all subfolders unless another configuration file is found that defines new rules for the subfolder in which the additional configuration file is located and all its subfolders.

**Related Information**  


[SAP HDI Administration](10-HDI-Cloud-Administration/sap-hdi-administration-b36b4b6.md "An overview of the scope of the tasks required to maintain the SAP HANA Deployment Infrastructure (HDI).")

[Content Development in SAP HDI](20-HDI-Cloud-Content-Development/content-development-in-sap-hdi-4559e00.md "Develop and deploy database content in the SAP HANA Deployment Infrastructure (HDI).")

[The HDI Container Configuration File](20-HDI-Cloud-Content-Development/the-sap-hdi-container-configuration-file-6400400.md "Bind design-time file types to the corresponding build plug-in required in the SAP HANA Deployment Infrastructure (HDI).")

[The HDI Name-Space Configuration File](20-HDI-Cloud-Content-Development/the-hdi-name-space-configuration-file-6188d22.md "The SAP HANA Deployment Infrastructure (HDI) uses a JSON resource to define naming rules for run-time objects.")

[Run-Time Name Spaces in SAP HDI](20-HDI-Cloud-Content-Development/run-time-name-spaces-in-sap-hdi-a53bf96.md "SAP HDI defines a strict separation between the naming of run-time objects and the organization of design-time files.")

