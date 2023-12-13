<!-- loio00340d4ede0a43ceb0a67f36bbc46a3a -->

# Create Virtual Tables

Virtual tables enable you to access objects in other databases without having to replicate in SAP HANA.



<a name="loio00340d4ede0a43ceb0a67f36bbc46a3a__prereq_qrw_sym_bhb"/>

## Prerequisites

You must already have created a remote source.



## Context

The SAP Web IDE supports the creation of virtual tables using either a code editor or a built-in Wizard. The Wizard is designed to help those users who are not sure of the syntax required to create virtual tables in the code editor. After creating the virtual tables, you can use them as a data source.



## Procedure

1.  Start SAP Web IDE in a Web browser.

2.  If you want to create a new project for the virtual table, do the following:

    1.  In the SAP Web IDE, choose *File* \> *New* \> *Project from Template*.

    2.  In the *Environment* dropdown list, select *Cloud Foundry*.

    3.  Select *Multi-Target Application Project* and choose *Next*.

    4.  Type a name for the new MTA project \(for example, `myApp` and choose *Next* to confirm\).

    5.  Specify details of the new MTA project and choose *Next* to confirm.

    6.  Create the new MTA project; choose *Finish*.


3.  Select the *SAP HANA Database Module* in which you want to create the virtual table.

    > ### Tip:  
    > If you do not already have a database module, right-click the root folder of your new MTA project and, in the context menu, choose *New* \> *SAP HANA Database Module*.

4.  Browse to the *src* folder, right-click it and choose *New* \> *Virtual Table*.

5.  Grant the privileges required to locate and select objects on the remote source.

    The object owner and the application \(run-time\) user require the global object privilege `CREATE VIRTUAL TABLE` on the remote source to be able to use the *Virtual Table Editor* to locate and select objects in the remote database.

    > ### Tip:  
    > You can use an `hdbgrants` file to grant the required privileges, for example, with the `"global_object_privileges": [...]` key in the `"object_owner"` and `"application_user"` sections as shown in the following example. For more information about syntax requirements in the `hdbgrants` file, see *Related Information* below.

    > ### Code Syntax:  
    > My `db/src/.hdbgrants` File
    > 
    > ```
    > 
    > {
    >  "grantor-service": {
    >    "object_owner": { 
    >      "global_object_privileges": [ 
    >       { 
    >        "name": "MyRemoteSource",  
    >        "type": "REMOTE SOURCE",  
    >        "privileges": [  
    >          "CREATE VIRTUAL TABLE"  
    >        ] 
    >       } 
    >      ]  
    >    }, 
    >    "application_user": { 
    >      "global_object_privileges": [ 
    >       { 
    >        "name": "MyRemoteSource",  
    >        "type": "REMOTE SOURCE",  
    >        "privileges": [  
    >          "CREATE VIRTUAL TABLE"  
    >        ] 
    >       } 
    >      ]  
    >    }
    >  }
    > }
    > ```

6.  In the *Create Virtual Object* wizard, select a remote source and click *Next*.

7.  Use the filter parameters to search for one or more remote objects you want to create a virtual table from and click *Next*.

8.  Enter a name for the virtual object and click *Finish*.

    Use the naming format ***namespace::virtual\_table\_name***.

9.  Choose *Save* in the menu bar or [CTRL\] + [S\]  to save your file \(virtual table\).

10. Build the SAP HANA database module.

    The build process uses the design-time database artifacts to generate the corresponding actual objects \(run-time objects\) in the HDI container.

    From the module context menu, choose *Build*.


**Related Information**  


[Syntax Options in the hdbgrants File](syntax-options-in-the-hdbgrants-file-f49c1f5.md "Assign the privileges required by users to access objects in the target schema.")

[File Format Options \(SDI & SDA Installation and Configuration Guide\)](https://help.sap.com/docs/HANA_SMART_DATA_INTEGRATION/7952ef28a6914997abc01745fef1b607/ae74d5b5e01c4393bc2c2ade0b3826bd.html)

