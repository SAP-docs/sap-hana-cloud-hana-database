<!-- loio166f4fbbcbc64df3bd74220fd75c5b1e -->

# Working with the SAP Cloud Application Programming Model

Create a business application using the SAP Cloud Application Programming model.

The SAP Cloud Application Programming \(CAP\) Model is a framework of languages, libraries, and tools that enable you to build enterprise-grade services and applications for deployment to the SAP Business Technology Platform \(SAP BTP\). The programming model features a mix of proven and broadly adopted open-source and SAP technologies which provide a collection of best practices and solutions that are designed to help avoid recurring and repetitive tasks. The main aim behind the SAP CAP approach is to ensure that CAP projects benefit from a primary focus on domain requirements, for example, by using CAP Core Data Services \(CDS\) to capture domain knowledge and intent instead of imperative coding.

> ### Note:  
> In CAP, CDS serves as the universal modeling language for both domain models and service definitions. The CAP documentation provides a complete language reference for CAP CDS, as indicated in *Related Information* below.

To get started with SAP CAP, bear in mind the following important points:

-   Tools

    In addition to your development environment \(for example, SAP Web IDE Full-stack or SAP Business Application Studio\), you need to install the following tools:

    -   Node.js
    -   SAP Node.js package `@sap/cds-dk`
    -   SQLite \(Microsoft Windows only\)
    -   Git \(optional: to download CAP project samples\)

-   Project setup

    CAP projects have a minimal setup. As you add models, however, you can deploy them to databases, and as soon as you add a first service definition, CAP starts a fully fledged OData server. For more information about setting up CAP projects and getting started, see *Related Information* below.

-   Sample projects

    If you have Git installed, you have access to a selection of samples CAP projects. For more information about how to find and use these sample CAP projects, see *Related Information* below.

-   Troubleshooting

    CAP provides a dedicated troubleshooting guide that includes information about resolving issues with the Node.js Package Manager \(NPM\), with access permissions, with setup, and even with the CDS version used in the various application run-time environments \(JavaScript, Java\). You can also find information about security-related problems and access to your target SAP HANA Cloud instance. For more information, see *Related Information* below.


**Related Information**  


[About CAP: The SAP Cloud Application Programming Model](https://cap.cloud.sap/docs/about/)

[Getting Started with SAP CAP](https://cap.cloud.sap/docs/get-started/)

[Troubleshooting SAP CAP](https://cap.cloud.sap/docs/resources/troubleshooting)

[Sample CAP projects on GitHub](https://github.com/sap-samples/cloud-cap-samples)

[CAP CDS Language Reference](https://cap.cloud.sap/docs/cds/)

