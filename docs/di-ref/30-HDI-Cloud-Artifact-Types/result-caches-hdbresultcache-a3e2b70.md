<!-- loioa3e2b70fc35845e58aff72f992bafca7 -->

# Result Caches \(.hdbresultcache\)

Transform a DDL-based definition of a result cache into the corresponding catalog object.



The Result Cache plug-in transforms a design-time DDL-based definition of a result cache \(`.hdbresultcache`\) into a catalog-level result-cache definition. The file format required for the \(`.hdbresultcache`\) artifact uses a DDL-style syntax that is similar to the corresponding syntax for the <code>[ALTER VIEW | FUNCTION] <i class="varname">&lt;object&gt;</i> ADD CACHE</code> statement. The `.hdbresultcache` file must use an artificial cache name that includes the prefix `_SYS_CACHE#` followed by the name of the referenced view or function, as illustrated in the following example.



<a name="loioa3e2b70fc35845e58aff72f992bafca7__section_pyq_4yh_1hb"/>

## Example Artifact Code

The following code shows a simple example of a design-time definition of a result cache for HDI:

> ### Code Syntax:  
> `src/a_resultcache.hdbresultcache`
> 
> ```sql
> RESULT CACHE "_SYS_CACHE#com.sap.hana.example::A_SQL_View"
>  ON VIEW "com.sap.hana.example::A_SQL_View" 
>  WITH RETENTION 30
> ```



<a name="loioa3e2b70fc35845e58aff72f992bafca7__section_y2b_nyh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbresultcache": { 
> 	"plugin_name" : "com.sap.hana.di.resultcache"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

