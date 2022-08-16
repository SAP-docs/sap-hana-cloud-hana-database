<!-- loiof33557bc693e42f393024958d52cd797 -->

# Deploy a Multitarget Application with Zero-Downtime Maintenance

Update an application that has database changes without any downtime.



<a name="loiof33557bc693e42f393024958d52cd797__prereq_sf4_nk5_1cb"/>

## Prerequisites

-   The applications use HDI containers for persistence
-   The application does not use a hard coded service name for the data source to the HDI service.



## Context

When performing a blue-green deployment using the zero-downtime-maintenance \(ZDM\) deployment scenario, you can update an application that has database changes between the existing \(blue\) and the new \(green\) versions of the application. To update your application using the ZDM scenario, proceed as follows:



<a name="loiof33557bc693e42f393024958d52cd797__steps_l2x_fx4_fdb"/>

## Procedure

1.  Define the `com.sap.xs.hdi-container` resource type in the application's deployment descriptor.

    > ### Sample Code:  
    > ```
    > _schema-version: 2.0.0
    > ID: com.sap.xs2.samples.javahelloworld
    > 
    > version: 0.1.0
    > 
    > modules:
    > ...
    > 
    > resources:
    >   - name: java-hdi-container
    >     type: com.sap.xs.hdi-container
    > 
    > ...
    > ```

2.  Run the deployment in ZDM mode.

    To enable zero-downtime-maintenance mode, you must declare the value `zdm-mode:true` as a parameter value of the `com.sap.xs.hdi` module type, as illustrated in the following example.

    > ### Note:  
    > You can define ZDM mode either in the application's deployment descriptor or in an extension descriptor.

    > ### Sample Code:  
    > ```
    > _schema-version: 2.0.0
    > ID: com.sap.xs2.samples.javahelloworld
    > 
    > version: 0.1.0
    > 
    > modules:
    > ...
    >   - name: java-hello-world-db
    >     type: com.sap.xs.hdi
    >     path: db/
    >     parameters:
    >       zdm-mode: true
    >     requires:
    >       - name: java-hdi-container
    > 
    > resources:
    >   - name: java-hdi-container
    >     type: com.sap.xs.hdi-container
    > ...
    > ```

3.  To start the ZDM deployment, follow the steps described in *Deploy an MTA with Blue-Green Deployment*.

    For more information, see *Related Information*.


**Related Information**  


[Deploy a Multitarget Application with Blue-Green Deployment](deploy-a-multitarget-application-with-blue-green-deployment-0cb13f1.md "The deploy service supports the blue-green deployment of stateless applications modeled as a multitarget application (MTA).")

[Zero-Downtime Maintenance with Multitarget Applications](zero-downtime-maintenance-with-multitarget-applications-a7afca8.md "The deploy service supports application updates using zero-downtime maintenance (ZDM).")

[HDI Artifacts and Database Changes Supported by ZDM](hdi-artifacts-and-database-changes-supported-by-zdm-58ff82e.md "Zero-downtime maintenance (ZDM) supports the HDI artifacts and database changes listed in this topic.")

