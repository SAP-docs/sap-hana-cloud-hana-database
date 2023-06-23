<!-- loio450e26c04b024330b743a0b4f312e2a6 -->

# SAP HDI Container Administration

Most of the tasks related to the administration of SAP HANA Deployment Infrastructure \(HDI\) containers can be performed by both the HDI administrator and the HDI container administrator.

HDI-container-related administrator tasks are performed by calling the respective HDI container-administration SQL procedures, not of a target container, but of the `_SYS_DI` schema of the HDI administrator with an additional first parameter taking the name of the target container. For details about the tasks required to maintain HDI containers and the functionality available to help perform these tasks, refer to the section about *Maintaining HDI Containers* listed in *Related Information*.

To grant a user “U” the privileges to access the run-time objects in the container “C”, the HDI administrator can call the SQL procedure `GRANT_CONTAINER_SCHEMA_PRIVILEGES` in the `_SYS_DI` schema, passing the container’s name \(in this example, “C”\) as the additional first parameter, as illustrated in the following example:

> ### Caution:  
> The administration of a container should normally be performed by the container’s assigned administrator. The HDI administrator should only be used for this purpose in exceptional circumstances.

> ### Sample Code:  
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_SCHEMA_PRIVILEGES; 
> INSERT INTO #PRIVILEGES ( PRIVILEGE_NAME, PRINCIPAL_SCHEMA_NAME, PRINCIPAL_NAME ) VALUES ( 'SELECT', '', 'U' ); 
> CALL _SYS_DI.GRANT_CONTAINER_SCHEMA_PRIVILEGES( 'C', #PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
> DROP TABLE #PRIVILEGES; 
> ```

**Related Information**  


[Maintaining SAP HDI Containers](10-HDI-Cloud-Administration/15-HDI-Cloud-Admin-Maintain-Containers/maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

