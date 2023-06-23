<!-- loiobda54706fbda4910908871743b675ad1 -->

# Constraints \(.hdbconstraint\)

Transform a design-time constraint into a constraint on database tables.



The foreign-key constraint plug-in transforms a design-time constraint \(defined in a `.hdbconstraint` artifact\) into a constraint on database tables. The file format required for the design-time `.hdbconstraint` artifact uses a DDL-style syntax that is similar to the SQL syntax in the corresponding SQL command `ALTER TABLE ADD CONSTRAINT`. However, to be consistent with other DDL-style artifacts, in the design-time definition specified in the `.hdbconstraint` file, the constraint is specified in the following way: <code>CONSTRAINT <i class="varname">&lt;myConstraint&gt;</i> ON table [...]</code>, as illustrated in the example below.

> ### Restriction:  
> The constraint plug-in only supports `FOREIGN KEY` constraints. Unique constraints are handled by the `.hdbindex` plugin.



<a name="loiobda54706fbda4910908871743b675ad1__section_kmb_w5h_1hb"/>

## Example Artifact Code

The following code shows a simple example of a foreign-key constraint definition for HDI:

> ### Code Syntax:  
> `/src/A_CONSTRAINT.hdbconstraint`
> 
> ```sql
> CONSTRAINT A_CONSTRAINT 
> ON BASE_TABLE 
> FOREIGN KEY (FIELD) REFERENCES OTHER_TABLE (FIELD) ON UPDATE CASCADE
> ```

> ### Tip:  
> Unique constraints are handled by the `.hdbindex` plugin.



<a name="loiobda54706fbda4910908871743b675ad1__section_a1b_v5h_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plugin configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbconstraint" : {
>    "plugin_name" : "com.sap.hana.di.constraint"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

