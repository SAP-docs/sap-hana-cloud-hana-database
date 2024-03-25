<!-- loiobbd06f5b88eb4d70a03a25a5c4274ec5 -->

# Triggers \(.hdbtrigger\)

Transforms a design-time trigger resource into a trigger on a database table.



The trigger plug-in transforms a design-time trigger resource \(defined in a `.hdbtrigger` artifact\) into a trigger on a database table. The file format required for the `.hdbtrigger` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL command `CREATE TRIGGER`, but without the leading `CREATE`.

> ### Note:  
> A database trigger on a table is not initiated during deployment of `.hdbtabledata` artefacts.



<a name="loiobbd06f5b88eb4d70a03a25a5c4274ec5__section_ky3_1j3_1hb"/>

## Example Artifact Code

The following code shows a simple example of a trigger definition for SAP HDI:

> ### Code Syntax:  
> `/src/TRIGGER_A.hdbtrigger`
> 
> ```sql
> TRIGGER "com.sap.hana.example::TRIGGER_A"
> AFTER DELETE ON "com.sap.hana.example::CUSTOMERS" 
> FOR EACH STATEMENT 
> BEGIN 
>   DECLARE THE_COUNT INT; 
>   SELECT COUNT(*) INTO THE_COUNT FROM "com.sap.hana.example::CUSTOMERS";
>   INSERT INTO "com.sap.hana.example::CUSTOMERS_COUNT" VALUES (THE_COUNT);
> END
> ```



<a name="loiobbd06f5b88eb4d70a03a25a5c4274ec5__section_jcn_z33_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbtrigger" : {
>    "plugin_name" : "com.sap.hana.di.trigger"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

