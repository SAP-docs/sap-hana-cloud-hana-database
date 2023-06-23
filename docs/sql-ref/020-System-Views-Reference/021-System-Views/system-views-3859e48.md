<!-- loio3859e48180bb4cf8a207e15cf25a7e57 -->

# System Views

System views allow you to query for various information about the system state using SQL commands. The results appear as tables.

System views are located in the SYS schema.

**Time-related columns in views**: Time-related columns in system views contain data in the local time \(not UTC\) unless specifically noted in the description for the column.

**Metadata views vs monitoring views**: SAP HANA system views are separated into two categories: **metadata** views and **monitoring** \(or runtime\) views.

Metadata views provide metadata about objects in the database, including options or settings that were set using a DDL statement. Monitoring views provide actual HANA runtime data, including statistics and status information related to the execution of DML statements. Monitoring views start with M\_.

Normally, the names are symmetric - for example, TABLES and M\_TABLES, and they may also include some other defining abbreviation.

