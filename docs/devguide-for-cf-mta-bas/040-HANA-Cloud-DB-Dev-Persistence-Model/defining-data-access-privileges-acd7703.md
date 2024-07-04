<!-- loioacd770361d4945daaa2dfc701a1b308d -->

# Defining Data Access Privileges

Use the analytic privilege editor in *SAP Business Application Studio* to create analytic privileges.

You create analytic privileges to grant different users access to different portions of data in the same view based on their business role. Within the definition of an analytic privilege, the conditions that control which data users see is defined using SQL.

Standard object privileges \(`SELECT`, `ALTER`, `DROP`, and more\) implement coarse-grained authorization at object level only. Users either have access to an object, such as a table, view or procedure, or they don't. Often finer granular access control is required and the visibility of data should be based on certain column values or combination of column values. Analytic privileges are used in the SAP HANA database to provide such fine-grained control at row level of which data individual users can see within the same view.



## Example

Sales data for all regions is contained within one calculation view. However, regional sales managers should only see the data for their region. In this case, an analytic privilege could be modeled so that they can all query the view, but only the data that each user is authorized to see is returned.

**Related Information**  


[Create Static SQL Analytic Privileges](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2024_3_QRC/en-US/55aebdcf8d564412834f75b03c127a22.html "For static SQL analytic privileges, attribute columns in views can be used to define fixed restrictions on data access. These restrictions are defined in the analytic privilege editor at design time.") :arrow_upper_right:

[Create Dynamic SQL Analytic Privileges](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2024_3_QRC/en-US/2408cd1bef564284b8aaea7d8c267010.html "Dynamic SQL analytic privileges determine the filter condition string to restrict data access at runtime. You use the analytic privilege editor to define the dynamic SQL analytic privilege.") :arrow_upper_right:

[Create Analytic Privileges Using SQL Expressions](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2024_3_QRC/en-US/1716378df3334e4db8f5668fc6fbbae9.html "The analytic privilege editor gives you the flexibility to create SQL-based analytic privileges using the familiar SQL environment. You can create both static and dynamic SQL analytic privileges by writing relevant SQL expressions.") :arrow_upper_right:

[Structure of Analytic Privileges](https://help.sap.com/viewer/460112ecd20e42c0a647979434b32412/2024_3_QRC/en-US/349f423ce2154e3e9b39ed525d46aa94.html "An analytic privilege consists of a set of restrictions against which user access to a particular calculation view or SQL view is verified. These restrictions are specified as filter conditions that are fully SQL based.") :arrow_upper_right:

