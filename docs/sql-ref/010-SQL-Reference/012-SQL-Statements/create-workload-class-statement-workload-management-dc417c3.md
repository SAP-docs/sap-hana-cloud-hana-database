<!-- loiodc417c30b1b3460c8860f6c7ea2a7faa -->

# CREATE WORKLOAD CLASS Statement \(Workload Management\)

Defines workload classes.



## Syntax

```
CREATE WORKLOAD CLASS <workload_class_name> [ <inheritance> ] [ <property_list> ] [ ENABLE | DISABLE ]
```



## Syntax Elements


<dl>
<dt><b>

*<workload\_class\_name\>*

</b></dt>
<dd>

Creates the specified workload class.

```
<workload_class_name> ::= <identifier>
```



</dd><dt><b>

*<inheritance\>*

</b></dt>
<dd>

Specifies a parent workload class. A hierarchy of up to three levels is supported where a child workload class can only have one single parent.

```
<inheritance> ::= PARENT { <parent_name> | NULL }
```

A child workload class inherits the TOTAL STATEMENT MEMORY LIMIT or TOTAL STATEMENT THREAD LIMIT values from the parent workload classes. During query processing when a class or hierarchy is mapped to a statement the limit that is exceeded first is applied.

Specifying NULL unsets the parent workload class.



</dd><dt><b>

*<property\_list\>*

</b></dt>
<dd>

Defines the properties of a workload class. The properties have the format of key-value pairs.

```
property_list ::= 
   [SET | UNSET] {'<key>' = '<value>[%]' [,...] }
```

```
<key> ::= 
 PRIORITY 
 | STATEMENT TIMEOUT
 | WRITE TRANSACTION LIFETIME
 | IDLE CURSOR LIFETIME
 | STATEMENT MEMORY LIMIT 
 | STATEMENT THREAD LIMIT
 | TOTAL STATEMENT MEMORY LIMIT
 | TOTAL STATEMENT THREAD LIMIT
 | ADMISSION CONTROL REJECT CPU THRESHOLD
 | ADMISSION CONTROL REJECT MEMORY THRESHOLD
 | ADMISSION CONTROL QUEUE CPU THRESHOLD
 | ADMISSION CONTROL QUEUE MEMORY THRESHOLD
```


<dl>
<dt><b>

PRIORITY

</b></dt>
<dd>

Specifies a value from 0-9. A higher number specifies a higher priority.



</dd><dt><b>

STATEMENT TIMEOUT

</b></dt>
<dd>

Specifies an expiry time for statement execution, after which statement execution is canceled and the transaction is rolled back. The default is 0 \(no expiry\).



</dd><dt><b>

WRITE TRANSACTION LIFETIME

</b></dt>
<dd>

Specifies the duration of uncommitted write transactions, in minutes, before the connection is terminated. If this value is set to 0, then the timeout behavior is disabled.



</dd><dt><b>

IDLE CURSOR LIFETIME

</b></dt>
<dd>

Specifies the duration of cursors, in minutes, before the connection is terminated. If this value is set to 0, then the timeout behavior is disabled.



</dd><dt><b>

STATEMENT MEMORY LIMIT

</b></dt>
<dd>

Specifies a limit in GB. For example, STATEMENT MEMORY LIMIT = '2' specifies a 2 GB limit.



</dd><dt><b>

STATEMENT THREAD LIMIT

</b></dt>
<dd>

Specifies a statement concurrency limit, rather than a thread limit; SAP HANA does not impose a thread limit on statements.



</dd><dt><b>

TOTAL STATEMENT MEMORY LIMIT

</b></dt>
<dd>

Specifies an overall total memory limit, in GB, for all statements belonging to a specific workload class.



</dd><dt><b>

TOTAL STATEMENT THREAD LIMIT

</b></dt>
<dd>

Specifies an overall limit for the number of active threads scheduled for statements for the specific workload class.



</dd><dt><b>

ADMISSION CONTROL REJECT CPU THRESHOLD / ADMISSION CONTROL REJECT MEMORY THRESHOLD

</b></dt>
<dd>

Specifies the threshold value as a percentage to reject a request based on CPU or memory consumption, if the measured load is equal to or larger than the configured value from the workload class. The threshold range is 0 - 100, where 0 rejects all requests and 100 accepts all requests. This property only applies to new incoming requests \(statements already running are not affected\).

A request rejection returns the message ***'rejected by workload class configuration'***.

Precedence is workload class, then session-wise admission control.



</dd><dt><b>

