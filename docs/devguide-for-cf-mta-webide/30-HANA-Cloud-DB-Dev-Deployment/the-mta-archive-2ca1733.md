<!-- loio2ca1733ea9d0429ea36ed74ea88705a0 -->

# The MTA Archive

An MTA archive is a Jar file containing deployable application modules.

A multi-target application \(MTA\) archive is used to deploy an application that comprises multiple modules in one deployment operation. An MTA archive contains all the application modules to be deployed; MTA archives have the file extension `.mtar`. MTA archives can be built either with the Java SDK `jar` command or with Zip-tools.

> ### Tip:  
> It is also possible to build an MTA archive with the tools included in SAP Web IDE Full-Stack. Right-click the application project for which you want to create an MTA archive and choose *Build* \> *Build* in the context menu displayed.

An MTA archive contains the following minimum mandatory content:

-   One or more MTA modules

-   Two mandatory configuration files in the `META-INF/` folder:

    -   `MANIFEST.MF`

        The deployment manifest

    -   `mtad.yaml`

        The deployment description



The MTA deployment tools assume that the content of an MTA archive has the following mandatory structure:

> ### Sample Code:  
> SAP HANA MTA Archive
> 
> ```
> 
> /java-backend/
> +--- backend.war
> /ui5-frontend/
> +--- ui.zip
> /META-INF/
> +--- MANIFEST.MF
> +--- mtad.yaml
> ```
> 
> The MTA archive can be deployed using the MTA deployment tools, for example, the `cf deploy` command in a command shell or the build/run tools available in the *SAP Web IDE Full-stack*.

