<!-- loioa53bf9619bdd44e1bc20fba3d21dc2c7 -->

# Run-Time Name Spaces in SAP HDI

SAP HDI defines a strict separation between the naming of run-time objects and the organization of design-time files.

In SAP HANA Deployment Infrastructure \(HDI\), there is no simple, one-to-one mapping between the file-system structure and the names of the resulting run-time objects. Instead, the names of run-time objects are determined by naming rules defined in HDI name-space files. If desired, the file-system structure can still be used to derive the run-time name space of an object. However, decoupling design-time file structure and run-time name-space names allows the file-system structure to reflect the organization of work, and it is easy to relocate design-time resources without changing run-time name spaces. Note that if design-time folder names do not contribute to run-time names, you avoid problems with limitations on name length.

In SAP HANA, name-space rules for run-time objects are defined in one or more files named `.hdinamespace`, which must be located in the folder to which the naming rules apply - or the root folder of a folder structure to which the naming rules apply. The name-space rules allow you to specify the following elements:

-   A name-space prefix, for example, `com.acme.hana.example`

-   The name of design-time folder\(s\) containing the deployed objects


> ### Code Syntax:  
> Run-Time Name Space with Appended Folder Name
> 
> ```
> com.acme.hana.example.[/pandoc/div/div/note/codeblock/code/varname
>      {"varname"}) <Design-Time_Folder_Name> (varname]::[/pandoc/div/div/note/codeblock/code/varname
>      {"varname"}) <Run-Time_Object_Name> (varname]
> ```

The following table illustrates how the rules specified in the name-space configuration file influence the way run-time objects are named. If the name-space rules specify that the name of the design-time sub-folder should be **appended** to the run-time name-space prefix, for example, `com.acme.hana.example`:

<a name="loioa53bf9619bdd44e1bc20fba3d21dc2c7__table_j4j_jbf_1t"/>Folder Names Appended to the Run-Time Name Space


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

 <code>com.acme.hana.example::<i class="varname">&lt;Object_Name&gt;</i></code> 



</td>
</tr>
<tr>
<td valign="top">

 `/src/db` 



</td>
<td valign="top">

 <code>com.acme.hana.example.db::<i class="varname">&lt;Object_Name&gt;</i></code> 



</td>
</tr>
<tr>
<td valign="top">

 `/src/data` 



</td>
<td valign="top">

 <code>com.acme.hana.example.data::<i class="varname">&lt;Object_Name&gt;</i></code> 



</td>
</tr>
</table>

**Related Information**  


[The HDI Name-Space Configuration File](the-hdi-name-space-configuration-file-6188d22.md "The SAP HANA Deployment Infrastructure (HDI) uses a JSON resource to define naming rules for run-time objects.")

[The SAP HDI Name-space Configuration Syntax](the-sap-hdi-name-space-configuration-syntax-c38cbef.md "In SAP HANA Deployment Infrastructure (HDI), the contents of the .hdinamespace file are formatted with the JSON syntax")

