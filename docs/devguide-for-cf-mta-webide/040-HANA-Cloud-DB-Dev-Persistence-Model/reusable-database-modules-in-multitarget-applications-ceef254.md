<!-- loioceef254dec8d48489f49a7095ebb999d -->

# Reusable Database Modules in Multitarget Applications

Setup reusable components inside an application's own data persistence model.

To enable an application to use parts of the database persistence of a reusable component inside its own persistence model, the HDI Deployer allows you to automate the linking \(include\) of design-time files of reusable components in a consuming application. This automated mechanism is based on the Node.js package management mechanism for defining, publishing, and consuming reusable database modules, which also supports versioning based on the semantic versioning concepts.

A reusable database module is considered to have the same `src/` and `cfg/` folder structure as a normal database module. The `src/.hdiconfig` file is mandatory and used by the module mechanism as an indicator that the `src/` and `cfg/` folders belong to a consumable, reusable database module. In addition, the reusable database module needs to have a `package.json` file which defines the module's name, the module's version, and so on.

The following example illustrates the structure of a complete reusable database module:

```
/
+-- src/
|   +-- .hdiconfig
|   +-- <source files ...>
+-- cfg/
|   +-- <optional configuration files ...>
+-- package.json
```

The `package.json` file contains the module’s name, description, version, repository URL, and the set of files which belong to the module, as illustrated in the following example:

> ### Code Syntax:  
> `package.json`
> 
> ```
> { 
>   "name": "module1",
>   "description": "A set of reusable database objects",
>   "version": "1.3.1",
>   "repository": {
>     "url": "git@github.com:modules/module1.git"
>    },
>   "files": [ 
>     "src", 
>     "cfg", 
>     "package.json"
>    ]
> }
> ```

Consumption of a reusable database module is done by adding a dependency in the consuming module's `package.json` file, for example, alongside the dependency to the HDI Deployer “`@sap/hdi-deploy`” as illustrated below, where the consuming module requires “`module1`” in version “`1.3.1`” and “`module2`” in version “`1.7.0`”:

> ### Code Syntax:  
> ```
> {
>  "name": "deploy",
>  "dependencies": {
>    "@sap/hdi-deploy": "3.7.0", 
>    "module1": "1.3.1", 
>    "module2": "1.7.0"
>  },
>  "scripts": {
>    "start": "node node_modules/@sap/hdi-deploy/"
>  }
> } 
> ```

When running `npm install` to download and install the dependencies which are listed in the dependencies section of the `package.json` file, `npm` will also download the reusable database modules and places them into the `node_modules/` folder of the consuming module. For each module a separate subfolder is created with the name of the module.

When the HDI Deployer is triggered to do the actual deployment of the \(consuming\) database module, it scans the `node_modules/` folder and virtually integrates the `src/` and `cfg/` folders of reusable database modules it finds into the \(consuming\) database module’s `lib/` folder. Reusable database modules are identified by the mandatory `src/.hdiconfig` file. On successful deployment, the HDI container will contain the consumed modules below the root-level `lib/` folder, as shown in the following example:

```
/
+-- src/
+-- cfg/
+-- lib/
|   +-- module1/
|   |   +-- src/
|   |   +-- cfg/
|   +-- module2/
|       +-- src/
|       +-- cfg/
```

> ### Note:  
> It is not permitted to recursively include reusable database modules.

**Related Information**  


[Configuring the HDI Deployer](configuring-the-hdi-deployer-d5bf65e.md "Set up and use the Node.js-based HDI Deployer in Cloud Foundry.")

[Integrate the HDI Deployer into a Mutlitarget Application's Database Module](integrate-the-hdi-deployer-into-a-mutlitarget-application-s-database-modu-0194390.md "Install the HDI Deployer for use by a Multi-Target Application (MTA).")

