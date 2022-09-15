<!-- loio6188d2234bb04b1f913516bf82e1c6a0 -->

# The HDI Name-Space Configuration File

The SAP HANA Deployment Infrastructure \(HDI\) uses a JSON resource to define naming rules for run-time objects.

In SAP HDI, name-space rules are defined in one or more file resource named `.hdinamespace`, which must be located in the folder to which the naming rules apply - or the root folder of a hierarchy to which the naming rules apply. The content of the `.hdinamespace` file is specified according to the JSON format with the following structure:

> ### Sample Code:  
> `src/.hdinamespace`
> 
> ```
> {
>    "name"      : "com.sap.hana.example",
>    "subfolder" : "<[append | ignore]>"
> }
> 
> ```

Every folder can contain its own name-space file. For a name-space file to take effect, it has to be deployed in the same way as any other design-time file. After deployment, a name-space file provides run-time name-space information for all files in the same folder.

The `.hdinamespace` file provides name-space information for all sub-folders where no additional name-space file is present. For those sub-folders without a name-space configuration file, the name space depends on the value of the `subfolder` key in the name-space-configuration file in the parent folder.

-   `append`

    Add the name of the sub-folder to the run-time name space for the deployed objects

-   `ignore`

    Do **not** add the name of the sub-folder to the run-time name space for the deployed objects


> ### Note:  
> Name spaces and the naming rules are configurable and do not directly relate to the folder structure of the design-time files.

Developers can place a name-space configuration file \(`.hdinamespace`\) in a design-time folder, which specifies how the generated database objects are named in the sub-hierarchy underneath this folder. For example, you can just use the plain design-time object name, or the object name with a common name-space prefix, or even the object name with a prefix that is a concatenation of a common name space and the design-time folder path. Choosing a folder-independent naming rule provides the freedom to change the design-time folder structure at a later point in time without causing incompatible changes to run-time names.

**Related Information**  


[Run-Time Name Spaces in SAP HDI](run-time-name-spaces-in-sap-hdi-a53bf96.md "SAP HDI defines a strict separation between the naming of run-time objects and the organization of design-time files.")

[The SAP HDI Name-space Configuration Syntax](the-sap-hdi-name-space-configuration-syntax-c38cbef.md "In SAP HANA Deployment Infrastructure (HDI), the contents of the .hdinamespace file are formatted with the JSON syntax")

[Define Run-Time Name-Space Rules for SAP HDI](define-run-time-name-space-rules-for-sap-hdi-5e638d4.md "Define rules for run-time name spaces in SAP HANA Deployment Infrastructure (HDI) containers.")

