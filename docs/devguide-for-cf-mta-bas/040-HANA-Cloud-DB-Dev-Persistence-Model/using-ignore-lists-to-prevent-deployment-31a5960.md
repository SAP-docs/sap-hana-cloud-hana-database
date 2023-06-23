<!-- loio31a5960f7c4e457ea5ed7d4b2b8f172c -->

# Using Ignore Lists to Prevent Deployment

Specify a list of artifacts that should be ignored during deployment.

The HDI deployer allows you to define a list of artifacts that should be ignored for the purposes of deployment; the artifacts are specified in a file that must have the name `.hdiignore` and are not considered for any deployment operation in HDI.

> ### Note:  
> The `.hdiignore` file must be placed at the root of the application project folder, just like the `undeploy.json` file.

The format of the `.hdiignore` file is similar to the structure of a `.gitignore` file; namely, lines of text specifying the relative path to any artifact you want to exclude from an HDI deployment operation. The syntax required in the `.hdiignore` file enables you to use either real paths or path patterns, as illustrated in the following example:

> ### Code Syntax:  
> The `.hdiignore` File
> 
> ```
> src/table_1.hdbtable
> src/*_2.hdbtable
> ```

The `.hdiignore` file works in the same way as the HDI deployer's *\--exclude-filter* option, and it is possible to use both features at the same time. For more information about the exclude filter as well as details of other deployment options, see *Deployment Options in HDI* in *Related Information* below.

**Related Information**  


[Deployment Options in HDI](deployment-options-in-hdi-a4bbc2d.md "A list of options for configuring custom deployment scenarios with SAP HDI.")

