<!-- loio2969da89b87f4abd85fd0b5f9f5bc395 -->

# Hierarchy Functions

Hierarchy functions allow you to work with hierarchical data such as tables with rows arranged in a tree or directed graph.



SAP HANA supports three types of hierarchy functions: **generator**, **navigation**, and **scalar**.

Following is a list of the supported hierarchy functions, which you can find documentation for in the *SAP HANA Cloud, SAP HANA Database Hierarchy Developer Guide* along with complete documentation for the SAP HANA hierarchy feature.


<dl>
<dt><b>

Generator functions

</b></dt>
<dd>

-   HIERARCHY Generator Function

-   HIERARCHY\_LEVELED Generator Function

-   HIERARCHY\_SPANTREE Generator Function

-   HIERARCHY\_TEMPORAL Generator Function




</dd><dt><b>

Navigation functions

</b></dt>
<dd>

-   HIERARCHY\_ANCESTORS Navigation Function

-   HIERARCHY\_ANCESTORS\_AGGREGATE Navigation Function

-   HIERARCHY\_DESCENDANTS Navigation Function

-   HIERARCHY\_DESCENDANTS\_AGGREGATE Navigation Function

-   HIERARCHY\_SIBLINGS Navigation Function




</dd><dt><b>

Scalar functions

</b></dt>
<dd>

-   HIERARCHY\_COMPOSITE\_ID Scalar Function




</dd>
</dl>

**Related Information**  


[SAP HANA Cloud, SAP HANA Database Hierarchy Developer Guide](https://help.sap.com/viewer/09f734c2169c4661b1aa15c00022ab21/2024_1_QRC/en-US/a93c356d32ef4e7fbd6143b554278eab.html "This guide explains how to use the hierarchy functions that are an integral part of SAP HANA core functionality.") :arrow_upper_right:

[HIERARCHY Generator Function](https://help.sap.com/viewer/09f734c2169c4661b1aa15c00022ab21/2024_1_QRC/en-US/f29c70e984254a6f8df76ad84e78f123.html "Generates a hierarchy based on recursive parent-child source data.") :arrow_upper_right:

[HIERARCHY_ANCESTORS Navigation Function](https://help.sap.com/viewer/09f734c2169c4661b1aa15c00022ab21/2024_1_QRC/en-US/bdb4719140634a56bb402fd1baa0e749.html "Returns all ancestors of a set of start nodes in a hierarchy.") :arrow_upper_right:

[HIERARCHY_ANCESTORS_AGGREGATE Navigation Function](https://help.sap.com/viewer/09f734c2169c4661b1aa15c00022ab21/2024_1_QRC/en-US/7198e5891c6e4b278b98aeedbb212de7.html "Efficiently calculates aggregates along a hierarchy in a top-down direction.") :arrow_upper_right:

[HIERARCHY_COMPOSITE_ID Scalar Function](https://help.sap.com/viewer/09f734c2169c4661b1aa15c00022ab21/2024_1_QRC/en-US/3a6f2a354e1c4dbcb4a80e7024c85481.html "Concatenates multicolumn tuple-like node identifiers into single scalar values.") :arrow_upper_right:

[HIERARCHY_DESCENDANTS Navigation Function](https://help.sap.com/viewer/09f734c2169c4661b1aa15c00022ab21/2024_1_QRC/en-US/77c7e749318c4f408bfe691e363614fd.html "Returns all descendants of a set of start nodes in a hierarchy.") :arrow_upper_right:

[HIERARCHY_DESCENDANTS_AGGREGATE Navigation Function](https://help.sap.com/viewer/09f734c2169c4661b1aa15c00022ab21/2024_1_QRC/en-US/c871422f92b24351a335f4a24ec1c54f.html "Efficiently calculates aggregates along a hierarchy in a bottom-up direction.") :arrow_upper_right:

[HIERARCHY_LEVELED Generator Function](https://help.sap.com/viewer/09f734c2169c4661b1aa15c00022ab21/2024_1_QRC/en-US/5720ec4044ea4d47955a3dd21272a47b.html "Creates a hierarchy based on source data that has a leveled format.") :arrow_upper_right:

[HIERARCHY_SIBLINGS Navigation Function](https://help.sap.com/viewer/09f734c2169c4661b1aa15c00022ab21/2024_1_QRC/en-US/e5db79e07e824b5a971f5b70f23f3981.html "Returns all siblings of a set of start nodes, including the start nodes.") :arrow_upper_right:

[HIERARCHY_SPANTREE Generator Function](https://help.sap.com/viewer/09f734c2169c4661b1aa15c00022ab21/2024_1_QRC/en-US/6f17763614824969915e4329d1729047.html "Generates a hierarchy for a recursive parent-child source containing only the first shortest path between each start and result node.") :arrow_upper_right:

[HIERARCHY_TEMPORAL Generator Function](https://help.sap.com/viewer/09f734c2169c4661b1aa15c00022ab21/2024_1_QRC/en-US/0be52ba7971740feab5c0a330fced1d1.html "Generates a time-dependent hierarchy for recursive parent-child source data whose edges are additionally qualified by validity intervals.") :arrow_upper_right:

