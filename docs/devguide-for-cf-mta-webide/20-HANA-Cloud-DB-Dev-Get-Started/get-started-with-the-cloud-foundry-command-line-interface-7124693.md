<!-- loio7124693bc1a346d3a3ed7f0989209960 -->

# Get Started with the Cloud Foundry Command-line Interface

Learn how to use the CF command.



<a name="loio7124693bc1a346d3a3ed7f0989209960__prereq_gst_3rp_qlb"/>

## Prerequisites

-   You have access to a Cloud Foundry environment
-   You know the URL for the target API on the Cloud Foundry Controller, for example, `https://api.cf.sap.hana.ondemand.com`



## Context

You will need to open a command shell to perform the following tasks:



## Procedure

1.  Check that the `cf` CLI is available and working.

    On your client machine, run the following commands in a command shell to show the version of the client and the help available for the `cf` commands:

    ```
    $ cf -v
    cf.exe version 6.51.0+2acd15650.2020-04-07
    
    $ cf help -a
    ```

    To display help for a specific command, use the `cf help` command followed by the name of a command whose help you want to display, as shown in the following example:

    ```
    $ cf help login
    NAME:
       login - Log user in
    
    USAGE:
       cf.exe login [-a API_URL] [-u USERNAME] [-p PASSWORD] [-o ORG] [-s SPACE] 
       [--sso | --sso-passcode PASSCODE] [--origin ORIGIN]
    ```

2.  Install the Cloud Foundry plug-ins for SAP Multitarget Applications \(MTA\).

    The `multiapps` plug-in enables you to manage and maintain so-called multitarget applications, which combine a number of Cloud Foundry applications in a single package. To install the `multiapps` plug-in, run the following command in a command shell:

    ```
    $ cf install-plugin multiapps -f
    ```

    > ### Tip:  
    > The *\-f* option **forces** the installation of the plug-ins without any further prompt or confirmation.

    When the installation has completed, list the installed plug-ins with the `cf plugins` command, as shown in the following example:

    ```
    $ cf plugins
    Listing installed plugins...
    
    plugin      version   command name                 command help
    multiapps   2.4.0     bg-deploy                    Deploy a multi-target app using blue-green deployment
    multiapps   2.4.0     deploy                       Deploy a new multi-target app or sync changes to an existing one
    multiapps   2.4.0     download-mta-op-logs, dmol   Download logs of multi-target app operation
    multiapps   2.4.0     mta                          Display health and status for a multi-target app
    multiapps   2.4.0     mta-ops                      List multi-target app operations
    multiapps   2.4.0     mtas                         List all multi-target apps
    multiapps   2.4.0     purge-mta-config             Purge no longer valid configuration entries
    multiapps   2.4.0     undeploy                     Undeploy a multi-target app
    ```

3.  Set the target API end point for the Cloud Foundry “Controller” to which you want to connect.

    Run the following command in a command shell:

    ```
    $ cf api https://api.cf.<host.name>
    ```

    > ### Tip:  
    > For example, the API end point for the Cloud Controller is a URL in the following form: `https://api.cf.eu007.hana.ondemand.com`.

4.  Log on to Cloud Foundry.

    Run the following CF command in a command shell:

    ```
    $ cf login
    ```

    > ### Note:  
    > When prompted, you will need to provide the name of a registered Cloud Foundry user and a corresponding password.

5.  Have a quick look around the Cloud Foundry environment.

    List the organizations available:

    ```
    cf orgs
    Getting orgs as user.name@acme.com...
    
    name
    myOrgName
    ```

    List the organization's users:

    ```
    cf org-users myOrgName -a
    Getting users in org myOrgName as user.name@acme.com...
    
    USERS
      user.name@acme.com
    ```

    List the spaces available in an organization:

    ```
    cf spaces myOrgName
    Getting spaces as user.name@acme.com...
    
    name
    Dev
    ```

    Set the target organization and space for login:

    ```
    cf target -o <ORG> -s <SPACE> 
    ```

    List the applications running in the current space:

    ```
    cf apps
    Getting apps in org myOrgName as user.name@acme.com...
    ```

    List the services available in the service marketplace:

    ```
    cf marketplace
    Getting services from marketplace in org myOrgName / space dev as user.name@acme.com...
    OK
    
    service             plans                 description                              broker
    xsuaa               space, application,   Manage application authorizations and    sm-xsuaa-9e...
                        broker, apiaccess     trust to identity providers.
    application logs    lite                  Create, store, access, and analyze       sleeve-broker
                                              application logs.  
    ...
    ```

    Display details of a specific service:

    ```
    cf marketplace -s xsuaa
    Getting service plan information for service xsuaa as user.name@acme.com...
    OK
    
    service plan   description                                              free or paid
    application    Application plan to be used for business applications    free
    ...
    ```


**Related Information**  


[Download and Install the Cloud Foundry CLI client](download-and-install-the-cloud-foundry-cli-client-c9f777d.md "Set up the Cloud Foundry Command Line Interface (CLI)")

