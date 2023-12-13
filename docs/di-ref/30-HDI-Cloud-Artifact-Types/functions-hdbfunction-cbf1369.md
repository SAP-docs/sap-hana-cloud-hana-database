<!-- loiocbf136986c98430ea50ddf4b95bc1efe -->

# Functions \(.hdbfunction\)

Transform a design-time function resource into a function database object.



The Function plug-in transforms a design-time function resource described in the `.hdbfunction` artifact into a function database object. The file format required for the `.hdbfunction` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL command `CREATE FUNCTION`, without the leading “`CREATE`”.

> ### Note:  
> The Function plug-in handles scalar and table functions, too. Virtual functions, defined in `.hdbvirtualfunction` artifacts, are handled by the Virtual Function plug-in.



<a name="loiocbf136986c98430ea50ddf4b95bc1efe__section_cb3_jwh_1hb"/>

## Example Artifact Code

The following code shows a simple example of a **scalar** function definition for SAP HANA Deployment Infrastructure \(HDI\):

> ### Code Syntax:  
> `/src/SCALAR_FUNC_ADD_MUL.hdbfunction`
> 
> ```sql
> FUNCTION "com.sap.hana.example::SCALAR_FUNC_ADD_MUL" (X DOUBLE, Y DOUBLE) 
> RETURNS RESULT_ADD DOUBLE, RESULT_MUL DOUBLE 
> LANGUAGE SQLSCRIPT 
> AS 
> BEGIN 
>   RESULT_ADD := :X + :Y; 
>   RESULT_MUL := :X * :Y; 
> END
> ```

The following code shows a simple example of a **table** function definition for SAP HDI:

> ### Code Syntax:  
> `/src/TABLE_FUNC_SCALE.hdbfunction`
> 
> ```sql
> FUNCTION "com.sap.hana.example::TABLE_FUNC_SCALE" (VAL CHAR) 
> RETURNS TABLE (A INT, B INT) 
> LANGUAGE SQLSCRIPT 
> AS 
> BEGIN 
>   RETURN SELECT A, :VAL * B AS B FROM MYTABLE; 
> END
> ```



<a name="loiocbf136986c98430ea50ddf4b95bc1efe__section_ifh_3wh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbfunction" : {
>    "plugin_name" : "com.sap.hana.di.function"
>    "plugin_version": "4.0.0.0" 
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

