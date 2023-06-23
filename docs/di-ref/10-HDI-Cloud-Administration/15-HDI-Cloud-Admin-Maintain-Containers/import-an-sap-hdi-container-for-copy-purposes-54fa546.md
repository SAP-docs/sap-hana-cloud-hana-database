<!-- loio54fa5466cdeb4e488b08d6c7da0244f2 -->

# Import an SAP HDI Container for Copy Purposes

An HDI container administrator can import an HDI container into the same \(or another\) database from a table.



<a name="loio54fa5466cdeb4e488b08d6c7da0244f2__prereq_ux4_zbq_sqb"/>

## Prerequisites

-   If the imported HDI container has any dependencies to other HDI containers or normal database schemas, then the other containers and schemas must also be made available in the target database first.
-   If the imported HDI container has been granted privileges to other containers or schemas, the granted privileges must also be assigned in the database before you import the dependent HDI container.

> ### Note:  
> While the export or import operation in running, it is not possible to run any other HDI API on the affected HDI container.



<a name="loio54fa5466cdeb4e488b08d6c7da0244f2__context_tr2_vq5_qcb"/>

## Context

An HDI container and its dependencies can be exported to a table and then imported to a new container. The import of a source container, for example, `C1` into a new container `C2` is performed by calling the built-in procedure `C2#DI.IMPORT_CONTAINER_FOR_COPY`. This procedure expects as input the schema and the names of two tables: the table containing the exported results and a table containing any necessary parameters.

The import procedure removes the contents of the target container, writes the data from the export table to the target container, and runs a `MAKE`. Any existing objects and data in the target container will be deleted before the import procedure starts. After the import procedure has completed successfully, the target container will be a copy of the source container including all the data of the original run-time schema.

> ### Note:  
> Only objects deployed by the source container’s `MAKE` procedure are copied. Objects created manually in the source container’s run-time schema are not copied.

To import a container `C1` into a new container `C2` for copy purposes, perform the following steps:

> ### Note:  
> The container version of the target container must be the same as the container version of the source container. Containers with version greater than or equal to \(\>=\) 40 can also be imported into containers with a higher container version. You can check the container version with the view `_SYS_DI#G.M_CONTAINER_VERSIONS`.



<a name="loio54fa5466cdeb4e488b08d6c7da0244f2__steps_ur2_vq5_qcb"/>

## Procedure

1.  Open an SQL console and connect to the SAP HANA database with the permissions of the administrator of the HDI container “C1”.

2.  Open the SQL editor for this database.

3.  Ensure the target container exists, for example, `C2`.

    The target container \(“C2” in this example\) must already exist before the import operation starts.

    ```sql
    CALL _SYS_DI#G.CREATE_CONTAINER('C2’, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    ```

    > ### Note:  
    > An HDI container must be created by an HDI **container-group** administrator. The new container does not have to be empty for the purpose of an import. However, any existing objects and data in the target container will be deleted before the import.

4.  If necessary, grant the object owner of the target container `C2#OO` any privileges for all the external objects required by the container \(“C1”\) to be imported.

    > ### Note:  
    > All external objects referenced by the container’s design-time objects must be available and accessible to the object owner of the target container.

5.  Set up any required dependencies and privileges.

    All external objects referenced by design-time objects in the imported container \(as well as the remote container\(s\) in which the external objects are located\) must already be available in the target database and accessible to the object owner of the imported container when you start the import operation. So, if necessary, grant the object owner of the target container `C2#OO` any privileges required for access to the external objects in any remote containers \(for example, in container "C3"\).

    > ### Note:  
    > If remote container "C3" exposes a role for enabling cross-container access, this role must be granted to the dependent container "C2"’s user `C2#OO`. The role can be granted to user `C2#OO` either by a role administrator \(`ROLE ADMIN`\) or by using the HDI Container API for role assignment.
    > 
    > If container "C3" does not expose a role, the required privileges must be granted to the dependent container "C2"s user `C2#OO` by other means, for example, using the HDI Container API for granting schema privileges.

6.  Paste the following SQL code into the SQL editor.

    If the HDI container you want to import \(C2\) has dependencies to objects in another container \(for example, container C3\), then you need to import the other container \(C3\) first and set up any required privileges, as described above.

    ```sql
    CALL C2#DI.IMPORT_CONTAINER_FOR_COPY
      (<MyImportSchema>, 'EXPORT_TABLE', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    ```

7.  Execute the SQL code, and check that the operation completed successfully \(HDI return code 0\).

8.  Confirm that the container has been successfully imported.

    In this example, you can check that the expected run-time objects of source container `C1` are also present in the target container `C2`.


**Related Information**  


[Maintaining SAP HDI Container Groups](../14-HDI-Cloud-Admin-Maintain-Container-Groups/maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Export an SAP HDI Container for Copy Purposes](export-an-sap-hdi-container-for-copy-purposes-c25ee28.md "An HDI container administrator can export an HDI container to a table, which can then be used to import the container into a database.")

