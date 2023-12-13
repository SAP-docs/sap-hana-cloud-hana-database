<!-- loioe735ec2bac4541339e9301e8cae7ca0b -->

# Restore Design-time Artifacts from the Database

Recreate a design-time database artifact from the run-time version in the HDI container's deployed file system.



<a name="loioe735ec2bac4541339e9301e8cae7ca0b__prereq_vym_d1w_fvb"/>

## Prerequisites

Before you start the database-artifact recovery process, bear in mind the following prerequisites

-   The database module that contains the database artifact must be bound to a service, for example, either an HDI container service or a user-provided service.




## Context

If design-time database artifacts are missing from your application's database module or changes made to the artifacts have rendered them undeployable due to configuration errors, you can use the *SAP HDI Artifact Recovery Wizard* to restore a working version of the missing or corrupt design-time artifact from the database object currently deployed to the HDI container's deployed file system, as follows:



## Procedure

1.  In SAP Business Application Studio, open the command palette.

    -   Press [Crtl\] + [Shift\] + [P\]  or
    -   Press [F1\] or
    -   Choose *View* \> *Command Palette...*

2.  Start the *SAP HDI Artifact Recovery Wizard*

    Type `recovery` in the command palette and choose *SAP HANA: Start Database Artifact Recovery* in the list of commands displayed.

    The *SAP HDI Artifact Recovery Wizard* is displayed.

3.  Choose the database module for the application design-time artifacts.

    Choose *Browse...* and use the *Open* dialog to locate the database module to which you want to restore artifacts, for example, `/home/user/projects/FlightReservation/db` and choose *OK*.

    The *Select artifacts to recover* pane lists the differences between the design-time artifacts in the application's workspace and the objects in the corresponding HDI container's deployed file system. Additional details describe the location of the listed objects and their current status, for example, *Missing from workspace* or *Modified*.

    **Workspace Artifact Status**


    <table>
    <tr>
    <th valign="top">

    Status
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Missing from workspace*
    
    </td>
    <td valign="top">
    
    The artifact exists in the HDI container's deployed file system but not in the application workspace
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Modified*
    
    </td>
    <td valign="top">
    
    The artifact in the workspace is newer than the artifact in the deployed file system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Unchanged*
    
    </td>
    <td valign="top">
    
    The artifact in the workspace file system is the same as the artifact in the deployed file system.
    
    </td>
    </tr>
    </table>
    
    > ### Tip:  
    > Check the option *Show all workspace files* to display all *Unchanged* artifacts. You can only select for recovery those deployed artifacts whose status is different from the status of the corresponding artifacts in the database application's workspace, including those that have the status *Missing from workspace*.

    For more information about using HDI tools to see the status of artifacts in an HDI container's deployed file system, see *Related Information* below.

4.  Choose the artifacts to recover from the deployed file system.

    the artifacts currently in yourSelect the artifacts that you want to recover from the deployed file system and choose *Continue* to display an overview of the artifacts selected for recovery.

    > ### Note:  
    > Artifacts with the status *Unchanged* cannot be selected for recovery.

5.  Recover all selected artifacts.

    This step restores to the database module in your application's workspace all the artifacts you have selected from the deployed file system.

    In the *Selected artifacts* pane, choose *Recover selected*.

    The selected database artifacts are restored to the original location in the specified design-time project folder, for example, `/home/user/projects/FlightReservation/db`.


**Related Information**  


[Add Database Artifacts to your SAP HANA Cloud Database Application](add-database-artifacts-to-your-sap-hana-cloud-database-application-1aa9165.md "Add the underlying design-time database objects to your SAP HANA application.")

[The HDI Container API; STATUS Command \(SAP HANA Cloud HDI Reference\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/c2cc2e43458d4abda6788049c58143dc/e14a40cb7db048f99b5cea2548fc89ee.html)

