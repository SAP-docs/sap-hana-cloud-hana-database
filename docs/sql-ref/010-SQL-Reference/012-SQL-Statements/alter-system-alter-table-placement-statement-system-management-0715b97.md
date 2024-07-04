<!-- loio0715b97c91cd4c87982040cdd341d676 -->

# ALTER SYSTEM ALTER TABLE PLACEMENT Statement \(System Management\)

Changes table classification and placement settings for table groups.



## Syntax

```
ALTER SYSTEM ALTER TABLE PLACEMENT [ ( <table_classification_settings> ) ] [ SET | UNSET ] [ ( <table_placement_settings> ) ]
| ALTER SYSTEM ALTER TABLE PLACEMENT LOCATION <custom_location_specification>
```



## Syntax Elements


<dl>
<dt><b>

*<table\_classification\_settings\>*

</b></dt>
<dd>

Specifies one or more table group options.

```
<table_classification_settings> ::= <classification_key_value_pair> [,<...>]

<classification_key_value_pair> ::= 
 SCHEMA_NAME [=> <string_literal> ]
 | TABLE_NAME [=> <string_literal> ]
 | GROUP_NAME [=> <string_literal> ]
 | GROUP_TYPE [=> <string_literal> ]
 | SUB_TYPE [=> <string_literal> ]
```


<dl>
<dt><b>

SCHEMA\_NAME

</b></dt>
<dd>

The schema name associated with the table \(for example, SAPBWP\).



</dd><dt><b>

TABLE\_NAME

</b></dt>
<dd>

The table name \(for example, /BIC/AZFIGL00\).



</dd><dt><b>

GROUP\_NAME

</b></dt>
<dd>

The table group name \(for example, ZFIGL\).



</dd><dt><b>

GROUP\_TYPE

</b></dt>
<dd>

The table group type \(for example, sap.bw.cube\).



</dd><dt><b>

SUB\_TYPE

</b></dt>
<dd>

The table group subtype. Possible values are ACTIVE, QUEUE, or CHANGE\_LOG.



</dd>
</dl>



</dd><dt><b>

*<table\_placement\_settings\>*

</b></dt>
<dd>

Specifies one or more table group placement properties.

```
<table_placement_settings> ::= <placement_key_value_pair> [,...]

<placement_key_value_pair> ::= 
 MIN_ROWS_FOR_PARTITIONING [ => <unsigned_integer> ]
 | INITIAL_PARTITIONS [=> <unsigned_integer> ]
 | REPARTITIONING_THRESHOLD [ => <unsigned_integer> ]
 | LOCATION [ => <string_literal> ]
 | SAME_PARTITION_COUNT [ => <boolean> ]
 | DYNAMIC_RANGE_THRESHOLD [ => <unsigned_integer> ]
 | PAGE_LOADABLE [ => <boolean> ]
 | PERSISTENT_MEMORY [ => <boolean> ]
 | NUMA_NODE_INDEXES [ => <string_literal> ]
 | REPLICA_COUNT [ => <unsigned_integer> ]
 | REPLICA_TYPE [ => <string_literal> ]
 | COMPUTE_REPLICA_COUNT [ => <unsigned integer> ]
 | COMPUTE_REPLICA_TYPE [ => <string_literal> ]
 | REPLICA_LOAD_UNIT [ => <string_literal> ]
 | COMPUTE_REPLICA_LOAD_UNIT [ => <string_literal> ]
```


<dl>
<dt><b>

MIN\_ROWS\_FOR\_PARTITIONING \[ =\> *<unsigned\_integer\>* \]

</b></dt>
<dd>

Defines the minimum number of records that must exist in a table before level 1 partitioning takes place \(for example, 40,000\).



</dd><dt><b>

INITIAL\_PARTITIONS \[ =\> *<unsigned\_integer\>*\]

</b></dt>
<dd>

Defines the initial number of partitions. If the threshold value in the MIN\_ROWS\_FOR\_PARTITIONING column is exceeded, the table redistribution performs a partitioning \(for example, 3\).



</dd><dt><b>

REPARTITIONING\_THRESHOLD \[ =\> *<unsigned\_integer\>*\]

</b></dt>
<dd>

Specifies the threshold value for the number of records in a partition that triggers a repartitioning \(for example, 2,000,000,000\).

Once a table has been partitioned with the specified initial number of partitions, for performance reasons, the table is only repartitioned by doubling the number of partitions. For example, if the initial number of partitions is 3, this would result in 6 partitions being created during a repartitioning.



</dd><dt><b>

LOCATION \[=\> *<string\_literal\>*\]

</b></dt>
<dd>

