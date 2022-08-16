<!-- loioebb42efc880c4276a5f2294063fae0c3 -->

# Create the MTA Description Files

Multi-target applications are defined in multiple descriptor files.



## Context

A multi-target application \(MTA\) comprises multiple pieces of software called “modules” which all share a common lifecycle for development and deployment. An MTA is described in two descriptor files:

-   The **development** descriptor \(`mta.yaml`\)

    Used to define the design-time elements and dependencies of a multitarget application. The development descriptor is used to generate the deployment descriptor.

-   The **deployment** descriptor \(`mtad.yaml`\)

    Defines the run-time prerequisites and dependencies for the deployment of a multitarget application


> ### Note:  
> If you use *SAP Business Application Studio* to build and deploy an MTA, both the development and the deployment descriptor are created for you automatically and placed in the required location.

To create a multi-target application, perform the following steps:



## Procedure

1.  Create the application resource-file structure.

2.  Create the **development** descriptor for the multi-target application.

    The development descriptor for an MTA is defined in the design-time artifact `mta.yaml`, which must be placed in the root folder of your MTA project. The MTA development descriptor is used by *SAP Business Application Studio* to generate an MTA deployment descriptor \(`mtad.yaml`\).

    > ### Note:  
    > *SAP Business Application Studio* creates the `mta.yaml` file automatically when you create a new MTA project.

3.  View or edit the **development** descriptor \(`mta.yaml`\).

    *SAP Business Application Studio* provide a choice between graphical and text-based code editors. To edit a multitarget application's development descriptor, proceed as follows:

    1.  Locate the development descriptor that you want to view and edit.

        In the *SAP Business Application Studio's* project explorer, expand the application project whose development descriptor you want to edit.

    2.  Right click the `mta.yaml` file, choose *Open With* 

    3.  Choose the editor you want to use to view and edit the `mta.yaml` file.

        The following options are provided:

        -   *Code Editor*

            Displays the contents of the `mta.yaml` file in a text-based editing tool.

        -   *MTA Editor*

            Displays the contents of the `mta.yaml` file in a graphical editing tool.


        > ### Tip:  
        > For more information about the keywords, properties, and parameters used in the `mta.yaml` file, see *The MTA Development Descriptor* and *MTA Deployment Descriptor Syntax* in *Related Information* below.


4.  Create the **deployment** descriptor for the multi-target application.

    The deployment descriptor for an MTA is defined in the design-time artifact `mtad.yaml`, which must be placed in the root folder of your MTA project.

    > ### Note:  
    > If you use *SAP Business Application Studio* or the Cloud MTA Build Tool \(MBT\) to build and deploy an MTA, the deployment descriptor is created for you automatically based on the information in the MTA **development** descriptor \(`mta.yaml`\) in your MTA project.

    The following restrictions apply to the MTA **Deployment** Descriptor \(`mtad.yaml`\):

    <a name="loioebb42efc880c4276a5f2294063fae0c3__table_gnw_lgv_ccb"/>MTA Descriptor File Size Restrictions


    <table>
    <tr>
    <th valign="top">

    MTA Component


    
    </th>
    <th valign="top">

    Maximum Size


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    MTA archive


    
    </td>
    <td valign="top">

    4 GB


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    MTA **module** content


    
    </td>
    <td valign="top">

    4 GB


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    MTA **resource** content


    
    </td>
    <td valign="top">

    1 GB


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    MTA deployment descriptor \(`mtad.yaml`\)


    
    </td>
    <td valign="top">

    1 MB


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    MTA manifest \(`MANIFEST.MF`\)


    
    </td>
    <td valign="top">

    1 MB


    
    </td>
    </tr>
    </table>
    
5.  If required, create a deployment extension description for the multi-target application. \(optional\)

    The **extension** of an MTA deployment description is defined in a file with the suffix `.mtaext`, for example, `production-config.mtaext`.


**Related Information**  


[Multitarget Applications](multitarget-applications-8b55a61.md "Multitarget applications collect multiple modules and resource references in a single, deployable archive.")

[The MTA Development Descriptor](the-mta-development-descriptor-4486ada.md "Multi-target applications are defined in a design-time development descriptor.")

[The MTA Deployment Descriptor](the-mta-deployment-descriptor-33548a7.md "Description of the deployment options for a multitarget application.")

[MTA Deployment Descriptor Syntax](mta-deployment-descriptor-syntax-4050fee.md "Description of an MTA's deployment-related prerequisites and dependencies.")

[The Cloud MTA Build Tool \(MBT\)](the-cloud-mta-build-tool-mbt-1412120.md "A new tool for building deployment archives for multitarget applications (MTA).")

