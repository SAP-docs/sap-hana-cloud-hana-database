<!-- loio031158f3b53342b095ab4d49ffd95a3e -->

# ALTER SYSTEM \{ENABLE | DISABLE | REMOVE\} ABSTRACT SQL PLAN \(System Management\)

Enables or disables execution plan generation for abstract SQL plans, or removes plans from the ABSTRACT\_SQL\_PLANS table.



<a name="loio031158f3b53342b095ab4d49ffd95a3e__section_qbl_mp2_qz"/>

## Syntax

Syntax 1

```
ALTER SYSTEM { ENABLE | DISABLE | REMOVE } ABSTRACT SQL PLAN ENTRY <target>
```

Syntax 2

```
ALTER SYSTEM REMOVE ABSTRACT SQL PLAN RELATED OBJECT DEFINITION { ALL | INVALID }
```



<a name="loio031158f3b53342b095ab4d49ffd95a3e__section_ryc_s4y_pz"/>

## Syntax Elements


<dl>
<dt><b>

RELATED OBJECT DEFINITION \{ ALL | INVALID \}

</b></dt>
<dd>

Clears the stored definitions for the related objects of the captured plan.


<dl>
<dt><b>

ALL

</b></dt>
<dd>

Removes all related object definitions of the captured plan.



</dd><dt><b>

INVALID

</b></dt>
<dd>

Removes only invalid related object definitions of the captured plan.



</dd>
</dl>



</dd><dt><b>

*<target\>*

</b></dt>
<dd>

Specifies the scope of action.

```
<target> ::= ALL | FOR <id_list>
```

```
<id_list> ::= <plan_id> [, <plan_id> [,...] ]
```


<dl>
<dt><b>

*<id\_list\>*

</b></dt>
<dd>

Specifies the plans to which the action applies.


<table>
<tr>
<th valign="top">

Action

</th>
<th valign="top">

Behavior

</th>
</tr>
<tr>
<td valign="top">

ENABLE

</td>
<td valign="top">

Enable the abstract SQL plan entries specified in the *<id\_list\>*. If multiple abstract SQL plan entries of the same query are specified in the *<id\_list\>*, then the last entry of the same query in the list is enabled.

</td>
</tr>
<tr>
<td valign="top">

DISABLE

</td>
<td valign="top">

Disable the abstract SQL plan entries specified in the *<id\_list\>*.

</td>
</tr>
<tr>
<td valign="top">

REMOVE

</td>
<td valign="top">

Remove the abstract SQL plan entries specified in the *<id\_list\>*.

</td>
</tr>
</table>



</dd>
</dl>


<dl>
<dt><b>

ALL

</b></dt>
<dd>

ALL applies the action to all abstract SQL plans.


<table>
<tr>
<th valign="top">

Action

</th>
<th valign="top">

Behavior

</th>
</tr>
<tr>
<td valign="top">

ENABLE

</td>
<td valign="top">

For each abstract SQL plan query that does not have any enabled entry, enable the first captured entry.

</td>
</tr>
<tr>
<td valign="top">

DISABLE

</td>
<td valign="top">

Disable all enabled abstract SQL plan entries.

</td>
</tr>
<tr>
<td valign="top">

REMOVE

</td>
<td valign="top">

Remove all abstract SQL plan entries.

</td>
</tr>
</table>



</dd>
</dl>



</dd>
</dl>



<a name="loio031158f3b53342b095ab4d49ffd95a3e__section_ifw_xsz_pz"/>

## Description

This statement controls optimizer access to abstract SQL plans.

When ENABLE or DISABLE are specified in the ABSTRACT SQL PLAN ENTRY ALL statement, any captured plans specified by*<target\>* are expelled. When REMOVE is specified in the ABSTRACT SQL PLAN ENTRY ALL statement, any captured plans referenced by *<target\>* with a status of are expelled.



<a name="loio031158f3b53342b095ab4d49ffd95a3e__section_jfw_xsz_pz"/>

## Example

The following example removes all abstract SQL plans:

```
ALTER SYSTEM REMOVE ABSTRACT SQL PLAN ENTRY ALL;
```

The following example enables the single abstract SQL plan with ID 9630002 for use by the optimizer:

```
ALTER SYSTEM ENABLE ABSTRACT SQL PLAN ENTRY FOR 9630002;
```

The following example removes all related object definitions from the captured plan.

```
ALTER SYSTEM REMOVE ABSTRACT SQL PLAN RELATED OBJECT DEFINITION ALL;
```

**Related Information**  


[SQL Plan Stability](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/deab4aee414e4b00a3df5666a44adfff.html "SQL Plan Stability can be used to guarantee the consistent optimal performance of select statements by capturing query execution plans so that exactly the same plan can be reused when the query is executed again.") :arrow_upper_right:

[ALTER SYSTEM \{ADD | REMOVE\} ABSTRACT SQL PLAN FILTER \(System Management\)](alter-system-add-remove-abstract-sql-plan-filter-system-management-9c6ac16.md "Starts or stops capturing abstract SQL plans for queries that match the specified filters.")

[ALTER SYSTEM \{START | STOP\} CAPTURE ABSTRACT SQL PLAN \(System Management\)](alter-system-start-stop-capture-abstract-sql-plan-system-management-dc46271.md "Starts or stops capturing abstract SQL plans for queries that are executed against the database.")

[ALTER SYSTEM \{START | STOP\} APPLY ABSTRACT SQL PLAN \(System Management\)](alter-system-start-stop-apply-abstract-sql-plan-system-management-935ecd1.md "Starts or stops matching executed queries with captured abstract SQL plans.")

[ABSTRACT\_SQL\_PLANS System View](../../020-System-Views-Reference/021-System-Views/abstract-sql-plans-system-view-ba830ef.md "Lists information about abstract SQL plans.")

[M\_ABSTRACT\_SQL\_PLAN\_OVERVIEW System View](../../020-System-Views-Reference/022-Monitoring-Views/m-abstract-sql-plan-overview-system-view-03aa3ad.md "Provides the status of each Plan Stability Manager on every index server in SAP HANA.")

[M\_ABSTRACT\_SQL\_PLAN\_STATISTICS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-abstract-sql-plan-statistics-system-view-35af7f2.md "Provides SQL query runtime statistics.")

