<!-- loio9c6ac161c9d8492f9d55c9cff38fb17f -->

# ALTER SYSTEM \{ADD | REMOVE\} ABSTRACT SQL PLAN FILTER \(System Management\)

Starts or stops capturing abstract SQL plans for queries that match the specified filters.



## Syntax

```
ALTER SYSTEM ADD ABSTRACT SQL PLAN FILTER <filter_name>
   SET <predicate_list>

| ALTER SYSTEM REMOVE ABSTRACT SQL PLAN FILTER <target_filter>
```



## Syntax Element


<dl>
<dt><b>

*<filter\_name\>*

</b></dt>
<dd>

Specifies the name of the filter.

```
<filter_name>::= <string_literal>
```



</dd>
<dd>


<dl>
<dt><b>

SET *<predicate\_list\>*

</b></dt>
<dd>

Specifies the predicates that must be matched for the filter to be applied.

```
<predicate_list>::= <predicate>[, <predicate>...]

<predicate>::= '<key>' = '<value>'

<key>::= APPLICATION USER NAME
   | APPLICATION NAME
   | USER NAME
   | SCHEMA NAME
   | XS APPLICATION USER NAME

<value>::= <string_literal>
```



</dd>
</dl>



</dd><dt><b>

REMOVE

</b></dt>
<dd>

Removes the specified abstract SQL plan filter.


<dl>
<dt><b>

*<target\_filter\>*

</b></dt>
<dd>

Specifies the name of a specific filter to remove or that all filters should be removed.

```
<target_filter>::= <filter_name> | ALL
```



</dd>
</dl>



</dd>
</dl>



## Description

Abstract SQL plans are captured for queries that all of the specified predicates for a filter. If there are multiple filters defined, then a query is checked against all filters, and if the query matches any filter, the query is captured.



## Example

The following example defines a filter that captures abstract SQL plans for applications named App1.

```
ALTER SYSTEM ADD ABSTRACT SQL PLAN FILTER 'abc' SET 'APPLICATION NAME'='App1';

```

The following example defines a filter that captures abstract SQL plans for applications named App1 or with the application user name TEST.

```
ALTER SYSTEM ADD ABSTRACT SQL PLAN FILTER 'def' SET 'APPLICATION NAME'='App2', 'APPLICATION USER NAME'='TEST’;

```

The following example deletes the filter named abc.

```
ALTER SYSTEM REMOVE ABSTRACT SQL PLAN FILTER 'abc';
```

The following example deletes all filters that have been defined.

```
ALTER SYSTEM REMOVE ABSTRACT SQL PLAN FILTER ALL;
```

**Related Information**  


[SQL Plan Stability](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/deab4aee414e4b00a3df5666a44adfff.html "SQL Plan Stability can be used to guarantee the consistent optimal performance of select statements by capturing query execution plans so that exactly the same plan can be reused when the query is executed again.") :arrow_upper_right:

[ALTER SYSTEM \{ADD | REMOVE\} ABSTRACT SQL PLAN FILTER \(System Management\)](alter-system-add-remove-abstract-sql-plan-filter-system-management-9c6ac16.md "Starts or stops capturing abstract SQL plans for queries that match the specified filters.")

[ALTER SYSTEM \{ENABLE | DISABLE | REMOVE\} ABSTRACT SQL PLAN \(System Management\)](alter-system-enable-disable-remove-abstract-sql-plan-system-management-031158f.md "Enables or disables execution plan generation for abstract SQL plans, or removes plans from the ABSTRACT_SQL_PLANS table.")

[ALTER SYSTEM \{START | STOP\} APPLY ABSTRACT SQL PLAN \(System Management\)](alter-system-start-stop-apply-abstract-sql-plan-system-management-935ecd1.md "Starts or stops matching executed queries with captured abstract SQL plans.")

[ABSTRACT\_SQL\_PLANS System View](../../020-System-Views-Reference/021-System-Views/abstract-sql-plans-system-view-ba830ef.md "Lists information about abstract SQL plans.")

[M\_ABSTRACT\_SQL\_PLAN\_OVERVIEW System View](../../020-System-Views-Reference/022-Monitoring-Views/m-abstract-sql-plan-overview-system-view-03aa3ad.md "Provides the status of each Plan Stability Manager on every index server in SAP HANA.")

[M\_ABSTRACT\_SQL\_PLAN\_STATISTICS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-abstract-sql-plan-statistics-system-view-35af7f2.md "Provides SQL query runtime statistics.")

