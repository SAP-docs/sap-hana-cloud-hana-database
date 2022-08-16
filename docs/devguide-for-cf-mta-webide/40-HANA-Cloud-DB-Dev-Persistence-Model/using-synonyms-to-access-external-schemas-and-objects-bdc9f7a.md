<!-- loiobdc9f7ae66134c279a5f3683bba9b361 -->

# Using Synonyms to Access External Schemas and Objects

Deploy synonyms to enable cross-container access to external objects.

The information in this section covers the following basic application-development scenarios:

-   Enable access to tables owned by a classical schema from a schema \(HDI container\).

    For example, enable access to an existing ERP schema from your multitarget application.

-   Enable access to tables owned by one HDI schema from another HDI schema.

    For example, enable one HDI container to access another HDI container, or enable a Data Warehouse application to access a schema containing data in another application's HDI container.


> ### Note:  
> For more information about authorization checks on objects with dependencies, see the *Object Privileges* section in the *SAP HANA Cloud Security Guide*, which is listed in *Related Information* below.

**Related Information**  


[Enable Access to Objects in a Remote Classic Schema](enable-access-to-objects-in-a-remote-classic-schema-402944b.md "Use a synonym to enable access to objects in a remote schema that is not managed by your Cloud Foundry application (for example, ERP).")

[Enable Access to Objects in Another HDI Container](enable-access-to-objects-in-another-hdi-container-4adba34.md "Use a synonym to enable access to another HDI container.")

[SAP HANA Cloud Security Guide (Authorization, Object Privileges)](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2022_2_QRC/en-US/d6311b15a7e74e01b3f660f7d175b318.html "Object privileges are SQL privileges that are used to allow access to and modification of database objects.") :arrow_upper_right:

