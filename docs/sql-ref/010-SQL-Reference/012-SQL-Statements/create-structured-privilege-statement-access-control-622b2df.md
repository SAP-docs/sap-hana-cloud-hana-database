<!-- loio622b2dfdce81455a949fb2bb3be014d2 -->

# CREATE STRUCTURED PRIVILEGE Statement \(Access Control\)

Creates a structured \(analytic\) privilege.



## Syntax

```
CREATE STRUCTURED PRIVILEGE <privilege_name> FOR SELECT 
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



## Description

Creates an analytic privilege. Analytic privileges provide fine-grained control over which data a user can see within a view. Analytic privileges are also referred to as*structured privileges*.

The new structured privilege is automatically applied to the owner/creator of the privilege; however, the owner is not listed as a grantee of the privilege in the GRANTED\_PRIVILEGES system view because they have the privilege applied to them by virtue of ownership.



<a name="loio622b2dfdce81455a949fb2bb3be014d2__section_ny1_w1n_zcb"/>

## Permissions

Requires one of:

-   CREATE STRUCTURED PRIVILEGE system privilege
-   STRUCTUREDPRIVILEGE ADMIN system privilege
-   CREATE OBJECT STRUCTURED PRIVILEGE object privilege on the target view to be secured with the analytic privilege

**Related Information**  


[Analytic Privileges](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/db08ea0cbb571014a386f851122958b2.html "Analytic privileges grant different users access to different portions of data in the same view based on their business role. Within the definition of an analytic privilege, the conditions that control which data users see is defined using SQL.") :arrow_upper_right:

[Structure of Analytic Privileges](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2023_4_QRC/en-US/349f423ce2154e3e9b39ed525d46aa94.html "An analytic privilege consists of a set of restrictions against which user access to a particular calculation view or SQL view is verified. These restrictions are specified as filter conditions that are fully SQL based.") :arrow_upper_right:

[STRUCTURED\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/structured-privileges-system-view-20ffdc2.md "Provides information about available structured (analytic) privileges.")

[ALTER STRUCTURED PRIVILEGE Statement \(Access Control\)](alter-structured-privilege-statement-access-control-fd40165.md "Alters a structured (analytic) privilege, replacing the existing definition of the structured privilege with the new definition.")

[DROP STRUCTURED PRIVILEGE Statement \(Access Control\)](drop-structured-privilege-statement-access-control-4742f57.md "Drops a structured (analytic) privilege.")

[CREATE VIEW Statement \(Data Definition\)](create-view-statement-data-definition-20d5fa9.md "Creates a view on the database.")

[EFFECTIVE\_STRUCTURED\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/effective-structured-privileges-system-view-d201952.md "Displays the structured privileges applied to an object.")

