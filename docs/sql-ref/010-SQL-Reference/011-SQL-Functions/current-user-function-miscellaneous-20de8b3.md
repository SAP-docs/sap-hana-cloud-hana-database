<!-- loio20de8b3775191014acc4e9ee60df1746 -->

# CURRENT\_USER Function \(Miscellaneous\)

Returns the current user name at the current statement context.



<a name="loio20de8b3775191014acc4e9ee60df1746__sql_function_current_user_1sql_function_current_user_syntax"/>

## Syntax

```
CURRENT_USER
```



<a name="loio20de8b3775191014acc4e9ee60df1746__sql_function_current_user_1sql_function_current_user_description"/>

## Description

Returns the current user name at the current statement context. This is the user name that is currently at the top of authorization stack.

SESSION\_USER and CURRENT\_USER are similar functions, but there are differences. SESSION\_USER reflects how the session connected to the server, while CURRENT\_USER may be affected by the SQL SECURITY clause and reflects how permissions are applied.



<a name="loio20de8b3775191014acc4e9ee60df1746__sql_function_current_user_1sql_function_current_user_examples"/>

## Example

In the following example, USER A creates a procedure:

```
CREATE PROCEDURE USER_A.PROC1 LANGUAGE SQLSCRIPT SQL SECURITY DEFINER AS
 BEGIN
     SELECT CURRENT_USER "current user" FROM DUMMY;
 END;
```

USER B calls the procedure USER\_A.PROC1, which returns USER\_A:

```
CALL USER_A.PROC1;
```

USER A also creates the following procedure:

```
CREATE PROCEDURE USER_A.PROC2 LANGUAGE SQLSCRIPT SQL SECURITY INVOKER AS
 BEGIN
     SELECT CURRENT_USER "current user" FROM DUMMY;
 END;
```

USER B calls the procedure USER\_A.PROC2, which returns USER\_B:

```
CALL USER_A.PROC2;
```

**Related Information**  


[SESSION\_USER Function \(Miscellaneous\)](session-user-function-miscellaneous-20e76c1.md "Returns the user name of the current session.")

