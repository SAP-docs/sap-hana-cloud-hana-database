<!-- loioad7d3fda72e04fc68bbdd4756d79ed3c -->

# SAP HDI Container-Group Administration

The administration of SAP HANA Deployment Infrastructure \(HDI\) container-groups involves the management of a set of HDI containers in an assigned HDI container group.

Most container-group-related administration tasks can be performed by both the HDI container-group administrator and the HDI administrator; the tasks include creating and dropping containers in the container group or, if necessary, granting container-administration privileges to other users of a container. However, only the HDI administrator can create and drop a container **group**. After creating a container group, the HDI administrator creates a new container-group administrator by assigning the necessary container-group administrator privileges to one or more selected users. The new container-group administrator is responsible for maintaining the containers in the new container group.

Each container group can have its own set of administrators. Administrative privileges for a container group can only be granted by an HDI administrator or a container group administrator who has the necessary privileges. Container-group administrators can only grant privileges for the container groups for which they are directly responsible.

For the HDI administrator, the APIs of a container group are located in the schema `_SYS_DI`; for the HDI container-group administrator, the APIs of a container group called “G” are located in the schema `_SYS_DI#G`. For more information about the functionality available to the HDI container-group administrator, see the section *Maintaining HDI Container Groups* listed in *Related Information*.

> ### Caution:  
> The administration of a container group should normally be performed by the container group’s assigned administrator. The HDI administrator should only be used for container-group administration purposes in exceptional circumstances.



<a name="loioad7d3fda72e04fc68bbdd4756d79ed3c__section_u5p_sn1_m1b"/>

## Exporting and Importing HDI Containers

In special cases, a container and its dependencies can be exported from the database and imported into a different database for support purposes.

> ### Caution:  
> The API procedures `_SYS_DI#G.EXPORT_CONTAINER_FOR_SUPPORT` and `_SYS_DI#G.IMPORT_CONTAINER_FOR_SUPPORT` are available to the HDI container-group administrator but intended for use only by SAP support. The exported data might include private or confidential data from the container, and the container import could also compromise the integrity of the database.
> 
> The same API procedures are also available to the HDI administrator, but in the schema `_SYS_DI`, for example, `_SYS_DI.EXPORT_CONTAINER_FOR_SUPPORT`.

**Related Information**  


[Maintaining SAP HDI Container Groups](10-HDI-Cloud-Administration/14-HDI-Cloud-Admin-Maintain-Container-Groups/maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

