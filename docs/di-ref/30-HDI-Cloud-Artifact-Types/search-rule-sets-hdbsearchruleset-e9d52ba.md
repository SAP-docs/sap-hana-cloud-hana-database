<!-- loioe9d52ba816b04577a450f87032d7dbda -->

# Search Rule Sets \(.hdbsearchruleset\)

Creates search configurations that can be consumed with a built-in database procedure.



The Search Rule Set plug-in creates search configurations defined in design-time `.hdbsearchruleset` artifacts which can be consumed with the built-in database procedure `SYS.EXECUTE_SEARCH_RULE_SET`. The format of the `.hdbsearchruleset` design-time artifact that defines the search-rule configuration is based on XML. Search configurations define rules that describe when a row will be returned as a search result.

> ### Note:  
> To use the search configuration, `EXECUTE` privileges on `SYS.EXECUTE_SEARCH_RULE_SET` are required.



<a name="loioe9d52ba816b04577a450f87032d7dbda__section_qt1_1zh_1hb"/>

## Example Artifact Code

The following code shows a simple example of a design-time definition of a search rule set for SAP HDI:

> ### Code Syntax:  
> `/SRS.hdbsearchruleset`
> 
> ```xml
> <?xml version="1.0" encoding="UTF-8"?>
> <SearchRuleSet:ruleSet xmlns:SearchRuleSet="http://www.sap.com/ndb/SearchRuleSet.ecore" scoreSelection="firstRule">
>   <attributeView name="p1.p2.p3::aView">
>     <keyColumn name="id1"/>
>     <keyColumn name="id2"/>
>   </attributeView>
>   <rule name="Rule 1">
>     <column minFuzziness="0.7" name="firstName" weight="0.9">
>       <textColumnOptions abbreviationSimilarity="0.9"/>
>     </column>
>     <column minFuzziness="1.0" name="lastName">
>       <textColumnOptions/>
>     </column>
>     <column minFuzziness="0.8" name="street">
>       <stringColumnOptions/>
>     </column>
>     <column minFuzziness="0.8" name="city">
>       <stringColumnOptions/>
>     </column>
>   </rule>
>   <rule name="Rule 1">
>     <column minFuzziness="1.0" name="firstName">
>       <textColumnOptions/>
>     </column>
>     <column minFuzziness="1.0" name="lastName">
>       <textColumnOptions/>
>     </column>
>     <column minFuzziness="0.8" name="dateOfBirth">
>       <dateColumnOptions maxDateDistance="5"/>
>     </column>
>   </rule>
> </SearchRuleSet:ruleSet>
> 
> ```

> ### Tip:  
> For examples showing the content and format of the `.hdbsearchruleset` artifact, see the *SAP HANA Search Developer Guide* in the *Related Links* below.



<a name="loioe9d52ba816b04577a450f87032d7dbda__section_ofx_yyh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbsearchruleset" : {
>    "plugin_name" : "com.sap.hana.di.searchruleset", 
>    "plugin_version": "4.0.0.0" 
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

