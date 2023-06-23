<!-- loio20d23ead751910148f18dcd2a0862e90 -->

# ALTER SYSTEM RECONFIGURE SERVICE Statement \(System Management\)

Reconfigures a specified service by applying the current configuration parameters.



<a name="loio20d23ead751910148f18dcd2a0862e90__sql_alter_system_reconfigure_service_1sql_alter_system_reconfigure_service_syntax"/>

## Syntax

```
ALTER SYSTEM RECONFIGURE SERVICE (<service_name>,<hostname>,<port_number>)
```



<a name="loio20d23ead751910148f18dcd2a0862e90__sql_alter_system_reconfigure_service_1sql_alter_system_reconfigure_service_syntax_element"/>

## Syntax Element


<dl>
<dt><b>

*<service\_name\>*

</b></dt>
<dd>

Specifies the name of the service you wish to reconfigure. See the M\_SERVICE\_TYPES monitoring view topic for a list of available service types.

```
<service_name> ::= <string_literal>
```



</dd><dt><b>

*<hostname\>*

</b></dt>
<dd>

Specifies the hostname and port number where you would like to reconfigure a service.

```
<hostname> ::= <string_literal>

<port_number> ::= <unsigned_integer>
```



</dd>
</dl>



<a name="loio20d23ead751910148f18dcd2a0862e90__sql_alter_system_reconfigure_service_1sql_alter_system_reconfigure_service_description"/>

## Description

You use ALTER SYSTEM RECONFIGURE SERVICE to reconfigure a specified service by applying the current configuration parameters. This command is used after changing multiple configuration parameters with the ALTER CONFIGURATION command without the RECONFIGURE option set. See the ALTER SYSTEM ALTER CONFIGURATION topic.

To reconfigure a specific service specify *<service\_name\>* and leave *<hostname\>* and *<port\_number\>* empty. To reconfigure all services of a type, specify *<hostname\>* and *<port\_number\>* and leave *<service\_name\>* empty. To reconfigure all services, leave all parameters empty.



<a name="loio20d23ead751910148f18dcd2a0862e90__section_lr5_gpr_xrb"/>

## Permissions

To reconfigure a service, you must have the SERVICE ADMIN system privilege.



<a name="loio20d23ead751910148f18dcd2a0862e90__sql_alter_system_reconfigure_service_1sql_alter_system_reconfigure_service_example"/>

## Example

You use the following command to reconfigure all services on the hana.yourcompany.com host using port number 30303:

```
ALTER SYSTEM RECONFIGURE SERVICE ('','hana.yourcompany.com',30303);
```

You use the following command to reconfigure all services of type indexserver:

```
ALTER SYSTEM RECONFIGURE SERVICE ('indexserver','',0);
```

**Related Information**  


[ALTER WORKLOAD CLASS Statement \(Workload Management\)](alter-workload-class-statement-workload-management-d4b4659.md "Changes workload classes.")

[ALTER SYSTEM ALTER CONFIGURATION Statement \(System Management\)](alter-system-alter-configuration-statement-system-management-20d08a5.md "Sets or removes configuration parameters in an INI file.")

