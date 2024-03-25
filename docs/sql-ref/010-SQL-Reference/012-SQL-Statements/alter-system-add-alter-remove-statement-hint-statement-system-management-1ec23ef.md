<!-- loio1ec23ef0839b45b7991a785eff19fd2c -->

# ALTER SYSTEM \{ADD | ALTER | REMOVE\} STATEMENT HINT Statement \(System Management\)

Adds, alters, or removes statement hints from the system to a specified query or statement hash.



## Syntax

```
ALTER SYSTEM 
   { ADD STATEMENT HINT ( [ <hint_list> ] ) [ [ NO ] OVERRIDE ] [ COMMENT <comment> ] <statement_hint_target>
   | ALTER STATEMENT HINT [ [ NO ] OVERRIDE ] [ COMMENT <comment> ] <statement_hint_target>
   | REMOVE STATEMENT HINT [ ALL ] <statement_hint_target> }
```



## Syntax Elements


<dl>
<dt><b>

ADD STATEMENT HINT

</b></dt>
<dd>

Adds hints specified in the *<hints\_list\>* to the specified target query or statement hash as a key. Separate multiple hints on the *<hints\_list\>* by a comma.

Evicts all cached plans for the target SQL statements that do not have the pattern symbols. For SQL statements using the pattern symbols, existing cached plans must be evicted manually prior to adding a hint.



</dd><dt><b>

REMOVE STATEMENT HINT

</b></dt>
<dd>

Removes statement hints from the system that match the specified target query or statement hash. If there are system hints, and the ALL option is not specified, then instead of removing the statement hints from the system, REMOVE STATEMENT HINT replaces the current user hints with the system hints. If the ALL option is specified, the statement removes the user hints and the system hints together with the specified SQL statement string. If ALL and *<statement\_hash\>* are specified, then user hints, system hints and the statement hash are removed. If *<statement\_hash\>* is specified without ALL, then the current user hints are replaced with the system hints.

Evicts all cached plans for the target SQL statements that do not have the pattern symbols. For SQL statements using the pattern symbols, existing cached plans must be evicted manually.



</dd><dt><b>

*<hint\_list\>*

</b></dt>
<dd>

Specifies a set of hints that are applied to the target query or statement\_hash.

```
<hint_list> ::= <hint> [,... ]
```



</dd><dt><b>

*<statement\_hint\_target\>*

</b></dt>
<dd>

Specifies the target of the hints to apply.

```
<statement_hint_target> ::= 
   { [ ON { PROCEDURE | FUNCTION } <proc_func_name> ] FOR <target_query> 
   | FOR STATEMENT HASH <statement_hash> }
```


<dl>
<dt><b>

ON \{ PROCEDURE | FUNCTION \} *<proc\_func\_name\>*

</b></dt>
<dd>

If a statement is specified as the target with the corresponding procedure/function name, the given hint is implicitly applied to the statement inside the corresponding procedure/function.

```
<proc_func_name> ::= [ <schema_name>.]<identifier>
```



</dd><dt><b>

*<target\_query\>*

</b></dt>
<dd>

Specifies the target query.



</dd><dt><b>

*<statement\_hash\>*

</b></dt>
<dd>

Specifies the statement hash.



</dd>
</dl>



</dd><dt><b>

\[ NO \] OVERRIDE

</b></dt>
<dd>

