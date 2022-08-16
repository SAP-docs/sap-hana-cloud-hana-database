<!-- loiodf31a08a2c164520bb7e558103dd5adf -->

# Create the Security Descriptor for a Multitarget Application

The security descriptor defines details of an application's security-related dependencies.



## Prerequisites

-   File name

    `xs-security.json`

-   Location

    Either of the following folders:

    -   Application root folder, for example, `/path/appname/`
    -   Application security folder, for example, `/path/appname/security`

-   Format

    JavaScript Object Notation \(JSON\)




## Context

The `xs-security.json` file defines the security and deployment options for an application; the information in the application-security file is used at application-deployment time, for example, for authentication and authorization.



<a name="loiodf31a08a2c164520bb7e558103dd5adf__steps_xly_smq_xs"/>

## Procedure

1.  Create the application resource-file structure.

    For example, `/path/appname/`

2.  Create a sub-folder for the JavaScript security files.

    The security sub-folder should be located in the application root folder, for example, `/path/appname/security`.

3.  Create the application security file.

    The application security file `xs-security.json` can be located either in the application root folder `/path/appname/` or the security folder `/path/appname/security`.

4.  Define details of the application's security-related dependencies.

    The contents of the `xs-security.json` file must adhere to the standards defined in the application's JSON-formatted security-descriptor syntax.


**Related Information**  


[The Application Security Descriptor](the-application-security-descriptor-3bfb120.md "A file that defines the details of the authentication methods and authorization types to use for access to your application.")

[Application Security Descriptor Configuration Syntax](application-security-descriptor-configuration-syntax-6d3ed64.md "The syntax required to set the properties and values defined in the xs-security.json application-security description file.")

