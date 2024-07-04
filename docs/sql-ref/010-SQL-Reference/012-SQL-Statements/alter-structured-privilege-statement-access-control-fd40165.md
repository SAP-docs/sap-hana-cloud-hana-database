<!-- loiofd4016543766478ea6304c3909b4245c -->

# ALTER STRUCTURED PRIVILEGE Statement \(Access Control\)

Alters a structured \(analytic\) privilege, replacing the existing definition of the structured privilege with the new definition.



## Syntax

```
ALTER STRUCTURED PRIVILEGE <privilege_name> FOR SELECT 
   ON <object_name_list> <filter_condition>
```



## Syntax Elements


<dl>
<dt><b>

*<privilege\_name\>*

</b></dt>
<dd>

Specifies a name for the privilege.

```
<privilege_name> ::= [<schema>.]<identifier>
```



</dd><dt><b>

*<object\_name\_list\>*

</b></dt>
<dd>

Specifies the views to be restricted by this analytic privilege.

```
<object_name_list> ::= <object_name> [{, <object_name>}...]

<object_name> :: = [<schema>.]<identifier>
```

*<object\_name\>* specifies a view registered for a SQL-based analytic privilege check.



</dd><dt><b>

*<filter\_condition\>*

</b></dt>
<dd>

Restricts the returned rows of the specified views for users who have been granted this privilege.

```
<filter_condition> ::= { <static_filter_condition> | <dynamic_filter_condition> }

<static_filter_condition> ::= WHERE <condition>

<dynamic_filter_condition> ::= CONDITION PROVIDER [<schema>.]<identifier>
```

*<condition\>* restricts the rows returned and can contain subqueries.

\[*<schema\>*.\]*<identifier\>* specifies the procedure providing the dynamic restriction.



</dd>
</dl>



<a name="loiofd4016543766478ea6304c3909b4245c__section_nn2_bcn_zcb"/>

## Permissions

You must have the STRUCTUREDPRIVILEGE ADMIN privilege to execute this statement.



<a name="loiofd4016543766478ea6304c3909b4245c__section_s32_bcn_zcb"/>

## Description

Alters an analytic privilege. Analytic privileges provide fine-grained control over which data a user can see within a view. Analytic privileges are sometimes referred to as*structured privileges*.

**Related Information**  


[Analytic Privileges](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/db08ea0cbb571014a386f851122958b2.html "Analytic privileges grant different users access to different portions of data in the same view based on their business role. Within the definition of an analytic privilege, the conditions that control which data users see is defined using SQL.") :arrow_upper_right:

[Structure of Analytic Privileges](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2024_3_QRC/en-US/349f423ce2154e3e9b39ed525d46aa94.html "An analytic privilege consists of a set of restrictions against which user access to a particular calculation view or SQL view is verified. These restrictions are specified as filter conditions that are fully SQL based.") :arrow_upper_right:

[STRUCTURED\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/structured-privileges-system-view-20ffdc2.md "Provides information about available structured (analytic) privileges.")

[DROP STRUCTURED PRIVILEGE Statement \(Access Control\)](drop-structured-privilege-statement-access-control-4742f57.md "Drops a structured (analytic) privilege.")

[CREATE STRUCTURED PRIVILEGE Statement \(Access Control\)](create-structured-privilege-statement-access-control-622b2df.md "Creates a structured (analytic) privilege.")

[CREATE VIEW Statement \(Data Definition\)](create-view-statement-data-definition-20d5fa9.md "Creates a view on the database.")

[EFFECTIVE\_STRUCTURED\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/effective-structured-privileges-system-view-d201952.md "Displays the structured privileges applied to an object.")

