<!-- loio0b0ed18fa4794cc4949404e5547103f0 -->

# Create the Multitarget Application Package Descriptor

The package descriptor defines a JavaScript application's design-time and run-time dependencies in Cloud Foundry.



## Prerequisites

-   File name:

    `package.json`

-   Location:

    Application source-file folder, for example, `package.json`

-   Format

    JavaScript Object Notation \(JSON\)




## Context

The build, deployment, and run-time dependencies of a JavaScript application are described in the `package.json` file. The `package.json` file is mandatory for JavaScript applications and it must be located in the JavaScript application's source-file folder, for example, `js/`.

To create an application package description for your new application project, perform the following steps:



<a name="loio0b0ed18fa4794cc4949404e5547103f0__steps_xly_smq_xs"/>

## Procedure

1.  Create the application resource-file structure.

    For example, `/appname1/`

2.  Create a sub-folder for the JavaScript source-files in the application root folder.

    For example, `/appname1/js`

3.  Create the application package description file.

    The application descriptor file `package.json` must be located in the JavaScript source-files folder, for example, `/appname1/js`.

4.  Define details of the application packages and any dependencies:

    The contents of the `package.json` file must follow the required syntax.


**Related Information**  


[The Multitarget Application Package Descriptor](the-multitarget-application-package-descriptor-0818c56.md "A file describing the prerequisites and dependencies that apply to a JavaScript multitarget application in Cloud Foundry on SAP Business Technology Platform.")

[Multitarget Application Package Descriptor Configuration Syntax](multitarget-application-package-descriptor-configuration-syntax-a4a91b5.md "The package descriptor defines the prerequisites and dependencies that apply to packages in a JavaScript multitarget application deployed in the Cloud Foundry run time.")

