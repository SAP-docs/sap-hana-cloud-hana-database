<!-- loio5157398354a14cf49110fac593f83997 -->

# GENERATE\_PASSWORD Function \(Security\)

Generates a password.



<a name="loio5157398354a14cf49110fac593f83997__sql_function_greatest_1sql_function_greatest_syntax"/>

## Syntax

```
GENERATE_PASSWORD( <password_length> [, <usergroup_name>] )
```



<a name="loio5157398354a14cf49110fac593f83997__section_rhv_sj1_t1b"/>

## Syntax Elements


<dl>
<dt><b>

*<password\_length\>*

</b></dt>
<dd>

Specifies the length of the password to generate as an integer.



</dd><dt><b>

*<usergroup\_name\>*

</b></dt>
<dd>

Specifies a usergroup name. If there are password policy parameters defined for the usergroup, they are applied during password generation.



</dd>
</dl>



<a name="loio5157398354a14cf49110fac593f83997__sql_function_greatest_1sql_function_greatest_description"/>

## Description

Generates and returns a password of type NVARCHAR\(128\).

> ### Note:  
> The function call can fail displaying the following out of range error message if the password policy and exclude list are too restrictive:
> 
> ```
> password exclude list too restrictive
> ```
> 
> Depending on the strictness of the password exclude list, it might suffice to retry the command.



<a name="loio5157398354a14cf49110fac593f83997__sql_function_greatest_1sql_function_greatest_examples"/>

## Example

The following example returns a generated password of 16 characters::

```
SELECT GENERATE_PASSWORD(16) FROM Dummy;
```

