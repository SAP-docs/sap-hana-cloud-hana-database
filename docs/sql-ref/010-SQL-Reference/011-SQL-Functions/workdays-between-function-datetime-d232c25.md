<!-- loiod232c253d295101486a3dee449981b3f -->

# WORKDAYS\_BETWEEN Function \(Datetime\)

Computes the number of workdays between a specified start date and a specified end date.



<a name="loiod232c253d295101486a3dee449981b3f__sql_function_workdays_between_1sql_function_workdays_between_syntax"/>

## Syntax

```
WORKDAYS_BETWEEN(
   <factory_calendar_id>, 
   <start_date>, 
   <end_date> 
   [, <source_schema>
   [, <table_name_suffix>, 
   [, <client> ] ] ] )
```



<a name="loiod232c253d295101486a3dee449981b3f__sql_function_workdays_between_1sql_function_add_workdays_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<factory\_calendar\_id\>*

</b></dt>
<dd>

Specifies the ID of the factory calendar.

```
<factory_calendar_id> ::= <string_literal>
```



</dd><dt><b>

*<start\_date\>*

</b></dt>
<dd>

Specifies the start date. You can use either a DAYDATE type or a date format string \(for example '20140101' or '2014-01-01'\) for this parameter.

```
<start_date> ::= <string_literal> | <DAYDATE>
```



</dd><dt><b>

*<end\_date\>*

</b></dt>
<dd>

Specifies the end date. You can use either a DAYDATE type or a date format string \(for example '20140101' or '2014-01-01'\) for this parameter.

```
<end_date> ::= <string_literal> | <DAYDATE>
```



</dd><dt><b>

*<source\_schema\>*

</b></dt>
<dd>

Specifies the schema containing the Factory Calendar table or the Factory And Holiday Calendar tables.

```
<source_schema> ::= <string_literal>
```

This parameter can be omitted if the schema is the same as the current schema.



</dd><dt><b>

*<table\_name\_suffix\>*

</b></dt>
<dd>

Specifies the suffix appended to the standard Factory Calendar table name or the standard Factory And Holiday Calendar table names if using an alternative set of tables. For example, with suffix '\_XYZ' the function accesses the alternative tables TFACS\_XYZ or FHC\_C\_FCAL\_XYZ instead of standard tables TFACS or FHC\_C\_FCAL. If omitted or empty, the standard tables are used.

```
<table_name_suffix> ::= <string_literal>
```



</dd><dt><b>

*<client\>*

</b></dt>
<dd>

Specifies the client used for the client-dependent Factory And Holiday Calendar implementation. If omitted or empty, then the function tries to retrieve the client from the context \(user parameter\), which can be set in the context by ALTER USER *<user\_name\>* SET PARAMETER CLIENT = *<client\>*. The client is ignored if the client-independent Factory Calendar implementation is active.

```
<client> ::= <string_literal>
```



</dd>
</dl>



<a name="loiod232c253d295101486a3dee449981b3f__sql_function_workdays_between_1sql_function_workdays_between_returns"/>

## Return Type

INTEGER



<a name="loiod232c253d295101486a3dee449981b3f__sql_function_workdays_between_1sql_function_workdays_between_description"/>

## Description

There are two different implementations for workday calculation in ABAP based systems like SAP S/4HANA:

-   The Factory Calendar that stores its data in a single table TFACS.
-   The Factory And Holiday Calendar that stores its data in multiple tables \(FHC\*\).

By default, the WORKDAYS\_BETWEEN functions assume that the Factory Calendar is active. Once table FHC\_CONFIG \(or FHC\_CONFIG *<table\_suffix\>* where *<table\_suffix\>* is specified\) is available in the system and contains an entry with KEY\_FIELD = ‘MIGRATION\_COMPLETED' and VALUE = ‘X’ for the specified client, the WORKDAYS\_BETWEEN functions assume that the newer Factory And Holiday Calendar is active.

The respective tables must be available in the SAP HANA database to use the WORKDAYS\_BETWEEN function. In SAP BW, SAP CRM, and SAP ERP running on an SAP HANA database, these tables are located in the ABAP schema SAP*<SID\>*. For other SAP HANA database systems, these tables can be replicated from an SAP Business Suite system.

When the Factory Calendar is active, WORKDAYS\_BETWEEN accesses the table TFACS \(or TFACS*<table\_suffix\>* if *<table\_suffix\>* is specified\). When the Factory And Holiday Calendar is active, WORKDAYS\_BETWEEN accesses the following tables, which must be available in the system with *<table\_suffix\>* appended to their respective names if *<table\_suffix\>* is specified:

-   FHC\_C\_FCAL
-   FHC\_C\_FCAL\_EXC
-   FHC\_C\_HCAL
-   FHC\_C\_HCAL\_ASSGN
-   FHC\_C\_HOL
-   FHC\_C\_HOL\_EASTER
-   FHC\_C\_HOL\_FIXED
-   FHC\_C\_HOL\_FLOAT
-   FHC\_C\_HOL\_FLDATE
-   FHC\_C\_HOL\_WKDAY
-   FHC\_CONFIG

