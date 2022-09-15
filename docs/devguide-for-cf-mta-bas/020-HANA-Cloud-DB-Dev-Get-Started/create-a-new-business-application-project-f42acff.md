<!-- loiof42acff48e164acbb01b1ee969b1282b -->

# Create a New Business Application Project

Set up a new project for your application in SAP Business Application Studio.



<a name="loiof42acff48e164acbb01b1ee969b1282b__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged in to SAP Business Application Studio.
-   You are using the dev space that you set up in the previous tutorial.



## Context

This tutorial shows how to use the templates provided by SAP Business Application Studio to set up a project for your new SAP HANA database application.

> ### Tip:  
> The *Get Started with SAP HANA* tutorial in SAP Business Application Studio's *Guided Development* tool helps you to complete this task. The tool is available on SAP Business Application Studio's *Welcome* screen or in the command palette \(*View* \> *Find Command...* \> *Guided Development*\).



## Procedure

1.  Start the *Create Project from Template* Wizard.

    -   Open the command palette:

        Either press  [Crtl\] + [Shift\] + [P\]  

        Or choose *View* \> *Find Command...*

        Or just press [F1\]

    -   In the command palette, type ***Project*** and choose *Create Project from Template*.

    > ### Tip:  
    > Alternatively, in the *Welcome* tab, choose *Start from Template* \> *Create a new project*.

2.  Create a new project for your business application.

    1.  In the *New Project from Template* Wizard, choose *SAP HANA Database Project* and then choose *Start*.

    2.  In the *Add Basic Information* pane, type the name of the new project \(***FlightReservation*** \) and choose *Next*.

    3.  In the *Set Basic Properties* pane, accept the default settings and choose *Next*.

    4.  In the *Set Database Information* pane, use the default settings and choose *Next*.

        You can use the following default settings:

        -   *Namespace* \(empty\)

        -   *Schema Name* \(empty\)

        -   *SAP HANA Database Version \** \(HANA Cloud\)

        -   *Bind the database module to a Cloud Foundry service instance?* \(Yes\)


    5.  In the *Bind to HDI Container Service* pane, provide the requested information.

        It is necessary to provide the credentials required to log on to the Cloud Foundry end point that provides the service instance to which you want to bind the database module of your new application project. After you log on to Cloud Foundry, you can choose the target organization, space, and service instance.

        -   *Enter e-mail address* \(Type the e-mail address of a registered Cloud Foundry user\)
        -   *Enter Password* \(Type the Cloud Foundry user's password\)

            Press [Enter\] or click *Login -\>* to connect to Cloud Foundry.

            > ### Note:  
            > If two-factor authentication \(2FA\) is configured in your landscape, you might need to provide an additional single-use token.


        After you log in to Cloud Foundry, use the following options to specify the target Cloud Foundry space where the service instance is running:

        -   *Choose Cloud Foundry Org \** \(Select from the drop-down list\)
        -   *Choose Cloud Foundry Space \** \(Select from the drop-down list\)
        -   *Choose Cloud Foundry Service \** \(Create a new service instance\)
        -   *Please enter a unique and non-existing service-instance name\** \(default is "*<ProjectName\>*-hdidb-ws-*<WorkspaceName\>*"\)

            > ### Note:  
            > It is recommended to accept the default service-instance name displayed, but you can also choose an existing service instance from the drop-down list provided. However, binding to an existing service can lead to problems caused by the undeployment of existing files.


        Choose *Finish* to generate the new project called *FlightReservation* in the chosen Cloud Foundry organization and space.

        > ### Tip:  
        > If the underlying Cloud Foundry space subsequently changes, you can ensure that all bound services are automatically unbound, for example, by enabling the option *Unbind all services if the Cloud Foundry space changes* for the SAP HANA Project Explorer in User Preferences for SAP Business Application Studio. For more information, see *Related Information* below.


3.  Add the new project to a new workspace; choose *Open in New Workspace*.

    SAP Business Application Studio opens the explorer and displays the new project.

4.  Check the contents of the new project:

    Expand *FlightReservation* \> *db* \> *src* and look for `.hdiconfig` which provides a list of all supported database artifacts and a corresponding deployment HDI plug-in.

    In the *SAP HANA Project Explorer*, check the following details:

    1.  The new project has been added to your workspace.
    2.  The new project's `.gitignore` file includes an entry for the application's `.env` file, which defines any environment variable used by the application, for example:

        > ### Sample Code:  
        > <code>/<i class="varname">&lt;myApp&gt;</i>/.gitignore</code>
        > 
        > ```
        > mta_archives/
        > 
        > # auto generated wildcard
        > db/.env
        > ```

        > ### Note:  
        > Since the `.env` file can contain sensitive information, for example, in the form of user credentials, the *SAP HANA Projects* explorer checks if an application project's `.gitignore` file includes an entry for the application's `.env` file. If no entry for `.env` exists, a warning is displayed with a recommendation to add the `.env` file manually to the list of files for Git to ignore. For more information, see *Security Considerations* in *Related Information* below.

    3.  In the *SAP HANA Project Explorer,* the UI element *Database Connections* contains the entry *hdi\_db*.
    4.  The UI elements ![](images/BAS_icon_dataConnections_e11cd70.svg) *Database Connections* and ![](images/BAS_icon_targetContainerBound_5c18d02.svg) *hdi\_db* are both green \(bound/enabled\).

        > ### Tip:  
        > If the application's database module is **bound** to a deploy service, the assigned SAP HDI container is used to store both the application's design-time and deployed run-time artifacts.


5.  Set up the SAP HANA Database Explorer.

    The SAP HANA Database Explorer enables you to view the run-time objects that are deployed to the SAP HDI container assigned to the SAP HANA database application.

    1.  Open the command palette.

    2.  Locate and run *SAP HANA: Open Database Explorer*

        Depending on the security setup, you might need to provide user credentials to log in and, if required, an additional access token.

    3.  Add the application project's HDI container to the SAP HANA Database Explorer.

        > ### Tip:  
        > For more information about viewing the contents of HDI containers in Database Explorer, see *View Database Objects with the Database Explorer* in *Related Information* below.



**Related Information**  


[Set up a Development Space for SAP Business Application Studio](set-up-a-development-space-for-sap-business-application-studio-6697174.md "Create a development space that includes tools that enable application development.")

[Add Database Artifacts to your SAP HANA Cloud Database Application](add-database-artifacts-to-your-sap-hana-cloud-database-application-1aa9165.md "Add the underlying design-time database objects to your SAP HANA application.")

[Working with SAP Business Application Studio](working-with-sap-business-application-studio-ebd3400.md "SAP Business Application Studio provides a modular development environment for the development of business applications for SAP HANA Cloud.")

[View Database Objects with the Database Explorer](view-database-objects-with-the-database-explorer-0e5ac0b.md "Check the contents of your database with SAP HANA Database Explorer.")

[Security Considerations](security-considerations-0e96265.md "An overview of the best practices that need to be implemented for secure development.")

[User Preferences for SAP HANA Native Application Development Tools](user-preferences-for-sap-hana-native-application-development-tools-57e2fe6.md "Customize the SAP HANA Native Application project workspace by setting or modifying user preferences.")

