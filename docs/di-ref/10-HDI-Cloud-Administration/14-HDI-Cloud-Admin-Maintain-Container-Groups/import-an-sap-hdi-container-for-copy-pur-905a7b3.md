<!-- loio905a7b383a5a472f9d712fa3fb8d14ee -->

# Import an SAP HDI Container for Copy Purposes

An HDI container can be imported into the same \(or another\) database from a table.



<a name="loio905a7b383a5a472f9d712fa3fb8d14ee__prereq_ux4_zbq_sqb"/>

## Prerequisites

-   If the imported HDI container has any dependencies to other HDI containers or normal database schemas, then the other containers and schemas must also be made available in the target database first.
-   If the imported HDI container has been granted privileges to other containers or schemas, the granted privileges must also be assigned in the database before you import the dependent HDI container.

> ### Note:  
> While an export or import operation is running, it is not possible to run any other HDI API on the affected HDI container.



<a name="loio905a7b383a5a472f9d712fa3fb8d14ee__context_tr2_vq5_qcb"/>

## Context

An HDI container and its dependencies can be exported to a table and then imported to a new container. The import of a source container into a new container is performed by calling the built-in procedure <code>_SYS_DI#<i class="varname">&lt;container_group_name&gt;</i>.IMPORT_CONTAINER_FOR_COPY</code>. This procedure expects as input the name of an existing, empty, target container, the schema and table names of the table containing the exported results, and a table containing any necessary parameters.

The import procedure removes the contents of the target container, writes the data from the export table to the target container, and runs a `MAKE`. Any existing objects and data in the target container will be deleted before the import procedure starts. After the import procedure has completed successfully, the target container will be a copy of the source container including all the data of the original run-time schema.

> ### Note:  
> Only objects deployed by the source container’s `MAKE` procedure are copied. Objects created manually in the source container’s run-time schema are not copied.

To import the container *<source\_container\_name\>* into a new container *<target\_container\_name\>* for copy purposes, perform the following steps:

> ### Note:  
> The container version of the target container must be the same as the container version of the source container. Containers with a version greater than or equal to \(\>=\) 40 can also be imported into containers with a higher container version. You can check the container version with the view <code>_SYS_DI#<i class="varname">&lt;container_group_name&gt;</i>.M_CONTAINER_VERSIONS</code>.



<a name="loio905a7b383a5a472f9d712fa3fb8d14ee__steps_ur2_vq5_qcb"/>

## Procedure

1.  Open an SQL console and connect to the SAP HANA database with the permissions of the administrator of the HDI container group *<container\_group\_name\>*.

2.  Open the SQL editor for this database.

3.  If needed, create the new target container, for example, *<target\_container\_name\>*.

    ```sql
    CALL _SYS_DI#<container_group_name>.CREATE_CONTAINER('<target_container_name>’, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    ```

    > ### Note:  
    > In the `CALL` command, replace *<container\_group\_name\>* and *<target\_container\_name\>* with the names of your HDI container group and target container respectively. The new container does not have to be empty for the purpose of an import. However, any existing objects and data in the target container will be deleted before the import.

4.  Set up any required dependencies and privileges.

    All external objects referenced by design-time objects in the imported container \(as well as the remote container\(s\) in which the external objects are located\) must already be available in the target database and accessible to the object owner of the imported container when you start the import operation. So, if necessary, grant the object owner of the target container <code><i class="varname">&lt;target_container_name&gt;</i>#OO</code> any privileges required for access to the external objects in any remote containers \(for example, in container *<remote\_container\_name\>*\).

    > ### Note:  
    > If remote container *<remote\_container\_name\>* exposes a role for enabling cross-container access, this role must be granted to the dependent target container's user <code><i class="varname">&lt;target_container_name&gt;</i>#OO</code>. The role can be granted to user <code><i class="varname">&lt;target_container_name&gt;</i>#OO</code> either by a role administrator \(`ROLE ADMIN`\) or by using the HDI Container API for role assignment.
    > 
    > If container *<remote\_container\_name\>* does not expose a role, the required privileges must be granted to the dependent target container's user <code><i class="varname">&lt;target_container_name&gt;</i>#OO</code> by other means, for example, using the HDI Container API for granting schema privileges.

5.  Paste the following SQL code into the SQL editor.

    If the HDI container you want to import \(*<source\_container\_name\>*\) has dependencies to objects in another container \(for example, container *<remote\_container\_name\>*\), then you need to import the other container \(*<remote\_container\_name\>*\) first and set up any required privileges, as described above.

    ```sql
    CALL _SYS_DI#<container_group_name>.IMPORT_CONTAINER_FOR_COPY
      ('<target_container_name>', '<MyImportSchema>', 'EXPORT_TABLE', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    ```

    > ### Note:  
    > In the `CALL` command, replace *<container\_group\_name\>*, *<target\_container\_name\>*, *<MyImportSchema\>* with the names of your HDI container group, target container, and target schema respectively.

6.  Execute the SQL code, and check that the operation completed successfully \(HDI return code 0\).

7.  Confirm that the container has been successfully imported.

    In this example, you can check that the expected run-time objects of *<source\_container\_name\>* are also present in the target container *<target\_container\_name\>*.


**Related Information**  


[Maintaining SAP HDI Container Groups](maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Export an SAP HDI Container for Copy Purposes](export-an-sap-hdi-container-for-copy-pur-36a5547.md "An HDI container can be exported to a table, which can then be used to import the container into a database.")