Computations are done with respect to a factory calendar with ID *<factory\_calendar\_id\>*.

If the *<start\_date\>* is earlier than or equal to the *<end\_date\>*, then the number of working days in the period starting at the *<start\_date\>* and ending at the *<end\_date\>* is returned.

If the *<start\_date\>* is after the *<end\_date\>*, then a negative number of workdays in the period starting at the *<end\_date\>* and ending at the *<start\_date\>* is returned.

The returned number of days always includes the day of the *<end\_date\>*, but excludes the day of the *<start\_date\>*.



<a name="loiod232c253d295101486a3dee449981b3f__sql_function_workdays_between_1sql_function_workdays_between_examples"/>

## Examples

The following examples use the Factory Calendar table for the month of January 2014 exclusively. For examples using the Factory And Holiday Calendar, see [Factory Calendar](https://help.sap.com/docs/ABAP_PLATFORM_NEW/b5670aaaa2364a29935f40b16499972d/f7cbd3c336f84dc09c85639c55b4309f.html).


<table>
<tr>
<th valign="top">

TFACS bitfield

</th>
<th valign="top">

Day of the month

</th>
<th valign="top">

Reason for not working

</th>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
<td valign="top">

Public Holiday

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

2

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

3

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

4

</td>
<td valign="top">

Weekend

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

5

</td>
<td valign="top">

Weekend

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

6

</td>
<td valign="top">

Public Holiday

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

7

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

8

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

9

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

10

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

11

</td>
<td valign="top">

Weekend

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

12

</td>
<td valign="top">

Weekend

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

13

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

14

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

15

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

16

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

17

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

18

</td>
<td valign="top">

Weekend

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

19

</td>
<td valign="top">

Weekend

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

20

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

21

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

22

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

23

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

24

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

25

</td>
<td valign="top">

Weekend

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

26

</td>
<td valign="top">

Weekend

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

27

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

28

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

29

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

30

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

31

</td>
<td valign="top">

 

</td>
</tr>
</table>

The following example returns the value 1 for work days between the two specified dates. **Result:** A single workday has been computed starting on the 9th and finishing on, but not including, the 10th.

```
SELECT WORKDAYS_BETWEEN('01', '2014-01-09', '2014-01-10' , 'FCTEST') "workdays" FROM DUMMY; 
```

The following example returns the value -1 for work days between the two specified dates. **Result:** A single workday has been computed on the 10th, excluding the day of the 9th.

```
SELECT WORKDAYS_BETWEEN('01', '2014-01-10', '2014-01-09' , 'FCTEST') "workdays" FROM DUMMY;
```

The following example returns the value 1 for work days between the two specified dates. **Result:**The single workday has been computed on the 17th. The weekend period and the end date day are excluded.

```
SELECT WORKDAYS_BETWEEN('01', '2014-01-17', '2014-01-20', 'FCTEST') "workdays" FROM DUMMY;
```

The following example returns the value -1 for work days between the two specified dates. **Result:** The single workday has been computed on the 20th. The weekend period and the start date day are excluded.

```
SELECT WORKDAYS_BETWEEN('01', '2014-01-20', '2014-01-17', 'FCTEST') "workdays" FROM DUMMY;
```

The following example returns the value 20 for work days between the two specified dates. **Result:** The system takes into account the weekends \(4th, 5th, 11th, 12th, 18th, 19th, 25th and 26th\) and public holidays \(1st and 6th\) and excludes them from the working period.

```
SELECT WORKDAYS_BETWEEN('01', '2014-01-01', '2014-01-31', 'FCTEST') "workdays" FROM DUMMY; 
```

The following example returns the values 30, 28, 25, and 20.

```
SET SCHEMA "SAPABC";
 CREATE ROW TABLE MY_DATES (FCID NVARCHAR(2), STARTDATE DAYDATE, ENDDATE DAYDATE);
 INSERT INTO MY_DATES VALUES ('01', '2014-01-01', '2014-02-14');
 INSERT INTO MY_DATES VALUES ('01', '2014-04-01', '2014-05-14');
 INSERT INTO MY_DATES VALUES ('01', '2014-07-01', '2014-08-05');
 INSERT INTO MY_DATES VALUES ('01', '2014-10-01', '2014-10-30');
 SELECT WORKDAYS_BETWEEN(FCID, STARTDATE, ENDDATE) "production duration" FROM MY_DATES;
```

**Related Information**  


[Data Types](../data-types-20a1569.md "A data type defines the characteristics of a data value. A special value of NULL is included in every data type to indicate the absence of a value.")

[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

[ALTER USER Statement \(Access Control\)](../012-SQL-Statements/alter-user-statement-access-control-20d3459.md "Modifies the database user.")

