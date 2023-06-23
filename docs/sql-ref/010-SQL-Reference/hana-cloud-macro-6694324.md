<!-- loio6694324fbf4f4e1eb3b82f32ae0ffddd -->

# HANA\_CLOUD Macro

Write syntax that distinguishes between SAP HANA Cloud and SAP HANA on premise.



<a name="loio6694324fbf4f4e1eb3b82f32ae0ffddd__sql_create_saml_provider_1sql_create_saml_provider_syntax"/>

## Syntax

```
##ifdef HANA_CLOUD
<HANA_cloud_syntax>
[ ##else 
<HANA_on_premise_syntax> ]
##endif
```



<a name="loio6694324fbf4f4e1eb3b82f32ae0ffddd__sql_create_saml_provider_1sql_create_saml_provider_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<HANA\_cloud\_syntax\>*

</b></dt>
<dd>

Syntax that is valid in SAP HANA Cloud.



</dd><dt><b>

*<HANA\_on\_premise\_syntax\>*

</b></dt>
<dd>

Syntax that is valid in SAP HANA on premise.



</dd>
</dl>



<a name="loio6694324fbf4f4e1eb3b82f32ae0ffddd__sql_create_saml_provider_1sql_create_saml_provider_description"/>

## Description

Nesting multiple instances of the macro is not supported.



<a name="loio6694324fbf4f4e1eb3b82f32ae0ffddd__sql_create_saml_provider_1sql_create_saml_provider_examples"/>

## Examples

Create a table with different datatypes for each platform.

```
CREATE TABLE T (X  
##ifdef HANA_CLOUD  
NVARCHAR(5000)
##else  
TEXT
##endif  
);
```

Select data from a different table on each platform.

```
SELECT * FROM  
##ifdef HANA_CLOUD  
cloudTable
##else  
otherTable
##endif  
;
```

Create a procedure with different definitions for each platform.

```
CREATE PROCEDURE testproc AS 
BEGIN
    ##ifdef HANA_CLOUD  
    CREATE TABLE cloudTable(d int);
    ##else  
    CREATE TABLE opremTable(d int);
    ##endif  
END;
```

