<!-- loiobdc9f7ae66134c279a5f3683bba9b361 -->

# Using Synonyms to Access External Schemas and Objects

Deploy synonyms to enable cross-container access to external objects.

The information in this section covers the following basic application-development scenarios:

-   Enable access to tables owned by a classical schema from a schema \(HDI container\).

    For example, you can enable access to an existing ERP schema from your multitarget application.

-   Enable access to tables owned by one HDI schema from another HDI schema.

    For example, you can enable one HDI container to access another HDI container, or enable a Data Warehouse application to access a schema containing data in another application's HDI container.

-   Enable access between HDI containers in the same HDI container group.

    For example, you can use an HDI container-group configuration parameter to enable access between all HDI containers in the same HDI container group. For more information, see *Related Information* below.


> ### Note:  
> For more information about authorization checks on objects with dependencies, see the *Object Privileges* section in the *SAP HANA Cloud Security Guide*, which is listed in *Related Information* below.

**Related Information**  


[Enable Access to Objects in a Classic \(non-HDI\) Schema](enable-access-to-objects-in-a-classic-non-hdi-schema-402944b.md "Use a synonym to enable access to objects in a database schema that is not managed by SAP HDI (for example, ERP).")

[Enable Access to Objects in Another HDI Container](enable-access-to-objects-in-another-hdi-container-4adba34.md "Use a synonym to enable access to another HDI container.")

[Enable and Disable Cross-Container Access for HDI in Cloud Foundry](enable-and-disable-cross-container-access-for-hdi-in-cloud-foundry-3447f97.md "Use an HDI container-group configuration parameter to enable access between HDI containers in the same HDI container group.")

[SAP HANA Cloud Security Guide \(Authorization, Object Privileges\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/c82f8d6a84c147f8b78bf6416dae7290/d6311b15a7e74e01b3f660f7d175b318.html)

