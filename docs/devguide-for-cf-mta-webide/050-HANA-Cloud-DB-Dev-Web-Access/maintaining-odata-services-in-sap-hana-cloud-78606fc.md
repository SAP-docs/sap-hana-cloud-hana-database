<!-- loio78606fc13a6b41e5b654ca5f289351ca -->

# Maintaining OData Services in SAP HANA Cloud

Define OData services for your Java and JavaScript multitarget applications in SAP HANA Cloud.

In your multitarget application, you can create OData services that use either OData version 2.0 or OData version 4.0.

OData version 2.0 is the basis for the XSODATA service infrastructure used in SAP HANA extended application services. XSODATA services can also be used in Cloud Foundry with the so-called XS compatibility layer, a Node package \(`@sap/xsjs`\) that enables SAP HANA XS applications to run in the JavaScript run time on Cloud Foundry. For more information about `@sap/xsjs`, see *Standard SAP Node.js Packages* in *Related Information* below.

> ### Note:  
> The XSODATA infrastructure for OData services based on OData version 2 will no longer be extended or improved, In addition, XSODATA does not support SAP HANA Cloud services, as described in SAP note: [3013788](https://me.sap.com/notes/3013788). For new OData services, it is recommended to move to OData version 4 or, alternatively, switch to the new SAP Cloud application programming model mentioned below.

The OData version your multitarget applications can consume is determined by the programming model you use to develop the application, for example, Cloud Foundry or SAP Cloud application programming model, as described in the following list:

-   SAP Cloud Application Programming Model \(CAP\)

    The SAP Cloud application programming model is now the recommended model for new applications that make use of OData services. This programming model provides both Java and JavaScript APIs that enable the easy use and integration of either OData v 2.0 or v 4.0 services.

-   Cloud Foundry application programming model:
    -   JavaScript & Node.js

        For JavaScript and Node.js applications, you can define an XS OData service using OData version 2.0, for example, `myOdataV2Service.xsodata`. However, since there are no plans to extend or improve the underlying XSOData infrastructure, and for the sake of future compatibility, it is recommended to use the new SAP Cloud application programming model for your OData services in this scenario.



**Related Information**  


[Defining OData v2 Services for JavaScript Applications](defining-odata-v2-services-for-javascript-applications-5792055.md "Create the OData service definitions consumed by your multitarget JavaScript application.")

[Standard SAP Node.js Packages](../060-HANA-Cloud-DB-Dev-App-Code/standard-sap-node-js-packages-5451327.md "A collection of Node.js packages developed by SAP is provided to help you develop Node.js applications for Cloud Foundry and SAP HANA Cloud.")

[Working with the SAP Cloud Application Programming Model](../020-HANA-Cloud-DB-Dev-Get-Started/working-with-the-sap-cloud-application-programming-model-166f4fb.md "Create a business application using the SAP Cloud Application Programming model.")

[SAP Note 3013788](https://me.sap.com/notes/3013788 "XSODATA not supported in SAP HANA Cloud Service")

