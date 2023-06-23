<!-- loio20dde16475191014bf3090e6b2e9857f -->

# CURRENT\_CONNECTION Function \(Miscellaneous\)

Returns the ID of the current connection.



<a name="loio20dde16475191014bf3090e6b2e9857f__sql_function_current_connection_1sql_function_current_connection_syntax"/>

## Syntax

```
CURRENT_CONNECTION
```



<a name="loio20dde16475191014bf3090e6b2e9857f__sql_function_current_connection_1sql_function_current_connection_description"/>

## Description

Returns the ID of the current connection as an integer value.

This function is called without braces.



<a name="loio20dde16475191014bf3090e6b2e9857f__sql_function_current_connection_1sql_function_current_connection_examples"/>

## Example

The following query returns the ID of the current connection.

```
SELECT CURRENT_CONNECTION "current connection" FROM DUMMY;
```

**Related Information**  


[M\_CONNECTIONS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-connections-system-view-20abcf1.md "Provides detailed information on connections between a client and a database. Information includes: connection status, client information, connection type, and resource utilization.")

