<!-- loio274e8c16ea244ce3b55edd39d6fb4a7b -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Bind an Application to a User-Provided Service



<a name="loio274e8c16ea244ce3b55edd39d6fb4a7b__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project \(*FlightReservation* in this example\) that you want to bind is available.
-   The application project contains a database module called *db*.

    > ### Tip:  
    > If the database module is not yet bound to any service, you can bind it as part of this tutorial.




## Context

The *SAP HANA PROJECTS* explorer includes tools that enable you to manage the bindings to any user-provided services required by your SAP HANA database application. You can bind an application either to a new user-provided service that you create using the <span class="SAP-icons-V5"></span> \(Add database connection\) tool in the *Database Connections* node or to a user-provided service that already exists.

> ### Tip:  
> The list of user-provided services is displayed in *Database Connections* along with the current binding status, for example: ![](images/BAS_icon_dependencyBound_e45e7a9.svg) \(*bound service*\) or ![](images/BAS_icon_dependencyNotBound_1694e4a.svg) \(*unbound service*\). If a service is already bound to your application, the name of the bound service is included \(in brackets\), for example, *cross-container-service-1 \(UPS\)*.



## Procedure

1.  Open the *SAP HANA PROJECTS* explorer.

2.  Add a new database connection. \(*Optional*\)

    If the service to which you want to bind your application is not already included in the list of available services displayed in *Database Connections*, you need to add it, as follows:

    1.  Start the add-database-connection Wizard.

        Use the <span class="SAP-icons-V5"></span> \(Add database connection\) tool in the *Database Connections* node to start the *Add Database Connection* Wizard.

    2.  Specify a connection type for the new database connection.

        Choose *Create user-provided service instance* and the option *Use deployment target container database*.


    You will need to provide a name for the user-provided service and the credentials of the user who manages the user-provided service. You also have the option of using a procedure grantor and \(or\) an hdbgrants file to assign the privileges required for access to the user-provided service and the objects it reveals.

    -   *Procedure grantor*

        This is required if you are using a procedure rather than a database user to grant the privileges required to use a new user-provided service. You will need to provide the name of the procedure that assigns the privileges and the name of the schema where the procedure is located.

    -   *Generate hdbgrants file*

        Select this option if you want to create a grants file \(for example, `mygrants.hdbgrants`\) that can be used to assign privileges to the owner and consumer of database objects in the HDI container assigned to this database connection. The hdbgrants file is created with a basic template that you can use or adjust to suit your requirements.

        > ### Tip:  
        > SAP Business Application Studio displays the design-time `hdbgrants` artifact by default in a graphical editor that is designed to help reduce syntax errors. However, you can open the file in a code editor, too, or change the default setting. You can also choose ![](images/BAS_Codicon_go-to-file_b3beacd.svg) \(*Open Editor \(Code/UI\)\)* to toggle between the code and graphical editors. Changes made to the open artifact during the editing session are synchronized between both editors, and any syntax problems are highlighted together with recommendations, where appropriate.
        > 
        > If the auto-complete feature is enabled in the text \(code\) editor, the SAP HANA Native Application dev space in SAP Business Application Studio provides context-sensitive descriptions of tags and properties in JSON-based HDI artifacts. For common scenarios, templates are provided, too.


3.  Bind a database application to a user-provided service.

    In the list of services displayed in *Database Connections*, select the user-provided service to which you want to bind your application \(for example, ![](images/BAS_icon_dependencyNotBound_1694e4a.svg)*cross-container-service-1*\) and choose ![](images/BAS_icon_bind_074ce84.svg) \(*Bind*\).

4.  Unbind a database application from a user-provided service.

    Use the *Database Connections* node to display a the list of available user-provided service instances and their current status.

    1.  In the list of database connections, locate the user-provided service instance from which you want to unbind your database application and choose ![](images/BAS_icon_unbind_3f54cf3.svg) \(*Unbind*\).

        -   Bound "non-target" container services, for example, a user-provided service:

            ![](images/BAS_icon_dependencyBound_e45e7a9.svg)*cross-container-service-1 \(MyUserProvidedService\)* 


    2.  Check the status of the user-provided service.

        On completion of the unbinding operation, the binding status is displayed in the *Database Connections* node, for example:

        -   Unbound "non-target" container services, for example, a user-provided service:

            ![](images/BAS_icon_dependencyNotBound_1694e4a.svg)*cross-container-service-1* 




**Related Information**  


[Bind Applications to Database Services with SAP HANA Projects Explorer](bind-applications-to-database-services-with-sap-hana-projects-explorer-a3865b1.md "Use the SAP HANA Projects explorer to bind applications to database services and manage database connections.")

[Bind an Application to an HDI-Container Service](bind-an-application-to-an-hdi-container-service-6db6afa.md "")

[Bind an Application to a Database Schema Service](bind-an-application-to-a-database-schema-service-4f5add9.md "")

[Bind an Application to a Service Managed by the Service Manager](bind-an-application-to-a-service-managed-by-the-service-manager-818a87c.md "You can bind an application's database module to a service managed by SAP Service manager.")

[Permissions for Objects in HDI Containers](../040-HANA-Cloud-DB-Dev-Persistence-Model/permissions-for-objects-in-hdi-containers-79e8664.md "The owner of a container object needs additional privileges to the ones assigned by default.")

