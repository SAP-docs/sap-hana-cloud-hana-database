<!-- loio20d30dab75191014bf7de6f8ea2b3ed6 -->

# ALTER SYSTEM STOP SERVICE Statement \(System Management\)

Stops single or multiple services on the designated host.



<a name="loio20d30dab75191014bf7de6f8ea2b3ed6__sql_alter_system_stop_service_1sql_alter_system_stop_service_syntax"/>

## Syntax

```
ALTER SYSTEM STOP SERVICE <host_port> [IMMEDIATE [WITH COREFILE]]
```



<a name="loio20d30dab75191014bf7de6f8ea2b3ed6__sql_alter_system_stop_service_1sql_alter_system_stop_service_syntax_element"/>

## Syntax Element


<dl>
<dt><b>

*<host\_port\>*

</b></dt>
<dd>

Specifies the host and port of the service to be stopped.

```
<host_port> ::= 
 <hostname>:<port_number> | ('<host_name>',<port_number>)
```



</dd><dt><b>

IMMEDIATE

</b></dt>
<dd>

Immediately stops the service without waiting for regular shutdown.



</dd><dt><b>

WITH COREFILE

</b></dt>
<dd>

Writes a core dump file.



</dd>
</dl>



<a name="loio20d30dab75191014bf7de6f8ea2b3ed6__sql_alter_system_stop_service_1sql_alter_system_stop_service_description"/>

## Description

Typically a service you stop is automatically restarted by the SAP HANA database system.

You should use this command after changing a configuration parameter, which requires a restart of the service.



<a name="loio20d30dab75191014bf7de6f8ea2b3ed6__section_qy5_3rr_xrb"/>

## Permissions

To stop a service, you must have the SERVICE ADMIN system privilege.



<a name="loio20d30dab75191014bf7de6f8ea2b3ed6__sql_alter_system_stop_service_1sql_alter_system_stop_service_example"/>

## Example

Stop a service running on host hdb1.yourcompany.com on port 30303.

```
ALTER SYSTEM STOP SERVICE 'hdb1.yourcompany.com:30303';
```

