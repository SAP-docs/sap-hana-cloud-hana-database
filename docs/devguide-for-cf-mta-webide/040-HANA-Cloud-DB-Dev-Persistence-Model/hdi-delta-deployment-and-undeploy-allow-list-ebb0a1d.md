<!-- loioebb0a1d1d41e4ab0a06ea951717e7d3d -->

# HDI Delta Deployment and Undeploy Allow List

The HDI Deployer implements a delta-based deployment strategy including an optional allow list.

On start up, the HDI Deployer recursively scans the local `src/` and `cfg/` folders, processes configuration templates, checks the HDI container on the server-side, and calculates the set of added, modified, and deleted files based on the difference between the local file system state and the state of the deployed file system of the server-side HDI container.

In normal operation, when performing a full build of the database module, the HDI Deployer schedules for deployment only the set of added and modified files. The set of unmatched or deleted files is not scheduled for automatic undeployment. For **selective** deployment, however, where you want to deploy selected, individual files, deleted files are neither detected nor undeployed.

If auto-undeployment is disabled, then to undeploy deleted or unmatched files, an application must include an undeploy “allow list”, for example, by creating an `undeploy.json` file in the root directory of the `db/` module \(alongside the `src/` and `cfg/` folders\). The undeploy allow list `undeploy.json` file is a JSON document with a top-level array of file names that can be undeployed, as illustrated in the following example:

> ### Code Syntax:  
> Example `undeploy.json` File
> 
> ```json
> [
>     "src/Table.hdbtable",
>     "src/Procedure.hdbprocedure"
> ]
> ```

The `undeploy.json` file must list all artifacts to be undeployed. In addition, the file path specified for the artifacts to remove must be **relative** to the root directory of the `db/` module and must use the HDI file path forward-slash delimiter \(/\).

For interactive scenarios, it is possible to pass the “*auto-undeploy*” option to the HDI Deployer, as illustrated in the following example:

```
node deploy --auto-undeploy
```

In this case, the HDI Deployer ignores the undeploy allow list defined in the `undeploy.json` file and schedules all deleted files in the `src/` and `cfg/` folders for undeployment.

**Related Information**  


[Integrate the HDI Deployer into a Mutlitarget Application's Database Module](integrate-the-hdi-deployer-into-a-mutlitarget-application-s-database-modu-0194390.md "Install the HDI Deployer for use by a Multi-Target Application (MTA).")

[File Structure of the Multitarget Application Database Module](file-structure-of-the-multitarget-application-database-module-18ac9fd.md "The structure and hierarchy required in the database module of a multitarget application.")

