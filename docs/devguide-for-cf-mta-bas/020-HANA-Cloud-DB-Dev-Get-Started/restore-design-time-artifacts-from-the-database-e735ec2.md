<!-- loioe735ec2bac4541339e9301e8cae7ca0b -->

# Restore Design-time Artifacts from the Database

Recreate a design-time database artifact from the run-time version in the HDI container's deployed file system.



## Context

If design-time database artifacts are missing from your application's database module or changes made to the artifacts have rendered them undeployable due to configuration errors, you can use the *SAP HDI Artifact Recovery Wizard* to restore a working version of the missing or corrupt design-time artifact from the database object currently deployed to the HDI container's deployed file system, as follows:



## Procedure

1.  In SAP Business Application Studio, open the command palette.

    -   Press  [Crtl\] + [Shift\] + [P\]  or
    -   Press [F1\] or
    -   Choose *View* \> *Find Command...*

2.  Start the *SAP HDI Artifact Recovery Wizard*

    Type ***start*** in the command palette and choose start the *SAP HANA: SAP HDI Artifact Recovery Wizard* in the list of commands displayed.

    The start the *SAP HDI Artifact Recovery Wizard* is displayed.

3.  Choose the database module for the application design-time artifacts.

    Choose *Browse...* and use the *Open* dialog to locate the database module to which you want to restore artifacts, for example, `/home/user/projects/FlightReservation/db`. Next choose *Choose database module directory for artifact recovery*.

    The *Select artifacts to recover* pane lists the differences between the design-time artifacts in the application's workspace and the objects in the corresponding HDI container's deployed file system. Additional details describe the location of the listed objects and their current status, for example, *Missing from workspace* or *Modified*.

    <a name="loioe735ec2bac4541339e9301e8cae7ca0b__table_fcd_krx_n5b"/>Workspace Artifact Status


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
    > Check the option *Show all workspace files* to display **all** the artifacts currently in your database application's workspace, including those that have the status *Unchanged*. Only artifacts with the status *Missing from workspace* can be selected for recovery.

    For more information about using HDI tools to see the status of artifacts in an HDI container's deployed file system, see *Related Information* below.

4.  Choose the artifacts to recover from the deployed file system.

    Select the artifacts that you want to recover from the deployed file system and choose *Continue* to display an overview of the artifacts selected for recovery.

    > ### Note:  
    > Artifacts with the status *Unchanged* cannot be selected for recovery.

5.  Recover all selected artifacts.

    This step restores to the database module in your application's workspace all the artifacts you have selected from the deployed file system.

    In the *Selected artifacts* pane, choose *Recover selected*.

    > ### Tip:  
    > The option *Backup modified workspace files* is enabled by default, and the backed-up files are stored in the folder <code>BACKUP_Artifact_Recovery-<i class="varname">&lt;timestamp&gt;</i></code> in the application's workspace.


**Related Information**  


[Add Database Artifacts to your SAP HANA Cloud Database Application](add-database-artifacts-to-your-sap-hana-cloud-database-application-1aa9165.md "Add the underlying design-time database objects to your SAP HANA application.")

[The HDI Container API; STATUS Command \(SAP HANA Cloud HDI Reference\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/c2cc2e43458d4abda6788049c58143dc/e14a40cb7db048f99b5cea2548fc89ee.html)

