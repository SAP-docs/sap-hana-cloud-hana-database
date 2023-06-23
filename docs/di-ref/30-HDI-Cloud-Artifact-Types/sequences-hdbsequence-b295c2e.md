<!-- loiob295c2e0a5d547f8b1717ad7dd52cc90 -->

# Sequences \(.hdbsequence\)

Transforms a design-time sequence resource into a sequence database object.



The sequence plug-in transforms a design-time sequence resource \(defined in a `.hdbsequence` artifact\) into a sequence database object. The file format required for the `.hdbsequence` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL command `CREATE SEQUENCE`, but without the leading “`CREATE`”. If the sequence definition contains a `RESET BY` query, then this `RESET BY` query is executed during deployment to set the sequence to its start value. Sequences **without** a `RESET BY` query are also supported.



<a name="loiob295c2e0a5d547f8b1717ad7dd52cc90__section_a3z_fzh_1hb"/>

## Example Artifact Code

The following code shows a simple example of a design-time definition of a sequence for SAP HDI:

> ### Code Syntax:  
> `/src/CUSTOMER_ID.hdbsequence`
> 
> ```sql
> SEQUENCE "com.sap.hana.example::CUSTOMER_ID" 
> RESET BY 
> SELECT IFNULL(MAX(ID), 0) + 1 FROM "com.sap.hana.example::CUSTOMERS"
> ```



<a name="loiob295c2e0a5d547f8b1717ad7dd52cc90__section_mz5_2zh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbsequence" : {
>    "plugin_name" : "com.sap.hana.di.sequence"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

