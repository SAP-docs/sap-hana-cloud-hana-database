<!-- loio897bc02cfb274a54a2661ffde9f97c76 -->

# DROP STRUCUTRED FILTER Statement \(Data Definition\)

Drop an existing structured filter.



<a name="loio897bc02cfb274a54a2661ffde9f97c76__section_jy5_jy4_21c"/>

## Syntax

```
DROP STRUCTURED FILTER <filter_name>
```



<a name="loio897bc02cfb274a54a2661ffde9f97c76__section_ny1_w1n_zcb"/>

## Permissions

Requires one of the following:

-   You own the underlying objects of the structured filter.
-   You have the ALTER object-level privilege on the underlying objects of the structured filter.



<a name="loio897bc02cfb274a54a2661ffde9f97c76__section_wbd_hw4_21c"/>

## Examples

This example drops the structured filter SF\_T2\_VIEW.

```
DROP STRUCTURED FILTER SF_T2_VIEW;
```

**Related Information**  


[ALTER STRUCUTRED FILTER Statement \(Data Definition\)](alter-strucutred-filter-statement-data-definition-07b14e0.md "Alter an existing a structured filter.")

[CREATE STRUCTURED FILTER Statement \(Data Definition\)](create-structured-filter-statement-data-definition-f0238ff.md "Create a structured filter to manage binding between a database object (SQL or parameterized SQL view) and static / dynamic filter condition under it.")