Specifies a location. Valid values are:

-   One of the predefined locations:
    -   COORDINATOR \(MASTER\)
    -   WORKER \(SLAVE\)
    -   ALL
    -   DEFAULT

-   the name of a custom set of indexservers previously defined \(*<custom\_location\_specification\>*\) using the ALTER TABLE ALTER TABLE PLACEMENT LOCATION syntax.

The location \(except DEFAULT\) can be followed by a '\#' and a number, which implies that at most that many servers out of the location shall be used. For example, WORKER\#1 means that the table and partitions will be placed on one server out of the worker servers.



</dd><dt><b>

SAME\_PARTITION\_COUNT \[ =\> *<boolean\>* \]

</b></dt>
<dd>

Specifies that all partitions of the tables in a group will contain the same number of partitions.



</dd><dt><b>

DYNAMIC\_RANGE\_THRESHOLD \[ =\> *<unsigned\_integer\>* \]

</b></dt>
<dd>

Specifies the dynamic range partitioning threshold that is applied to the table partitioning specification.



</dd><dt><b>

PAGE\_LOADABLE \[ =\> *<boolean\>* \]

</b></dt>
<dd>

Specifies whether a table should be stored in NSE or not.



</dd><dt><b>

PERSISTENT\_MEMORY \[ =\> *<boolean\>* \]

</b></dt>
<dd>

Specifies whether use of persistent memory should be enabled on table.



</dd><dt><b>

NUMA\_NODE\_INDEXES \[ =\> *<string\_literal\>* \]

</b></dt>
<dd>

Specifies the NUMA node specification for the table.



</dd><dt><b>

REPLICA\_COUNT \[ =\> *<unsigned\_integer\>* \]

</b></dt>
<dd>

Specifies the number of replicas that should be set up for a table.



</dd><dt><b>

REPLICA\_TYPE \[ =\> *<string\_literal\>* \]

</b></dt>
<dd>

Specifies the type of replica. Valid values are ASYNCHRONOUS or SYNCHRONOUS.



</dd><dt><b>

COMPUTE\_REPLICA\_COUNT \[ =\> *<unsigned integer\>* \]

</b></dt>
<dd>

Specifies the replica count for compute server replicas.



</dd><dt><b>

COMPUTE\_REPLICA\_TYPE \[ =\> *<string\_literal\>* \]

</b></dt>
<dd>

Specifies the type of compute server replicas.



</dd><dt><b>

REPLICA\_LOAD\_UNIT \[ =\> *<string\_literal\>* \]

</b></dt>
<dd>

Specifies the load unit of the replica. Valid values are:

-   PAGE - load unit is page
-   COLUMN - load unit is column
-   DEFAULT - load unit is same as replica source



</dd><dt><b>

COMPUTE\_REPLICA\_LOAD\_UNIT \[ =\> *<string\_literal\>* \]

</b></dt>
<dd>

Specifies the load unit of the compute server replica. Valid values are:

-   PAGE - load unit is page
-   COLUMN - load unit is column
-   DEFAULT - load unit is same as replica source



</dd>
</dl>



</dd><dt><b>

LOCATION *<custom\_location\_specification\>*

</b></dt>
<dd>

Defines a synonym for a list of one or more SAP HANA indexservers, or groups of indexservers, by their intended use. For example, as a worker for a specific application to isolate the workload, or to define a custom subset of indexservers that host data of a specific customer. This capability relies more on volume IDs instead of host/port names.

```
LOCATION <custom_location_specification> ::= <custom_location_names> { SET <location_specification> | UNSET }
```


<dl>
<dt><b>

*<custom\_location\_names\>*

</b></dt>
<dd>

Specifies a synonym for one or more volume IDs to use for table placement. You can then reference this name when specifying table placement settings using the ALTER TABLE ALTER TABLE PLACEMENT syntax.



</dd><dt><b>

SET *<location\_specification\>*

</b></dt>
<dd>

Specifies the locations to include or exclude during table placement.

```
<location_specification> ::= { [ <include_list> [, <exclude_list> ] ] }

<include_list> ::= INCLUDE=>'[ { <preset_value> [, ...] | <volumn_id> [,...] ] }'
<exclude_list> ::= EXCLUDE=>'[ { <preset_value> [, ...] | <volumn_id> [,...] ] }'

<preset_value> ::= { COORDINATOR | ALL | DEFAULT | WORKER }
```



</dd><dt><b>

UNSET

</b></dt>
<dd>

Unsets the locations configured for the specified *<custom\_location\_specification\>*.

