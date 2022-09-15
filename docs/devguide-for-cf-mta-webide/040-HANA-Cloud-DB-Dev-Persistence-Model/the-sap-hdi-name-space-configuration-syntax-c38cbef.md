<!-- loioc38cbef504b24a90a2a99c9d97633a85 -->

# The SAP HDI Name-space Configuration Syntax

In SAP HANA Deployment Infrastructure \(HDI\), the contents of the `.hdinamespace` file are formatted with the JSON syntax



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



<a name="loioc38cbef504b24a90a2a99c9d97633a85__section_wd1_dy2_1t"/>

## name

Use the `name` property in the `.hdinamespace` configuration file to specify the name of run-time space to map to the name of \(and objects in\) the file-system folder where the `.hdinamespace` file is located.

> ### Sample Code:  
> ```
> 
> "name" : "com.sap.hana.example",
> 
> ```



<a name="loioc38cbef504b24a90a2a99c9d97633a85__section_yrk_dy2_1t"/>

## subfolder

Use the `subfolder` key in the `.hdinamespace` configuration file to specify if the name of the file-system folder where the `.hdinamespace` file is located should be **appended** to the name of the corresponding run-time space or **ignored**.

> ### Sample Code:  
> ```
> {
> "name" : "com.sap.hana.example",
> "subfolder" : "<[append | ignore]>"
> }
> ```

For those sub-folders without a name-space configuration file, the name space depends on the value of the `subfolder` key in the name-space configuration file in the parent folder, for example: `append` or `ignore`.

-   `"subfolder" : "ignore"`

    The sub-folder inherits the name-space information from the parent folder. In this case, all sub-folders use the same run-time name space.

    <a name="loioc38cbef504b24a90a2a99c9d97633a85__table_yfc_cbf_1t"/>Design-Time Folder Names Ignored in Run-Time Name Space


    <table>
    <tr>
    <th valign="top">

    Design-time Resource Path


    
    </th>
    <th valign="top">

    Name of Run-time Object \(ignore\)


    
    </th>
    </tr>
    <tr>
    <td valign="top">

     `/src/` 


    
    </td>
    <td valign="top">

     <code>com.sap.hana.example::<i class="varname">&lt;Object_Name&gt;</i></code> 


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     `/src/db` 


    
    </td>
    <td valign="top">

     <code>com.sap.hana.example::<i class="varname">&lt;Object_Name&gt;</i></code> 


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     `/src/db/proc` 


    
    </td>
    <td valign="top">

     <code>com.sap.hana.example::<i class="varname">&lt;Object_Name&gt;</i></code> 


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     `/src/data` 


    
    </td>
    <td valign="top">

     <code>com.sap.hana.example::<i class="varname">&lt;Object_Name&gt;</i></code> 


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     `/src/data/import` 


    
    </td>
    <td valign="top">

     <code>com.sap.hana.example::<i class="varname">&lt;Object_Name&gt;</i></code> 


    
    </td>
    </tr>
    </table>
    
-   `"subfolder" : "append"`

    The run-time name-space for a sub-folder is derived by appending the sub-folder name to the name-space name of the parent folder.

    <a name="loioc38cbef504b24a90a2a99c9d97633a85__table_j4j_jbf_1t"/>Design-Time Folder Names Appended to Run-time Name Space


    <table>
    <tr>
    <th valign="top">

    Design-time Resource Path


    
    </th>
    <th valign="top">

    Name of Run-Time Object \(append\)


    
    </th>
    </tr>
    <tr>
    <td valign="top">

     `/src/` 


    
    </td>
    <td valign="top">

     <code>com.sap.hana.example::<i class="varname">&lt;Object_Name&gt;</i></code> 


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     `/src/db` 


    
    </td>
    <td valign="top">

     <code>com.sap.hana.example.db::<i class="varname">&lt;Object_Name&gt;</i></code> 


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     `/src/db/proc` 


    
    </td>
    <td valign="top">

     <code>com.sap.hana.example.db.proc::<i class="varname">&lt;Object_Name&gt;</i></code> 


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     `/src/data` 


    
    </td>
    <td valign="top">

     <code>com.sap.hana.example.data::<i class="varname">&lt;Object_Name&gt;</i></code> 


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     `/src/data/import` 


    
    </td>
    <td valign="top">

     <code>com.sap.hana.example.data.import::<i class="varname">&lt;Object_Name&gt;</i></code> 


    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Run-Time Name Spaces in SAP HDI](run-time-name-spaces-in-sap-hdi-a53bf96.md "SAP HDI defines a strict separation between the naming of run-time objects and the organization of design-time files.")

[The HDI Name-Space Configuration File](the-hdi-name-space-configuration-file-6188d22.md "The SAP HANA Deployment Infrastructure (HDI) uses a JSON resource to define naming rules for run-time objects.")

[Define Run-Time Name-Space Rules for SAP HDI](define-run-time-name-space-rules-for-sap-hdi-5e638d4.md "Define rules for run-time name spaces in SAP HANA Deployment Infrastructure (HDI) containers.")

