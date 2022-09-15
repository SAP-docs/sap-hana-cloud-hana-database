<!-- loiof728966223894cc28be3ca2ee60ee784 -->

# Set up a Development Space for Full-stack Cloud Applications

Create a development space for the Cloud Application Programming model \(CAP\) which includes tools for application development.



<a name="loiof728966223894cc28be3ca2ee60ee784__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You have access to SAP Business Application Studio.



<a name="loiof728966223894cc28be3ca2ee60ee784__context_pbf_m2n_b4b"/>

## Context

In SAP Business Application Studio, the developer is provided with one or more development spaces \(dev spaces\). As a developer, you can chose which tools will be installed in your dev spaces by selecting the suitable extension pack along with any additional extensions that you want or need. The dev space is an isolated development environment providing a pseudo-local development experience. Among other tools, it provides terminal access to the file system so you can run various commands, you can test-run your application in the dev space itself without deploying to the target run-time environment \(Cloud Foundry\), almost as if the you were working on your own desktop.

This tutorial shows how to create and set up a dev space in SAP Business Application Studio, which you can then use to develop and deploy applications using the SAP Cloud Application Programming model \(CAP\).



<a name="loiof728966223894cc28be3ca2ee60ee784__steps_qbf_m2n_b4b"/>

## Procedure

1.  Log in to SAP Business Application Studio.

2.  Create a new development space.

    1.  Choose *Create Dev Space*.

    2.  In the *Create a New Dev Space* Wizard, provide a name for the new space, for example, "***CAPDEV***"

        > ### Tip:  
        > The name must contain only alphanumeric characters; special characters are not permitted.

    3.  Choose the business scenario that best suits the applications you want to create, for example, *Full Stack Cloud Application*.

    4.  Check the list of predefined base extensions.

        The *Full Stack Cloud Application* dev space includes a set of basic predefined tools. Check that the list includes all the extensions you need.

    5.  Select additional extensions if necessary, for example: CDS Graphical Modeler, Calculation View, HDI base/feature, or Database Explorer.

        > ### Tip:  
        > If you are not sure which extensions you need, bear in mind that you can add extensions later after creating a dev space, for example, using the *\[Edit\]* tool in the list of dev spaces as described in the next steps.

    6.  Choose *Create Dev Space*.


3.  Start the new dev space.

    On startup, SAP Business Application Studio displays a list of available development spaces. Choose *\[\>\]* \(Run\) to start the development space that will contain your application project. You can only open a dev space whose status is *RUNNING*.

    In the list of dev spaces displayed in SAP Business Application Studio, locate the new dev space *CAPDEV*.

4.  Open the new dev space.

    In the list of dev space names, click the space name, for example, *CAPDEV*.

5.  Connect the dev space to the Cloud Foundry organization and space where you want to develop and deploy your business application.

    The target CF organization and space is displayed at the bottom of the window in the status bar, for example, *Targeting Cloud Foundry MyOrg/MySpace*. If no target is set, click the target field in the status bar to open the command palette and perform the following steps:

    1.  Log in to Cloud Foundry.

        You will need your CF user name and password.

        > ### Note:  
        > If two-factor authentication is active, you will need an additional one-time token, too.

    2.  Set the Cloud Foundry organization.

    3.  Set the Cloud Foundry space.


6.  Customize a dev space.

    You can add extensions to \(or remove them from\) an existing dev space, for example, using the *\[Edit\]* tool in the list of dev spaces.

    > ### Note:  
    > The dev space you want to modify must be *STOPPED*; it is not possible to edit a dev space whose status is *RUNNING* or *STARTING*.

    1.  Display the list of dev spaces you have created.

    2.  Check that the dev space you want to edit is *STOPPED*; if it is not, then stop it.

    3.  Choose the *Edit* button for the dev space you want to modify.

    4.  Select the extensions you want to add or remove and choose *Save Changes*.

    5.  Restart the modified dev space.



**Related Information**  


[Working with the SAP Cloud Application Programming Model](working-with-the-sap-cloud-application-programming-model-166f4fb.md "Create a business application using the SAP Cloud Application Programming model.")

[Set up a Development Space for SAP Business Application Studio](set-up-a-development-space-for-sap-business-application-studio-6697174.md "Create a development space that includes tools that enable application development.")