If *<custom\_location\_specification\>* is UNSET while also being the table placement setting currently in use, SAP HANA reverts to default table placement behaviors.



</dd>
</dl>



</dd>
</dl>



## Description

This statement allows you to set and unset attributes and placement properties for table groups. When you create a table, you can assign it to a table group. Table groups can improve the database server's ability to make decisions about how to distribute tables across servers. For example, the use of table groups can prevent frequently-joined tables from being placed on different hosts.

Table classification and the table placement settings are taken into account on two occasions: table redistribution and during table creation.

Table placement attributes and properties are stored in the TABLE\_GROUPS and TABLE\_PLACEMENT\_LOCATIONS system views and their corresponding monitoring view counterparts..



<a name="loio0715b97c91cd4c87982040cdd341d676__section_hpf_15n_wjb"/>

## Permissions

You must have the TABLE ADMIN system privilege to execute this statement.



## Examples

The following statement forces all tables to be stored on the secondary host.

```
ALTER SYSTEM ALTER TABLE PLACEMENT SET (LOCATION => 'worker');
```

The following statement forces all tables of the schema SAPKIT to be stored on the primary host.

```
ALTER SYSTEM ALTER TABLE PLACEMENT (SCHEMA_NAME => 'SAPKIT') SET (LOCATION => 'coordinator');
```

The following statement forces all tables of the schema SAPKIT and the GROUP\_TYPE `sap.bw.dso` to be stored on the secondary host with the specified properties.

```
ALTER SYSTEM ALTER TABLE PLACEMENT (SCHEMA_NAME => 'SAPKIT', GROUP_TYPE => 'sap.bw.dso') 
 SET (LOCATION => 'worker', MIN_ROWS_FOR_PARTITIONING => 40000000, REPARTITIONING_THRESHOLD => 40000000, INITIAL_PARTITIONS => 3);
```

The following example demonstrates how to unset the schema entry SAPKIT and GROUP\_TYPE `sap.bw.dso`.

```
ALTER SYSTEM ALTER TABLE PLACEMENT (SCHEMA_NAME => 'SAPKIT', GROUP_TYPE => 'sap.bw.dso') UNSET;
```

The following example demonstrates how to remove the LOCATION entry for schema SAPKIT and GROUP\_TYPE `sap.bw.dso`.

```
ALTER SYSTEM ALTER TABLE PLACEMENT (SCHEMA_NAME => 'SAPKIT', GROUP_TYPE => 'sap.bw.dso') UNSET (LOCATION);
```

The following example demonstrates how to set the SAME\_PARTITION\_COUNT table placement property for schema `SYSTEM` to `'TRUE'`.

```
ALTER SYSTEM ALTER TABLE PLACEMENT (SCHEMA_NAME=>'SYSTEM') SET (SAME_PARTITION_COUNT => 'TRUE');
```

The following example demonstrates how to unset the SAME\_PARTITION\_COUNT table placement property for schema `SYSTEM`.

```
ALTER SYSTEM ALTER TABLE PLACEMENT (SCHEMA_NAME=>'SYSTEM') UNSET (SAME_PARTITION_COUNT);
```

The following examples demonstrate how to include or exclude locations for table placement:

```
ALTER SYSTEM ALTER TABLE PLACEMENT LOCATION MyLocation SET (INCLUDE => '2,3', EXCLUDE => 'WORKER');				
ALTER SYSTEM ALTER TABLE PLACEMENT LOCATION MyLocation SET (INCLUDE => '2,3', EXCLUDE => '');
```

The following example unsets the list of locations that have been set for table placement:

```
ALTER SYSTEM ALTER TABLE PLACEMENT LOCATION MyLocation UNSET;
```

**Related Information**  


[Table Placement](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/22888f9344954f258284d2dd936d0d0a.html "Table classification and table placement configuration, enhanced by partitioning, build the foundation for controlling the data distribution in a SAP HANA scale-out environment.") :arrow_upper_right:

[TABLE\_PLACEMENT System View](../../020-System-Views-Reference/021-System-Views/table-placement-system-view-522cc8e.md "Provides table placement information.")

[M\_EFFECTIVE\_TABLE\_PLACEMENT System View](../../020-System-Views-Reference/022-Monitoring-Views/m-effective-table-placement-system-view-f3f74ec.md "Provides information about effective placement of tables.")

[M\_TABLE\_PLACEMENT\_LOCATIONS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-table-placement-locations-system-view-7ecc1cc.md "Provides table placement location monitoring information.")

[TABLE\_GROUPS System View](../../020-System-Views-Reference/021-System-Views/table-groups-system-view-210103b.md "Provides an overview of table group relationships.")

