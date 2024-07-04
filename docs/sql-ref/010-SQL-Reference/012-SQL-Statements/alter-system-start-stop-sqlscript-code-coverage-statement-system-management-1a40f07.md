<!-- loio1a40f07c15c3401083fc8fd8b9786f7b -->

# ALTER SYSTEM \{START | STOP\} SQLSCRIPT CODE COVERAGE Statement \(System Management\)

Starts and stops a SQLScript code coverage session for functions and procedures.



## Syntax

To start SQLScript code coverage:

```
ALTER SYSTEM START SQLSCRIPT CODE COVERAGE
 [ FOR DEBUG TOKEN <token_id> ]
 [ FOR USER <user_id> ]
 [ FOR APPLICATION USER <application_user_id> ]
 [ FOR SESSION <session_id> ]
```

To stop SQLScript code coverage:

```
ALTER SYSTEM STOP SQLSCRIPT CODE COVERAGE
```



<a name="loio1a40f07c15c3401083fc8fd8b9786f7b__sql_alter_system_start_perftrace_1sql_alter_system_start_perftrace_syntax_element"/>

## Syntax Elements


<dl>
<dt><b>

*<token\_id\>*

</b></dt>
<dd>

Specifies the token that the code coverage applies to.



</dd><dt><b>

*<user\_id\>*

</b></dt>
<dd>

Specifies the database user ID that the code coverage applies to.



</dd><dt><b>

*<application\_user\_id\>*

</b></dt>
<dd>

Specifies the ID of the application user that the code coverage applies to.



</dd><dt><b>

*<session\_id\>*

</b></dt>
<dd>

Specifies the ID of the session that the code coverage applies to.



</dd>
</dl>



<a name="loio1a40f07c15c3401083fc8fd8b9786f7b__sql_alter_system_start_perftrace_1sql_alter_system_start_perftrace_description"/>

## Description

See the *SAP HANA Cloud, SAP HANA Database SQLScript Reference* for more information on code coverage support for functions and procedures in SQLScript.

SAP HANA stores the results of a code coverage session in the M\_SQLSCRIPT\_CODE\_COVERAGE\_RESULTS monitoring view and stores the definitions of objects that were used during a code coverage session in the M\_SQLSCRIPT\_CODE\_COVERAGE\_OBJECT\_DEFINITIONS monitoring view.

Select from the monitoring views at any time, and from any column, you are interested in after starting code coverage. However, the full content of code coverage run is visible only after the query triggered in the second session \(which is being covered\) finishes \(described in the second example, below\).

The content in the monitoring views is overwritten in these views each time you stop a SQLScript code coverage session and start a new one. Since the data is temporary, copy or export the content from these views to retain data recorded by a SQLScript code coverage session before executing ALTER SYSTEM STOP SQLSCRIPT CODE COVERAGE.

You must have at least two connections for code coverage. In the first session you execute the codes on which you run code coverage, and in the second session you start the code coverage for a specific connection ID to record the coverage.



<a name="loio1a40f07c15c3401083fc8fd8b9786f7b__section_e1m_tpj_mfb"/>

## Permissions

You must have the EXECUTE, DEBUG, and ATTACH DEBUGGER object privileges on the relevant objects to perform code coverage.



<a name="loio1a40f07c15c3401083fc8fd8b9786f7b__sql_alter_system_stop_perftrace_1sql_alter_system_start_perftrace_example"/>

## Example

SAP HANA requires two sessions to perform the code coverage. The examples below use session A to execute the code on which you run code coverage, and session B starts the code coverage for a specific connection ID to record the coverage.

1.  In either session, create the `limitedLoop` and `dummy_proc` procedures:

    ```
    CREATE PROCEDURE limitedLoop() AS
    BEGIN
       DECLARE i BIGINT := 0;
        LOOP
          i := i + 1;
          IF :i > 27 THEN
                BREAK;
          END IF;
       END LOOP;
    END;
    CREATE PROCEDURE dummy_proc() AS
    BEGIN
        SELECT * FROM DUMMY;
        CALL limitedLoop();
    END;
    ```

2.  From session A, issue this to determine the connection ID:

    ```
    SELECT SESSION_CONTEXT('CONN_ID') FROM DUMMY;
    ```

3.  In session B, start code coverage by using the connection ID of the user who is executing the code in session A \(this example uses a connection ID of 203247\):

    ```
    ALTER SYSTEM START SQLSCRIPT CODE COVERAGE FOR SESSION '203247';
    ```

4.  From session A, call the `dummy_proc` procedure:

    ```
    CALL dummy_proc();
    ```

5.  From session B, view the code coverage by querying the M\_SQLSCRIPT\_CODE\_COVERAGE\_RESULTS and M\_SQLSCRIPT\_CODE\_COVERAGE\_OBJECT\_DEFINITIONS monitoring views

    ```
    SELECT * FROM M_SQLSCRIPT_CODE_COVERAGE_RESULTS;
    SELECT * FROM M_SQLSCRIPT_CODE_COVERAGE_OBJECT_DEFINITIONS;
    ```

    If required, store the contents of the monitoring views for later reference \(this can be a regular or a local temporary table\):

    ```
    CREATE LOCAL TEMPORARY TABLE "#SomeTableName" AS (SELECT * FROM M_SQLSCRIPT_CODE_COVERAGE_RESULTS) WITH DATA;
    ```

6.  From session B, disable the code coverage \(this also clears the existing code coverage\):

    ```
    ALTER SYSTEM STOP SQLSCRIPT CODE COVERAGE;
    ```


**Related Information**  


[SAP HANA Cloud, SAP HANA SQLScript Reference](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/28f2d64d4fab4e789ee0070be418419d.html "This reference describes how to use the SQL extension SAP HANA SQLScript to embed data-intensive application logic into SAP HANA.") :arrow_upper_right:

[CREATE PROCEDURE Statement \(Procedural\)](create-procedure-statement-procedural-20d4674.md "Creates a procedure that uses the specified programming language.")

[CREATE FUNCTION Statement \(Procedural\)](create-function-statement-procedural-20d42e7.md "Creates a user-defined function.")

[M\_SQLSCRIPT\_CODE\_COVERAGE\_RESULTS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-sqlscript-code-coverage-results-system-view-9628091.md "Provides per-session SQLScript code coverage results.")

[M\_SQLSCRIPT\_CODE\_COVERAGE\_OBJECT\_DEFINITIONS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-sqlscript-code-coverage-object-definitions-system-view-7992c97.md "Provides definitions for the objects referenced in SQLScript code coverage results.")