ADMISSION CONTROL QUEUE CPU THRESHOLD / ADMISSION CONTROL QUEUE MEMORY THRESHOLD

</b></dt>
<dd>

Specifies the threshold range as a value based on CPU or memory consumption. The threshold range is 0 - 100, where value 0 represents always queuing and value 100 represents no queuing. If the measured load is equal to or larger than configured queueing threshold from workload class, an arrived request is enqueued. If the waiting time in the queue of a certain request greater than the queue\_timeout value, the issued request is rejected.

A request rejection returns the message ***'queue wait timeout exceeded'***.

This property only handles new incoming requests \(already running statements are not affected\) as with session-wise admission control.

Precedence is REJECTION comparison, then QUEUEING comparison. Workload class takes precedence over admission control.



</dd><dt><b>

%

</b></dt>
<dd>

Specifies the value as a percentage within the range 0-100. Place the percent sign \(%\) immediately after the value. % is supported only for memory and thread limit property values.



</dd>
</dl>



</dd><dt><b>

ENABLE or DISABLE

</b></dt>
<dd>

Enables or disables the workload class.



</dd>
</dl>



<a name="loiodc417c30b1b3460c8860f6c7ea2a7faa__create_workload_class_description_section"/>

## Description

A workload class with only NULL values behaves like the default workload class.

An aggregated workload class must have all properties specified \(TOTAL STATEMENT MEMORY LIMIT, TOTAL STATEMENT THREAD LIMIT, and PRIORITY\).

**Precedence in the case of competing settings**: In the case of competing settings between workload class settings and user parameter settings \(set by using ALTER USER\), a workload class setting takes precedence over a user parameter setting. Workload class settings and user parameter settings always take precedence over `.ini` file settings. If the STATEMENT TIMEOUT setting, which can also be set by the client, is set to something more restrictive by the client than the value that is determined after evaluating the setting on the server side, then the more restrictive client-side setting is used instead. The following table demonstrates how precedence is determined:


<table>
<tr>
<th valign="top">

global.ini

</th>
<th valign="top">

User parameters

</th>
<th valign="top">

Workload class

</th>
<th valign="top">

Resulting effective values \(statement execution\)

</th>
</tr>
<tr>
<td valign="top">

memory 50 GB

</td>
<td valign="top">

priority 5, thread 5

</td>
<td valign="top">

if not matched class found

</td>
<td valign="top">

priority 5, thread limit 5, memory limit 50GB

</td>
</tr>
<tr>
<td valign="top">

memory 50 GB

</td>
<td valign="top">

priority 5, thread 5, memory 5

</td>
<td valign="top">

priority 7, thread limit 10, memory limit 30GB

</td>
<td valign="top">

priority 7, thread limit 10, memory limit 30GB

</td>
</tr>
<tr>
<td valign="top">

memory 50 GB

</td>
<td valign="top">

priority 5, thread 5, memory 30GB

</td>
<td valign="top">

priority 7, thread limit 10, memory limit undefined

</td>
<td valign="top">

priority 7, thread limit 10, memory limit 30GB

</td>
</tr>
<tr>
<td valign="top">

memory 50 GB

</td>
<td valign="top">

priority 5, thread 5, memory 30GB

</td>
<td valign="top">

priority 7, total thread limit 10, total memory limit 30GB

</td>
<td valign="top">

priority 7, total thread limit 10, total memory limit 30GB

</td>
</tr>
<tr>
<td valign="top">

memory 50 GB

</td>
<td valign="top">

priority 5, thread 5, memory 30GB

</td>
<td valign="top">

priority 7, total thread limit undefined, total memory limit 50GB \(SQL error returned at CREATE/ALTER WORKLOAD CLASS\)

</td>
<td valign="top">

priority 5, thread limit 5, memory limit 30GB

</td>
</tr>
<tr>
<td valign="top">

memory 50 GB

</td>
<td valign="top">

priority 5, thread 5, memory 30GB

</td>
<td valign="top">

priority 7, total thread limit 10, total memory limit undefined \(SQL error returned at CREATE/ALTER WORKLOAD CLASS\)

</td>
<td valign="top">

priority 5, thread limit 5, memory limit 30GB

</td>
</tr>
<tr>
<td valign="top">

statement timeout 2 seconds

</td>
<td valign="top">

N/A

</td>
<td valign="top">

statement timeout 5 seconds

</td>
<td valign="top">

statement time out is 5 unless the value was set more restrictively by the client. For example, if the client-side setting is 3, then 3 becomes the effective value.

</td>
</tr>
</table>



<a name="loiodc417c30b1b3460c8860f6c7ea2a7faa__section_stf_q2d_pbb"/>

## Permissions

You must have the WORKLOAD ADMIN system privilege to execute this statement.



## Examples

The following example defines a new workload class called MyWorkloadClass with all three properties defined.

```
CREATE WORKLOAD CLASS "MyWorkloadClass"
   SET 'PRIORITY' = '3', 'STATEMENT MEMORY LIMIT' = '2', 'STATEMENT THREAD LIMIT' = '20';
```

The following example defines new workload classes and mappings and demonstrates how to enable and disable them.

```
CREATE WORKLOAD MAPPING "MyMapping1" WORKLOAD CLASS "MyClass" SET 'CLIENT'='001';

CREATE WORKLOAD MAPPING "MyMapping2"
   WORKLOAD CLASS "MyClass" SET 'CLIENT'='002';

ALTER WORKLOAD CLASS "MyClass" DISABLE; -- disables "MyClass" and its mappings, "MyMapping1" and "MyMapping2"

ALTER WORKLOAD CLASS "MyClass" ENABLE; -- enables "MyClass" and its mappings, "MyMapping1" and "MyMapping2"

CREATE WORKLOAD CLASS "MyClass1"
   SET 'PRIORITY' = '0',
   'STATEMENT MEMORY LIMIT' = '3',
   'STATEMENT THREAD LIMIT' = '10';

CREATE WORKLOAD MAPPING "MyMapping3"
   WORKLOAD CLASS "MyClass1" SET 'CLIENT'='003';

ALTER WORKLOAD CLASS ALL DISABLE; -- disables all workload classes, "MyClass" and "MyClass1", and their mappings ("MyMapping1", "MyMapping2" and "MyMapping3")

ALTER WORKLOAD CLASS ALL ENABLE; -- enables all workload classes and related mappings again
```

The following example creates a class called class1, and sets the overall memory threshold to 30 GB and the overall thread limit to 50 for every statement that belongs to class1.

```
CREATE WORKLOAD CLASS class1 SET 'TOTAL STATEMENT MEMORY LIMIT'='30', 'TOTAL STATEMENT THREAD LIMIT'='50', 'PRIORITY' = '5';
```

This example creates a workload class called class1 with a write transaction lifetime of 10 minutes and an idle cursor lifetime of 11 minutes.

```
CREATE WORKLOAD CLASS class1 SET 'WRITE TRANSACTION LIFETIME' = '10', 'IDLE CURSOR LIFETIME' = '11';
```

This example creates a workload class called class1, with a statement memory limit expressed as a percentage \(20%\) and a thread limit expressed as a value \(30\).

```
CREATE WORKLOAD CLASS class1 SET 'STATEMENT MEMORY LIMIT'='20%','STATEMENT THREAD LIMIT'='30';
```

This example creates a workload class called class2 which rejects all requests \(threshold = 0\).

```
CREATE WORKLOAD CLASS class2 SET 'ADMISSION CONTROL REJECT CPU THRESHOLD' = '0', 'ADMISSION CONTROL REJECT MEMORY THRESHOLD' = '0';
```

This example creates a workload class called class3 which accepts all requests; no rejections \(threshold =100\).

```
CREATE WORKLOAD CLASS class3 SET 'ADMISSION CONTROL REJECT CPU THRESHOLD' = '100', 'ADMISSION CONTROL REJECT MEMORY THRESHOLD' = '100';
```

This example creates a workload class called class4 with a CPU threshold of 70 and a memory threshold of 80.

```
CREATE WORKLOAD CLASS class4 SET 'ADMISSION CONTROL REJECT CPU THRESHOLD' = '70', 'ADMISSION CONTROL REJECT MEMORY THRESHOLD' = '80';
```

This example creates two workload classes, PARENT\_CLS and CHILD\_CLS. CHILD\_CLS inherits the total statement memory limit from PARENT\_CLS.

```
CREATE WORKLOAD CLASS "PARENT_CLS" SET 'TOTAL STATEMENT MEMORY LIMIT' = '40';
CREATE WORKLOAD CLASS "CHILD_CLS" PARENT "PARENT_CLS" SET 'STATEMENT MEMORY LIMIT' = '10'; 

```

**Related Information**  


[ALTER WORKLOAD CLASS Statement \(Workload Management\)](alter-workload-class-statement-workload-management-d4b4659.md "Changes workload classes.")

[WORKLOAD\_CLASSES System View](../../020-System-Views-Reference/021-System-Views/workload-classes-system-view-d520e47.md "Provides information about available workload classes.")

