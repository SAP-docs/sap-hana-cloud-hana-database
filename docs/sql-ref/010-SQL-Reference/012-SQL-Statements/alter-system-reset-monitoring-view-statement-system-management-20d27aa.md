<!-- loio20d27aa375191014a9cd8ea8c334741a -->

# ALTER SYSTEM RESET MONITORING VIEW Statement \(System Management\)

Resets statistics data for the specified monitoring view.



<a name="loio20d27aa375191014a9cd8ea8c334741a__sql_alter_system_reset_monitor_view_1sql_alter_system_reset_monitor_view_syntax"/>

## Syntax

```
ALTER SYSTEM RESET MONITORING VIEW <view_name>
```



<a name="loio20d27aa375191014a9cd8ea8c334741a__sql_alter_system_reset_monitor_view_1sql_alter_system_reset_monitor_view_syntax_element"/>

## Syntax Elements


<dl>
<dt><b>

*<view\_name\>*

</b></dt>
<dd>

Specifies the name of the resettable monitoring view to be reset.

```
<view_name> ::= [<schema_name>.]<identifier> 
 
<schema_name> ::= <unicode_name>
```

Not all monitoring views can be reset using this command. The names of views that can be reset have the suffix \_RESET.



</dd>
</dl>



<a name="loio20d27aa375191014a9cd8ea8c334741a__sql_alter_system_reset_monitor_view_1sql_alter_system_reset_monitor_view_description"/>

## Description

Use this command to define a starting point for your measurements. First, you reset the monitoring view, and then you execute an action. After the action is completed, query the \_RESET version of the monitor view to get the statistical information gathered since the last reset.



<a name="loio20d27aa375191014a9cd8ea8c334741a__section_ex5_lqr_xrb"/>

## Permissions

To reset statistics data, you must have the RESOURCE ADMIN system privilege.



<a name="loio20d27aa375191014a9cd8ea8c334741a__sql_alter_system_reset_monitor_view_1sql_alter_system_reset_system_monitor_example"/>

## Example

Reset the "SYS"."M\_HEAP\_MEMORY\_RESET" monitoring view.

```
ALTER SYSTEM RESET MONITORING VIEW "SYS"."M_HEAP_MEMORY_RESET";
```

