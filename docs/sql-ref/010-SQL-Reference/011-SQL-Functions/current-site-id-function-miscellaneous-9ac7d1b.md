<!-- loio9ac7d1b81eb642f98a97c9682097e44f -->

# CURRENT\_SITE\_ID Function \(Miscellaneous\)

Returns the ID of the site that is calling the function. This function is primarily for use in SAP HANA System Replication \(HSR\).



<a name="loio9ac7d1b81eb642f98a97c9682097e44f__sql_function_lower_1sql_function_lower_syntax"/>

## Syntax

```
CURRENT_SITE_ID()
```



<a name="loio9ac7d1b81eb642f98a97c9682097e44f__sql_function_lower_1sql_function_lower_description"/>

## Description

Every site in an SAP HANA System Replication \(HSR\) environment has a site ID. Calling this function in an HSR system returns the ID of the site that is calling the function. Learning the site ID is useful when you are using forced routing.

When this function is called in a non-HSR system, 0 is returned.

Do not reference the DUMMY table in the FROM clause when calling the function. Instead, reference an actual table at the target location \(for example, the *<sap\_schema\>*.SVERS table, which is the recommended table for an SAP NetWeaver ABAP environment\).

This function returns the current site ID once for every row in the table you reference \(that is, the same site ID, but once for each table row\). It is therefore recommended that you specify TOP 1 when calling the function to return the current site ID only once. See the example for how to do this.



<a name="loio9ac7d1b81eb642f98a97c9682097e44f__sql_function_lower_1sql_function_lower_examples"/>

## Example

The following fictitious example returns the ID of the site that is executing the query:

```
SELECT TOP 1 CURRENT_SITE_ID() FROM mySchema.SVERS ( RESULT_LAG('hana_sr'));
```

