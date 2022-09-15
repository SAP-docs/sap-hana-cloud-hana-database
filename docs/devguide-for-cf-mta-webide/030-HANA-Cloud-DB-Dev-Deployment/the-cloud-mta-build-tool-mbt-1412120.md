<!-- loio1412120094534a23b1a894bc498c2767 -->

# The Cloud MTA Build Tool \(MBT\)

A new tool for building deployment archives for multitarget applications \(MTA\).

The Cloud MTA Build Tool \(MBT\) is a standalone command-line tool that enables you build a deployment-ready multitarget application \(MTA\) archive `.mtar` from the artifacts of an MTA project according to the project’s MTA development descriptor \(`mta.yaml` file\), or from the module build artifacts according to the MTA deployment descriptor \(`mtad.yaml` file\). The archive builder is used on a Windows or Linux file system that is independent from the development environment where the application project was created.

> ### Tip:  
> The Cloud MBT is the default \(and recommended\) build tool in SAP Web IDE Full-Stack. To build an MTA archive using the Cloud MBT in SAP Web IDE Full-Stack, right-click the project for which you want to generate an MTA archive and choose *Build* \> *Build with Cloud MTA Build Tool* in the context menu. You can monitor the build process in the system output displayed in the console. The resulting archive is saved in the folder `mta_archives` in the project structure.



<a name="loio1412120094534a23b1a894bc498c2767__section_sm5_ynh_vlb"/>

## Download and Install the MTA Build Tool

You can choose the method to download and install the MTA Build Tool:

-   Manual installation
    1.  Download the latest version of the MBT for your operating system from GitHub.

        > ### Note:  
        > For more details, see *Related Information* below.

    2.  Extract the archive to the location on the file system.
    3.  Add the `mbt` binary file to your `~/bin` path

-   Installation with the Node Package Manger \(NPM\)

    Assuming you have the `npm` tool installed, open a command shell and run the following command:

    `npm install -g mbt`




<a name="loio1412120094534a23b1a894bc498c2767__section_i4r_ysh_vlb"/>

## Prerequisites

To use the Cloud MBT to build an MTA archive from a project's source code in a Windows environment, you need to ensure that GNU Make 4.2.1 is already installed on your build machine.

Additional tools are required in your build environment if you want Cloud MBT to make use of specific builders, for example, `grunt`, `hdb`, `maven`, etc. For more details, see *The SAP Cloud MTA Build Tool \(GitHub\)* in *Related Information* below.

> ### Tip:  
> It is also possible to configure the builder in the project's `mta.yaml` file, for example, using the `build-parameters:` property.
> 
> ```
> - name: module1 
>    type: java 
>    build-parameters: 
>      builder: zip
> ```



<a name="loio1412120094534a23b1a894bc498c2767__section_e23_xsh_vlb"/>

## Usage

To use Cloud MBT to build an MTA archive for the default target environment \(Cloud Foundry\) from your project sources using the application's **development** descriptor \(`mta.yaml`\), use the following command in a command shell:

<code>mbt build <i class="varname">&lt;options&gt;</i></code>

The `mbt build` command generates a temporary `Makefile` according to the contents of the application project's MTA descriptor and runs the `make` command to package the MTA project into the MTA archive \(`MyArchive.mtar`\).

To use Cloud MBT to build an MTA archive using the application's **deployment** descriptor \(`mtad.yaml`\), use the following command in a command shell:

<code>mbt assemble <i class="varname">&lt;options&gt;</i></code>

> ### Note:  
> For more information about the build options available, for example, to specify the name and location of the generated MTAR archive, or the extension files \(`.mtaext`\) to use in the build, see *The SAP Cloud MTA Build Tool \(GitHub\)* in *Related Information* below.

**Related Information**  


[Download the SAP Cloud MTA Build Tool \(GitHub\)](https://github.com/SAP/cloud-mta-build-tool/releases)

[Welcome to the Cloud MTA Build Tool \(GitHub\)](https://sap.github.io/cloud-mta-build-tool/)

