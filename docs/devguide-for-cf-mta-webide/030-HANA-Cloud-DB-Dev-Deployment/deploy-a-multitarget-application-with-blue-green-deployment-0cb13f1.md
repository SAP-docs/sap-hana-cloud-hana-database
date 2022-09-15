<!-- loio0cb13f10a70a464e840aa53723a59e71 -->

# Deploy a Multitarget Application with Blue-Green Deployment

The deploy service supports the blue-green deployment of stateless applications modeled as a multitarget application \(MTA\).



<a name="loio0cb13f10a70a464e840aa53723a59e71__context_nvv_tfx_rcb"/>

## Context

By running two identical production environments that are called “blue” and “green”, you can perform a blue-green deployment, which will eliminate the downtime and risk for your system.

> ### Restriction:  
> Blue-green deployment is supported only for Cloud Foundry applications; it is not supported for bound services, such as service instances and their configuration, workflow content, and HTML5 repository content, among others. Bear in mind that live and idle applications are both bound to the same service instances. For more information about blue-green deployment in Cloud foundry environments, see *Blue-Green Deployment of Multitarget Applications \(SAP BTP Development Guide\)* in *Related Information* below.
> 
> In the Cloud Foundry environment, the MTA deployment service does not support zero-downtime maintenance when deploying MTAs to SAP HANA Cloud databases.



<a name="loio0cb13f10a70a464e840aa53723a59e71__steps_ryh_k2m_qcb"/>

## Procedure

1.  Deploy your initial MTA \(blue version\).

    Run the following command in an CF CLI command shell:

    ```
    $ cf bg-deploy <your-mta-archive-v1>
    ```

    The deploy service performs the following actions:

    -   Creates new applications

        > ### Note:  
        > If there are already installed applications, the deploy service will add “blue” to the existing application names

    -   Creates productive routes to the blue applications

        ![](images/Blue_Application_Version_of_an_MTA_e9bebd4.png)


2.  Deploy your updated MTA \(green version\).

    Run the following command in an CF CLI command shell:

    ```
    $ cf bg-deploy <your-mta-archive-v2>
    ```

    > ### Note:  
    > The first action is that all MTA services are updated. The changes between the old and the new versions must be compatible. For example, the changes between the old and the new versions of the database tables, UAA configurations, and so on.

    The deploy service performs the following actions:

    -   Creates new applications adding “green” to the existing application names

    -   Creates temporary routes to the green applications

        ![](images/Blue-Green_with_a_Temporatry_Route_175a527.png)

    -   Interrupts the deployment process showing a message the one shown in the following example:

        > ### Output Code:  
        > User input in Cloud Foundry
        > 
        > ```
        > Process needs additional user input
        > Use "cf bg-deploy -i 469520 -a resume" to resume the process
        > Use "cf bg-deploy -i 469520 -a abort" to abort the process
        > ```


3.  Test the green application version using the temporary routes.

4.  Choose which MTA version you want to make available \(blue or green\).

    1.  To keep the initial \(blue\) version of the MTA available in the productive system, stop the blue-green deployment process.

        > ### Note:  
        > Stopping the blue-green deployment process does not automatically remove the new green versions of the application or the temporary routes assigned to them.

    2.  To make the new \(green\) version of the MTA available in the productive system, choose *Resume*.

        This performs the following actions:

        -   Maps the productive routes to the new green versions of your MTA

            ![](images/Blue-Green_Deployment_of_an_MTA_dad1523.png)

        -   Deletes the temporary routes assigned to the new green version of the MTA

        -   Deletes the “blue” version of the MTA, which was productive before

            ![](images/Green_Application_version_of_an_MTA_b1f8997.png)




**Related Information**  


[Blue-Green Deployment of Multitarget Applications \(SAP BTP Development Guide\)](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/772ab72204f04946b79ce2d962e64970.html)