Specifies whether to use a hint override with *<statement\_hint\_target\>*. When OVERRIDE is specified, the hints specified in *<hint\_list\>* override any hints specified in *<statement\_hint\_target\>* \(e.g,`SELECT * FROM myView WITH HINT (NO_CS_JOIN)`.



</dd><dt><b>

COMMENT *<comment\>*

</b></dt>
<dd>

Specifies a comment to add to the STATEMENT\_HINTS system view when *<hint\_list\>* is applied to *<statement\_hint\_target\>*.



</dd><dt><b>

ALL

</b></dt>
<dd>

Removes all hints \(user-defined and system from the system that are associated with the specified *<statement\_hint\_target\>*. If ALL is not specified, then only the user-defined hints are removed. If ALL and *<statement\_hash\>* are specified, then user hints, system hints and the statement hash are removed. If *<statement\_hash\>* is specified without ALL, then the current user hints are replaced with the system hints.



</dd>
</dl>



## Description

In a statement hint entry, there are two kinds of hints: system and user. User hints are the hints added by users with the ADD STATEMENT HINT defined above. System hints are the hints provided by the system by default when the system is upgraded.

In the case of conflicts, for example if user hints are already specified in the system for the SQL statement to which the system hints will be applied during the system upgrade, then the user hints stay in the system and the system hints are kept for later usage.

In the case of *<hints\_list\>* conflicts, for example USE\_OLAP\_PLAN and NO\_USE\_OLAP\_PLAN, all hints are added to the target query without precedence or conflict resolution. This may cause queries to incur undefined behavior. Behavior is dependent on the implementation of each hint, making the result of the query containing the conflicts undeterminable.

to the SQLScript plan generation.

The pattern symbol $$?$$ can be used in ALTER SYSTEM...STATEMENT HINT commands for add, remote, enable, and disable statement hints with a simple pattern.

```
ALTER SYSTEM ADD STATEMENT HINT (NO_USE_HEX_PLAN) FOR SELECT * FROM a WHERE a = $$?$$;
```

For example, the following two statement hints are added. Statement hints using a query without the pattern symbol are searched first.

-   ALTER SYSTEM ADD STATEMENT HINT \(HINT2\) FOR SELECT \* FROM a WHERE a = $$%$$;
-   ALTER SYSTEM ADD STATEMENT HINT \(HINT1\) FOR SELECT \* FROM a WHERE a = 1234;

So, the applied statement hints for the user queries are:

-   SELECT \* FROM a WHERE a = 1234 - HINT1 is applied
-   SELECT \* FROM a WHERE a = 5678 - HINT2 is applied



<a name="loio1ec23ef0839b45b7991a785eff19fd2c__section_tyx_nsq_xrb"/>

## Permissions

You must have the OPTIMIZER ADMIN system privilege to administer statement hints.



<a name="loio1ec23ef0839b45b7991a785eff19fd2c__section_rl2_h5h_l2b"/>

## Example

This example adds the NO\_CS\_JOIN and NO\_CS\_UNION\_ALL hints to the SELECT query.

```
ALTER SYSTEM ADD STATEMENT HINT (NO_CS_JOIN, NO_CS_UNION_ALL) FOR SELECT * FROM AAA, BBB WHERE AAA.X = BBB.X;
```

This example alters the user hints associated with the specified SELECT statement, and specifies a comment.

```
ALTER SYSTEM ALTER STATEMENT HINT COMMENT 'AAA related join' FOR SELECT * FROM AAA, BBB WHERE AAA.X = BBB.X;
```

This example specifies an overriding hint to use with the specified SELECT statement.

```
ALTER SYSTEM ALTER STATEMENT HINT COMMENT 'AAA related join' FOR SELECT * FROM AAA, BBB WHERE AAA.X = BBB.X WITH HINT (NO_CS_JOIN);
```

This example removes all user hints associated with the specified SELECT statement.

```
ALTER SYSTEM REMOVE STATEMENT HINT FOR SELECT * FROM AAA, BBB WHERE AAA.X = BBB.X;
```

This example adds the NO\_CS\_JOIN hint to the statement hash 36896ef08346b8321f88449d5c5e97f8.

```
ALTER SYSTEM ADD STATEMENT HINT (NO_CS_JOIN) FOR STATEMENT HASH '36896ef08346b8321f88449d5c5e97f8';
```

This example removes all user hints associated with the statement hash 36896ef08346b8321f88449d5c5e97f8.

```
ALTER SYSTEM REMOVE STATEMENT HINT FOR STATEMENT HASH '36896ef08346b8321f88449d5c5e97f8';
```

This example removes all user and system hints and the statement hash 36896ef08346b8321f88449d5c5e97f8.

```
ALTER SYSTEM REMOVE STATEMENT HINT ALL FOR STATEMENT HASH '36896ef08346b8321f88449d5c5e97f8';
```

This example adds the NO\_CS\_JOIN, NO\_CS\_UNION\_ALL hints on the MY\_PROC procedure using the target query SELECT \* FROM :TVAR AAA, BBB WHERE AAA.X = BBB.X.

```
ALTER SYSTEM ADD STATEMENT HINT (NO_CS_JOIN, NO_CS_UNION_ALL) ON PROCEDURE MY_PROC FOR SELECT * FROM :TVAR AAA, BBB WHERE AAA.X = BBB.X;
```

**Related Information**  


[ALTER SYSTEM \{ENABLE | DISABLE\} STATEMENT HINT Statement \(System Management\)](alter-system-enable-disable-statement-hint-statement-system-management-8505e6f.md "Enables or disables hints from a target query or statement hash.")

[STATEMENT\_HINTS System View](../../020-System-Views-Reference/021-System-Views/statement-hints-system-view-161a91a.md "Provides information about statement hints, including when they were last enabled and/or disabled and by whom.")

[Managing and Monitoring SAP HANA Cloud](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/5c3891048fa44d6983801e0aeaf9af38.html "In addition to the administration tools in the SAP HANA cockpit and SAP HANA Cloud Central, other resources are introduced here that are available to help monitor and improve the performance of your database.") :arrow_upper_right:

