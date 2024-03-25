<!-- loiof7268f176e1943ad97edba3f1dfeda26 -->

# Multitarget Application Development Tools

SAP HANA provides a selection of development and administration tools.

SAP HANA provides a selection of tools to help in the various phases of the design-time development and run-time administration of Multi-Target Applications \(MTA\):

-   [Development Tools](multitarget-application-development-tools-f7268f1.md#loiof7268f176e1943ad97edba3f1dfeda26__section_r4p_13v_rv)
-   [Administration Tools](multitarget-application-development-tools-f7268f1.md#loiof7268f176e1943ad97edba3f1dfeda26__section_o4f_b3v_rv)



<a name="loiof7268f176e1943ad97edba3f1dfeda26__section_r4p_13v_rv"/>

## Development Tools

SAP Business Application Studio is a browser-based development environment for applications developed for deployment on the Cloud Foundry run-time environment on SAP HANA Cloud; SAP Business Application Studio can be used to develop all layers of an application, including the client user interface \(UI\), multitarget applications, and SAP HANA database content. With SAP Business Application Studio you have the tools to help you carry out all parts of the application-development process, for example: editing, debugging, testing, modeling, version management, building, and deploying. SAP Business Application Studio is based on the SAP HANA Deployment Infrastructure \(HDI\) and can use Git for source-code management.

-   Code editors

    With syntax suggestions/highlights, syntax and format checking, and graphical visualization

-   Debugging tools

    Break points, pause and step-over function, call stack visualization, variable lists and values, etc.

-   Version Control tools

    Easy lifecycle management of design-time artifacts with a bundled Git client and a special integration with Gerrit

-   Code visualization tools

    Display an outline of your code for easier navigation

-   Build tools

    Use the Cloud MTA Build Tool \(MBT\) to generate a deployment-ready multitarget application \(MTA\) archive `.mtar` from the artifacts of an MTA project according to the project’s MTA development descriptor \(`mta.yaml` file\), or from the module build artifacts according to the MTA deployment descriptor \(`mtad.yaml` file\). The Cloud MTA Build Tool \(MBT\) is the default \(and recommended\) build tool. For more details, see *The Cloud MTA Build Tool* in *Related Information* below.




### Database Explorer

The SAP Business Application Studio includes the SAP HANA database explorer that contains features and functions required by both developers and administrators, for example:

-   Database browser

    Browse, view, run, and visualize the content of all types of catalog objects, for example: tables, views, stored procedures, functions, synonyms, and so on.

-   SQL Console

    Create SQLScript, run SQL commands, visualize objects in text form \(procedures, functions, and so on\).

-   SQL Debugger

    Debug procedures and views in HDI containers. View the call stack, set break points, view and evaluate expressions and variables, and so on.

-   Job Log Viewer

    View the logs written by the scheduled jobs.




<a name="loiof7268f176e1943ad97edba3f1dfeda26__section_o4f_b3v_rv"/>

## Administration Tools

Web-based administration tools for SAP HANA Cloud are available in the SAP HANA Cloud cockpit. The cockpit is a Web-based tool that integrates a selection of tools for administration, monitoring, and software life-cycle management.

**Related Information**  


[Introduction to Multitarget Application Development and Deployment with SAP HANA Cloud](introduction-to-multitarget-application-development-and-deployment-with-sap-hana-clou-f472017.md "A developer’s view of multitarget applications in the Cloud Foundry run-time platform for SAP HANA Cloud, SAP HANA database.")

[SAP HANA Cloud, SAP HANA Database Administration Guide](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/330e5550b09d4f0f8b6cceb14a64cd22.html "This guide provides general information about administering the SAP HANA database consumed through SAP HANA Cloud.") :arrow_upper_right:

[The Cloud MTA Build Tool \(MBT\)](../030-HANA-Cloud-DB-Dev-Deployment/the-cloud-mta-build-tool-mbt-1412120.md "A new tool for building deployment archives for multitarget applications (MTA).")

[Working with SAP Business Application Studio](../020-HANA-Cloud-DB-Dev-Get-Started/working-with-sap-business-application-studio-ebd3400.md "SAP Business Application Studio provides a modular development environment for the development of business applications for SAP HANA Cloud.")

[SAP HANA Cockpit \(SAP HANA Cloud\)](https://help.sap.com/viewer/9630e508caef4578b34db22014998dba/cloud/en-US)

