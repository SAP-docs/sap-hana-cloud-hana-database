<!-- loiofb097f2620c645d18064ce6b93c24a1e -->

# ALTER SYSTEM CLEAR INIFILE CONTENT HISTORY Statement \(System Management\)

Clears `ini` file content history from the catalog.



<a name="loiofb097f2620c645d18064ce6b93c24a1e__sql_alter_system_clear_traces_1sql_alter_system_clear_traces_syntax"/>

## Syntax

```
ALTER SYSTEM CLEAR INIFILE CONTENT HISTORY
```



<a name="loiofb097f2620c645d18064ce6b93c24a1e__sql_alter_system_clear_traces_1sql_alter_system_clear_traces_description"/>

## Description

When you use this statement, the specified `ini` file catalog history data is cleared from the M\_INIFILE\_CONTENT\_HISTORY system view and underlying table.

In addition to deleting the records of `ini` file changes, this statement also inserts a record into M\_INIFILE\_CONTENT\_HISTORY to indicate the operation.



<a name="loiofb097f2620c645d18064ce6b93c24a1e__section_qns_lgd_fcb"/>

## Permissions

You must have the MONITOR ADMIN system privilege to execute this statement.

**Related Information**  


[M\_INIFILE\_CONTENTS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-inifile-contents-system-view-20b16a7.md "Provides configuration information from INI files.")

[M\_INIFILE\_CONTENT\_HISTORY System View](../../020-System-Views-Reference/022-Monitoring-Views/m-inifile-content-history-system-view-a42a0b8.md "Provides change history information for configuration (ini) files.")

[M\_INIFILES System View](../../020-System-Views-Reference/022-Monitoring-Views/m-inifiles-system-view-20b18dc.md "Provides information about all configuration files.")

[Configuring SAP HANA System Properties (INI Files)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/3f1a6a7dc31049409e1a9f9108d73d51.html "An SAP HANA database has several configuration (*.ini) files that contain properties for configuring the database and services.") :arrow_upper_right:

