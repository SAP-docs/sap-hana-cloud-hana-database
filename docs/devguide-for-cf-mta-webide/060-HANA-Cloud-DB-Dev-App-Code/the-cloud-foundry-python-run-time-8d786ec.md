<!-- loio8d786ec8ab964145a7453c1f53f452db -->

# The Cloud Foundry Python Run Time

SAP Business Technology Platform provides a Cloud Foundry Python run time to which you can deploy your Python applications.

A buildpack is available for you to deploy your Python code to the Cloud Foundry run-time environment on SAP Business Technology Platform. However, unlike Java and Node.js, there are no pre-built Python run-time binaries. This means that you have to deploy your own Python run-time version prior to application deployment. During application deployment, the build pack ensures that this run time is provided to the application and that the correct certificates, configuration, and environment is set for your application.

> ### Note:  
> The run-time platform makes no assumptions about which frameworks and libraries to use to implement the Python micro service.

The following components help build a Python micro service:

-   Setup of the SAP HANA Cloud client for communication with SAP HANA Cloud
-   A Python library to support JSON Web Tokens \(JWT\) validation

    Used for communication between the application router, micro services, and the database

-   A Python client for communication with the Audit Log service
-   A Python library for creating and deleting service instances per tenant within an application during run time

**Related Information**  


[Set up the Python Run Time for Cloud Foundry](set-up-the-python-run-time-for-cloud-foundry-d3eb423.md "Find information about how to set up the Python run time for your Python applications.")

[Download and Consume Python Libraries](download-and-consume-python-libraries-842824f.md "Python client libraries developed by SAP on the Python Package Index (PyPI).")

[Tutorials: Setting Up the Python Run Time](tutorials-setting-up-the-python-run-time-7c9e4a6.md "Tutorials that show you how to set up Python applications for Cloud Foundry.")

[Python Application Programming \(SAP HANA Client Interface Programming Reference\)](https://help.sap.com/docs/SAP_HANA_CLIENT/f1b440ded6144a54ada97ff95dac7adf/f3b8fabf34324302b123297cdbe710f0.html)

