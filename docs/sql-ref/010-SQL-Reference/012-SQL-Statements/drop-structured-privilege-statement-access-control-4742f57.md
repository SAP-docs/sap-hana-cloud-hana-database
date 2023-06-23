<!-- loio4742f573d0c24e9084a699d464bf20c7 -->

# DROP STRUCTURED PRIVILEGE Statement \(Access Control\)

Drops a structured \(analytic\) privilege.



## Syntax

```
DROP STRUCTURED PRIVILEGE <privilege_name>
```



## Syntax Elements


<dl>
<dt><b>

*<privilege\_name\>*

</b></dt>
<dd>

Specifies the name of the analytic privilege to drop.



</dd>
</dl>



<a name="loio4742f573d0c24e9084a699d464bf20c7__section_nn2_bcn_zcb"/>

## Permissions

You must have the STRUCTUREDPRIVILEGE ADMIN privilege to execute this statement.



<a name="loio4742f573d0c24e9084a699d464bf20c7__section_s32_bcn_zcb"/>

## Description

Drops an analytic privilege. Analytic privileges provide fine-grained control over which data a user can see within a view. Analytic privileges are sometimes referred to as*structured privileges*.

**Related Information**  


[Analytic Privileges](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/db08ea0cbb571014a386f851122958b2.html "Analytic privileges grant different users access to different portions of data in the same view based on their business role. Within the definition of an analytic privilege, the conditions that control which data users see is defined using SQL.") :arrow_upper_right:

[STRUCTURED\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/structured-privileges-system-view-20ffdc2.md "Provides information about available structured (analytic) privileges.")

[ALTER STRUCTURED PRIVILEGE Statement \(Access Control\)](alter-structured-privilege-statement-access-control-fd40165.md "Alters a structured (analytic) privilege, replacing the existing definition of the structured privilege with the new definition.")

[CREATE STRUCTURED PRIVILEGE Statement \(Access Control\)](create-structured-privilege-statement-access-control-622b2df.md "Creates a structured (analytic) privilege.")

