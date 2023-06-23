<!-- loio1d9582a464344b6c86bcd3489dca7554 -->

# SAP HDI Configuration Parameters

Configuration parameters are used to configure the behavior of SAP HANA Deployment Infrastructure \(HDI\).



SAP HDI configuration parameters enable you to configure the general behavior of SAP HDI. For example, HDI administrators can use the parameters to specify the time an SAP HDI operation waits for a locking conflict to clear; HDI container and container-group administrators can use the configuration parameters to specify the default behavior and allowed usage of containers and container groups.

In this topic, you can find information about the following types of HDI configuration parameters:

-   [Standard SAP HDI Configuration Parameters](sap-hdi-configuration-parameters-1d9582a.md#loio1d9582a464344b6c86bcd3489dca7554__section_cd2_5ys_15b)
-   [Container-Specific Configuration Parameters](sap-hdi-configuration-parameters-1d9582a.md#loio1d9582a464344b6c86bcd3489dca7554__section_op2_fys_15b)
-   [Container-Group-Specific Configuration Parameters](sap-hdi-configuration-parameters-1d9582a.md#loio1d9582a464344b6c86bcd3489dca7554__section_ob5_w4g_ptb)



<a name="loio1d9582a464344b6c86bcd3489dca7554__section_cd2_5ys_15b"/>

## Standard SAP HDI Configuration Parameters

SAP HDI configuration parameters are used to configure the general behavior of SAP HDI. For example, HDI administrators can specify the time an SAP HDI operation waits for a locking conflict to clear.

The following table describes the regular configuration parameters for SAP HDI and lists the possible values.

**SAP HDI Configuration Parameters**


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Possible Values



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `api.permit_self_granting` 



</td>
<td valign="top">

true, false



</td>
<td valign="top">

Specifies whether granting of privileges to the user calling a grant procedure is allowed.

The default is “true”.



</td>
</tr>
<tr>
<td valign="top">

 `api.severity_for_invalid_parameter` 



</td>
<td valign="top">

ERROR, WARNING, INFO



</td>
<td valign="top">

Specifies the severity of the corresponding log message when an invalid parameter has been passed with the SAP HANA DI operation.

The default value is ERROR.



</td>
</tr>
<tr>
<td valign="top">

 `connection.container_default_transaction_lock_wait_timeout` 



</td>
<td valign="top">

0 … 2,147,483,647



</td>
<td valign="top">

Specifies the default time \(in milliseconds\) a container operation waits for a locking conflict to clear.

The default value is 900000.



</td>
</tr>
<tr>
<td valign="top">

 `connection.global_transaction_lock_wait_timeout` 



</td>
<td valign="top">

0 … 2,147,483,647



</td>
<td valign="top">

Specifies the time \(in milliseconds\) an SAP HANA DI operation waits for a locking conflict to clear.

The default value is 900000.



</td>
</tr>
<tr>
<td valign="top">

 `make.default_max_parallel_jobs` 



</td>
<td valign="top">

0 … 2,147,483,647



</td>
<td valign="top">

Specifies the default maximum number of parallel jobs to be spawned during a make. The value "0" means that the best value is chosen automatically.

The default value is 0.



</td>
</tr>
<tr>
<td valign="top">

 `messages.container_default_days_to_keep` 



</td>
<td valign="top">

\-2,147,483,648 … 2,147,483,647



</td>
<td valign="top">

Specifies the default number of days to keep container-specific log messages. A value of 0 means all entries are deleted. A negative value means all entries are kept.

The default value is 90



</td>
</tr>
<tr>
<td valign="top">

 `messages.container_default_requests_to_keep` 



</td>
<td valign="top">

\-2,147,483,648 … 2,147,483,647



</td>
<td valign="top">

Specifies the default number of requests to keep container-specific log messages. A value of 0 means all entries are deleted. A negative value means all entries are kept.

The default value is 100000



</td>
</tr>
<tr>
<td valign="top">

 `messages.global_days_to_keep` 



</td>
<td valign="top">

\-2,147,483,648 … 2,147,483,647



</td>
<td valign="top">

Specifies the number of days to keep global SAP HANA DI log messages. A value of 0 means all entries are deleted. A negative value means all entries are kept.

The default value is 90.



</td>
</tr>
<tr>
<td valign="top">

 `messages.global_requests_to_keep` 



</td>
<td valign="top">

\-2,147,483,648 … 2,147,483,647



</td>
<td valign="top">

Specifies the number of requests to keep global SAP HANA DI log messages. A value of 0 means all entries are deleted. A negative value means all entries are kept.

The default value is 100000.



</td>
</tr>
</table>



### Example: Configuring SAP HANA DI with an SAP HANA DI Configuration Parameter

> ### Sample Code:  
> ```sql
> -- prepare configuration parameters table
> create table MY_CONFIG_PARAMETERS like _SYS_DI.TT_PARAMETERS;
> insert into MY_CONFIG_PARAMETERS(KEY, VALUE) values ('make.default_max_parallel_jobs', '10');
> 
> 
> -- prepare parameters table
> create table MY_PARAMETERS like _SYS_DI.TT_PARAMETERS;
> 
> 
> -- call procedure
> call _SYS_DI.CONFIGURE_DI_PARAMETERS(MY_CONFIG_PARAMETERS, MY_PARAMETERS, ?, ?, ?);
> 
> ```



<a name="loio1d9582a464344b6c86bcd3489dca7554__section_op2_fys_15b"/>

## Container-Specific Configuration Parameters

Container-specific configuration parameters are used to control the behavior of a single container. For example, they specify the time a container operation waits for a locking conflict to clear or the maximum number of parallel jobs to be spawned during a make operation.

The following table describes the container-specific configuration parameters and lists the possible values.

**SAP HANA DI Container-specific Configuration Parameters**


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Possible Values



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `api.enable_flowgraph_access` 



</td>
<td valign="top">

 “true” or “false” 



</td>
<td valign="top">

Indicates if access to flow graphs is allowed.

The default value is “false”.



</td>
</tr>
<tr>
<td valign="top">

 `blobs.days_to_keep` 



</td>
<td valign="top">

\-2,147,483,648 … 2,147,483,647



</td>
<td valign="top">

Specifies the number of days to keep data entries in the blob store. A value of 0 means all entries are deleted. A negative value means all entries are kept.

The default value is 10 days.



</td>
</tr>
<tr>
<td valign="top">

 `connection.transaction_lock_wait_timeout` 



</td>
<td valign="top">

0 … 2,147,483,647



</td>
<td valign="top">

Specifies the time \(in milliseconds\) a container operation waits for a locking conflict to clear. The default value is the value of the corresponding SAP HANA DI configuration parameter `connection.container_default_transaction_lock_wait_timeout`.



</td>
</tr>
<tr>
<td valign="top">

 `global.usage` 



</td>
<td valign="top">

production, test, development, custom



</td>
<td valign="top">

Indicates the intended usage of the container for which the make operation is run. Depending on the usage, different restrictions might apply. If this configuration parameter is not set, then the value is taken from the `system information` section in `global.ini` configuration file.



</td>
</tr>
<tr>
<td valign="top">

 `make.force_logical_schema_targets` 



</td>
<td valign="top">

 “true” or “false” 



</td>
<td valign="top">

Indicates if the usage of logical schemas in design-time artifacts should be forced. The default value is “false”.



</td>
</tr>
<tr>
<td valign="top">

 `make.max_parallel_jobs` 



</td>
<td valign="top">

0 … 2,147,483,647



</td>
<td valign="top">

Specifies the maximum number of parallel jobs to be spawned during a make.

The default value is the value of the corresponding SAP HANA DI configuration parameter `make.default_max_parallel_jobs`.



</td>
</tr>
<tr>
<td valign="top">

 `make.prohibit_config_file` 



</td>
<td valign="top">

 “true” or “false” 



</td>
<td valign="top">

Indicates if the deployment of configuration files \(`.hdiconfig`\) should be disabled.

The default value is “false”.



</td>
</tr>
<tr>
<td valign="top">

 `make.prohibit_definer_mode` 



</td>
<td valign="top">

 “true” or “false” 



</td>
<td valign="top">

Indicates if the creation of “definer-mode” procedures is disabled. The default value is “false”.



</td>
</tr>
<tr>
<td valign="top">

 `make.prohibit_namespace_file` 



</td>
<td valign="top">

 “true” or “false” 



</td>
<td valign="top">

Indicates if the deployment of namespace files \(`.hdinamespace`\) should be disabled.

The default value is “false”.



</td>
</tr>
<tr>
<td valign="top">

 `make.prohibit_table_creation` 



</td>
<td valign="top">

 “true” or “false” 



</td>
<td valign="top">

Indicates if the creation of tables is disabled. The default value is “false”.



</td>
</tr>
<tr>
<td valign="top">

 `make.validate_external_dependencies` 



</td>
<td valign="top">

 “true” or “false” 



</td>
<td valign="top">

Indicates that during a make, all deployed synonyms, projection views, and virtual tables should be checked for changes to referenced objects and redeployed, if a change is detected.

The default value is “false”.



</td>
</tr>
<tr>
<td valign="top">

 `messages.days_to_keep` 



</td>
<td valign="top">

\-2,147,483,648 … 2,147,483,647



</td>
<td valign="top">

Specifies the number of days to keep log messages. A value of 0 means all entries are deleted. A negative value means all entries are kept.

The default value is 90 days.



</td>
</tr>
<tr>
<td valign="top">

 `messages.requests_to_keep` 



</td>
<td valign="top">

\-2,147,483,648 … 2,147,483,647



</td>
<td valign="top">

Specifies the number of requests to keep log messages. A value of 0 means all entries are deleted. A negative value means all entries are kept.

The default value is 100000 requests.



</td>
</tr>
<tr>
<td valign="top">

 `build.plugin.name/disabled` 



</td>
<td valign="top">

 “true” or “false” 



</td>
<td valign="top">

Indicates if the build plug-in specified by the parameter is disabled. By default, there is no such parameter set; no build plug-in is disabled by default.



</td>
</tr>
</table>



### Example: Configuring a Container with a Container-specific Configuration Parameter

> ### Sample Code:  
> ```sql
> -- prepare configuration parameters table
> create table MY_CONFIG_PARAMETERS like _SYS_DI.TT_PARAMETERS;
> insert into MY_CONFIG_PARAMETERS(KEY, VALUE) values ('make.max_parallel_jobs', '10');
> 
> 
> -- prepare parameters table
> create table MY_PARAMETERS like _SYS_DI.TT_PARAMETERS;
> 
> 
> -- call procedure
> call MY_CONTAINER#DI.CONFIGURE_CONTAINER_PARAMETERS(MY_CONFIG_PARAMETERS, MY_PARAMETERS, ?, ?, ?);
> 
> ```



<a name="loio1d9582a464344b6c86bcd3489dca7554__section_ob5_w4g_ptb"/>

## Container-Group-Specific Configuration Parameters

Container-group configuration parameters are used to control the behavior of a specific container group and the containers in the group. For example, the HDI container-group administrator can specify whether containers in a container group can access database objects in other containers in the same container group.

The following table describes the parameters that can be used to configure container groups and lists the possible values.

**SAP HANA DI Container-group-specific Configuration Parameters**


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Possible Values



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `enable_cross_container_access` 



</td>
<td valign="top">

 “true” or “false” 



</td>
<td valign="top">

Enables or disables access in terms of DML privileges between containers in the same container group.

 



</td>
</tr>
</table>

The following example shows how to use the HDI container-group administration API \(`_SYS_DI#G`\) to enable the configuration parameter cross-container access for containers in container group 'G':

> ### Sample Code:  
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #CONFIG_GROUP_PARAMETERS LIKE _SYS_DI.TT_PARAMETERS;
> INSERT INTO #CONFIG_GROUP_PARAMETERS (KEY, VALUE) VALUES ('enable_cross_container_access', 'true');
> CALL _SYS_DI#G.CONFIGURE_CONTAINER_GROUP_PARAMETERS(#CONFIG_GROUP_PARAMETERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
> DROP TABLE #CONFIG_GROUP_PARAMETERS; 
> ```

**Related Information**  


[SAP HDI Parameters](sap-hdi-parameters-e2d3e54.md "An overview of the parameters available for the SAP HANA Deployment Infrastructure (HDI) and the corresponding build plug-ins.")

[Configure SAP HDI Parameters](configure-sap-hdi-parameters-7c989fa.md "The SAP HANA Deployment Infrastructure (HDI) administrator can configure some general aspects of the HDI with parameters, for example, how long an HDI operation waits for a locking conflict to clear or the default behavior of HDI containers.")

