<!-- loio6697174ae98d434d9f622b7765336fd7 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Set up a Development Space for SAP Business Application Studio

Create a development space that includes tools that enable application development.



<a name="loio6697174ae98d434d9f622b7765336fd7__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You have access to SAP Business Application Studio.



## Context

In SAP Business Application Studio, the developer is provided with one or more development spaces \(dev spaces\). As a developer, you can chose which tools will be installed in your dev spaces by selecting the suitable extension pack along with any additional extensions that you want or need. The dev space is an isolated development environment providing a pseudo-local development experience. Among other tools, it provides terminal access to the file system so you can run various commands, you can test-run your application in the dev space itself without deploying to the target run-time environment \(Cloud Foundry\), almost as if the you were working on your own desktop.

This tutorial shows how to create and set up a dev space in SAP Business Application Studio, which you can then use to develop and deploy SAP HANA database applications.



## Procedure

1.  Log in to SAP Business Application Studio.

2.  Create a new development space.

    1.  Choose *Create Dev Space*.

    2.  In the *Create a New Dev Space* Wizard, choose the business scenario that best suits the applications you want to create, for example, *SAP HANA Native Application*.

    3.  Check the list of predefined SAP extensions.

        The SAP HANA Native Application dev space includes a set of basic predefined extensions. Check that the list includes all the extensions you need.

    4.  Select additional extensions if necessary.

        Check the list of *Additional SAP Extensions* to see if it includes any other tools you might need, for example: *SAP HANA Performance Tools*, etc.

        > ### Tip:  
        > If you are not sure which extensions you need, bear in mind that you can add extensions later after creating a dev space, for example, using the *\[Edit\]* tool in the list of dev spaces as described in the next steps.

    5.  Provide a name for the new space, for example, "***HANADEV***"

        > ### Tip:  
        > The name must contain only alphanumeric characters; special characters are not permitted.

    6.  Choose *Create Dev Space*.

        The new dev space *HANADEV* is displayed in the dev space manager and automatically started.


3.  Open the new dev space.

    In the list of dev space names, monitor the status of the new *HANADEV* dev space. When it displays the status *RUNNING*, click the dev space name *HANADEV* to open it in a new workspace.

    > ### Tip:  
    > On startup, SAP Business Application Studio displays a list of available development spaces in the dev space manager, but all dev spaces are in the status *STOPPED*. Since you can only open a dev space whose status is *RUNNING*, you have to start it manually. Choose <span style="font-size:16px;"><span class="SAP-icons"></span></span> \(Run\) to start the development space that contains the application project you want to work on.

4.  Connect the dev space to the Cloud Foundry organization and space where you want to develop and deploy your business application.

    By default, SAP Business Application Studio logs on to the most recently used Cloud Foundry target and displays the connection details in the status bar, for example, *Targeting Cloud Foundry MyOrg/MySpace*. If no target has yet been set, the status bar displays the message *The Organization and space in CF have not been set*.

    > ### Note:  
    > If no information about the connection to Cloud Foundry is available in the status bar, click <span style="font-size:16px;"><span class="SAP-icons"></span></span> \(Manage\) and choose *Settings* \> *Extensions* \> *Cloud Foundry Tools* \> *Show Target Information* and enable *Display the current Cloud Foundry target information in the status bar*.

    To set the organization and space for your dev space, you need to log on to Cloud Foundry and specify the target to use, as described in the following steps:

    1.  Log in to Cloud Foundry.

        Click the message *The Organization and space in CF have not been set* in the status bar to open the command palette, where the *CF: Log in to cloud foundry* Wizard prompts you for the information required to log on to Cloud Foundry. Alternatively, you can use the *Cloud Foundry: Targets* tool in the tool-selection pane to display a list of known Cloud Foundry targets; create a new target; or set the default target organization and space to use for your dev space.

        > ### Note:  
        > To log on to Cloud Foundry, you need to know the Cloud Foundry API end point, for example, <code>https://api.cf.sap.hana.<i class="varname">&lt;etc...&gt;</i></code>. You will also need to provide a CF user name \(or e-mail address\) and a corresponding password. If two-factor authentication is active, bear in mind that an additional one-time authentication token is required.

    2.  Set the Cloud Foundry organization.

    3.  Set the Cloud Foundry space.


5.  Customize a dev space.

    You can add extensions to \(or remove them from\) an existing dev space, for example, using the <span style="font-size:16px;"><span class="SAP-icons"></span></span> \(Edit\) tool in the list of dev spaces.

    > ### Note:  
    > The dev space you want to modify must be *STOPPED*; it is not possible to edit a dev space whose status is *RUNNING* or *STARTING*.

    1.  Display the list of dev spaces you have created.

    2.  Check that the dev space you want to edit is *STOPPED*; if it is not, then stop it.

    3.  Choose the *Edit* button for the dev space you want to modify.

    4.  Select the extensions you want to add or remove and choose *Save Changes*.

    5.  Restart the modified dev space.



**Related Information**  


[Set up the SAP Business Application Studio Service](set-up-the-sap-business-application-studio-service-83c95f0.md "Subscribe to the SAP Business Application Studio Cloud service.")

[Create a New Business Application Project](create-a-new-business-application-project-f42acff.md "Set up a new project for your application in SAP Business Application Studio.")

[Working with SAP Business Application Studio](working-with-sap-business-application-studio-ebd3400.md "SAP Business Application Studio provides a modular development environment for the development of business applications for SAP HANA Cloud.")

[The SAP HANA Native Application Dev Space](the-sap-hana-native-application-dev-space-e2edc0e.md "Develop, build, and deploy native SAP HANA Cloud multitarget applications or analytical models.")

