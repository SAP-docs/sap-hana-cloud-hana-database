<!-- loio23f1f40731504e7eb7e4ec4b65cbfa71 -->

# Managing SAP HDI Containers and Artifacts

In SAP HANA Deployment Infrastructure \(HDI\), database development artifacts are deployed to so-called containers.

SAP HDI provides a service that enables you to deploy database development artifacts to HDI containers. This service includes a family of consistent design-time artifacts for all key SAP HANA platform database features which describe the target \(run-time\) state of SAP HANA database artifacts, for example: tables, views, or procedures. These artifacts are modeled, staged \(uploaded\), built, and deployed into SAP HANA.

> ### Note:  
> The HDI focuses strictly on deployment; HDI does not include any version-control tools, nor does it provide any tools for life-cycle management.

For pure HDI content development, the HDI SQL APIs also enable the maintenance and management of HDI containers and the creation of content in the containers.

The HDI deployment tools deploy database artifacts to an HDI container. Each HDI container comprises a design-time container \(DTC\) and a run-time container \(RTC\). Design-time database objects are typically located in the `db` folder of the application's design-time hierarchy, as illustrated in the following example:

> ### Output Code:  
> ```
> app1-hello-world
> |- db
>    \- src
>       |- .hdiconfig                       # HDI build-plugin configuration
>       |- .hdinamespace                    # Run-time name-space configuration
>       |- myTable.hdbtable                 # DB table definition
>       |- mySQLView.hdbview                # SQL view definition
>       |- mySynonym.hdbsynonym             # DB synonym definition
>       |- mySynoConfig.hdbsynonymconfig    # DB synonym configuration file
>       |- myProcedure.hdbprocedure         # DB procedure definition
>       \- myImportData.hdbtabledata        # Data-import definition
> ```

The build-and-make process in HDI API enable you to populate the database run-time with the specified catalog objects. In addition to database artifacts, HDI also enables you to import and export table content such as business configuration data and translatable texts.

> ### Restriction:  
> HDI enables you to deploy database objects only; it is not possible \(or necessary\) to deploy application-layer artifacts such as JavaScript programs or OData objects.

As part of the maintenance and management of containers, system administrators typically perform the following operations:

-   Configure access to the SAP HANA Deployment Infrastructure \(including containers\)

-   Create and remove HDI containers, each consisting of both a design-time and a run-time container


The configuration of HDI containers involves the creation and configuration of the following design-time artifacts:

-   Container deployment configuration \(`.hdiconfig`\)

    A JSON file containing a list of the bindings between database artifact types \(for example, sequence, procedure, table\) and the corresponding build and deployment plug-in \(and version\).

-   Run-time container name-space rules \(`.hdinamespace`\)

    A JSON file containing a list of design-time file suffixes and the naming rules for the corresponding runtime locations.

    > ### Tip:  
    > You can apply the rules defined in the `.hdinamespace` file either exclusively to the folder it is located in or to both the folder it is located in **and** its subfolders.


**Related Information**  


[SAP HDI Containers](sap-hdi-containers-e28abca.md "An SAP HANA HDI container consists of a design-time container and a corresponding run-time container.")

[SAP HDI Container Content Development with the HDI API](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_4_QRC/en-US/bea716c9ad68444ca63485e3f92d6589.html "SAP HDI includes an SQL API for the development of content in SAP HDI containers.") :arrow_upper_right:

