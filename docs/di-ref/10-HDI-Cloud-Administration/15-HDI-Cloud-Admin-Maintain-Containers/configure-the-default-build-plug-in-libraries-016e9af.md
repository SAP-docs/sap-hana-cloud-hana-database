<!-- loio016e9afdb7b54bfca0679c7358ccb543 -->

# Configure the Default Build Plug-in Libraries Available to an SAP HDI Container

Maintain the set of plug-in libraries available by default in an SAP HDI container.



## Context

In SAP HANA Deployment Infrastructure \(HDI\), HDI container administrators can configure a default set of commonly used SAP HDI plug-in libraries for any HDI container for which they have responsibility.

> ### Tip:  
> The table `_SYS_DI.T_DEFAULT_LIBRARIES` contains the names of a default set of plug-in libraries used for HDI artifacts. The contents of the table are passed to the configure-libraries procedure \(`DI.CONFIGURE_LIBRARIES`\) as input. The content of `_SYS_DI.T_DEFAULT_LIBRARIES` is not modified.



<a name="loio016e9afdb7b54bfca0679c7358ccb543__steps_hnw_j32_l1b"/>

## Procedure

1.  In an SQL console, connect to the database as the administrator of the target HDI container \(in this example, *<container\_name\>*\).

2.  Open the SQL editor for this database.

3.  Set the list of plug-in libraries available by default in the specified target container.

    Insert the following SQL statement into the SQL editor:

    > ### Sample Code:  
    > ```sql
    > CALL <container_name>#DI.CONFIGURE_LIBRARIES(_SYS_DI.T_DEFAULT_LIBRARIES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > ```

    1.  Replace *<container\_name\>* in the `CALL` statement with the name of your container.


4.  Run the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  \(**Optional**\) Confirm that the default libraries have been configured successfully by listing all currently configured build plug-in libraries available to the container.

    > ### Tip:  
    > It is also possible to configure the HDI plug-in library for an HDI container service instance in SAP BTP, for example, with an `update-service` operation. Log in to Cloud Foundry and use the following command :
    > 
    > <code>cf update-service <i class="varname">&lt;service instance name&gt;</i> -c '{"action": "configureLibraries"}</code>


**Related Information**  


[List All Currently Configured Build Plug-in Libraries Available to an SAP HDI Container](list-all-currently-configured-build-plug-in-li-ddb04a9.md "Display a list of all the build plug-in libraries available for use in an SAP HDI container.")

[Configure a Custom Set of Build Plug-in Libraries Available to an SAP HDI Container](configure-a-custom-set-of-build-plug-in-librar-f0557bf.md "Maintain a custom set of plug-in libraries available in an SAP HDI container.")

[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

