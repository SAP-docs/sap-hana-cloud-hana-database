<!-- loiod22c8391d2951014815a84e76cf66501 -->

# ADD\_WORKDAYS Function \(Datetime\)

Computes a date by adding a number of workdays to a starting date.



<a name="loiod22c8391d2951014815a84e76cf66501__sql_function_add_workdays_1sql_function_add_workdays_syntax"/>

## Syntax

```
ADD_WORKDAYS(
   <factory_calendar_id>, 
   <start_date>, 
   <workdays> 
   [, <source_schema> 
   [, <table_name_suffix>, 
   [, <client> ] ] ] )
```



<a name="loiod22c8391d2951014815a84e76cf66501__sql_function_workdays_between_1sql_function_add_workdays_syntax_elements"/>

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

Specifies the start date that the work days will be added to. You can use either a DATE type or a date format string \(for example '20140101' or '2014-01-01'\) for this parameter.

```
<start_date> ::= <string_literal> | <date>
```



</dd><dt><b>

*<workdays\>*

</b></dt>
<dd>

Specifies the number of working days to be added to the starting date.

```
<workdays> ::= <signed_integer>
```

When *<workdays\>* is positive, the resulting calculated date is the next working day after the period defined by the number of *<workdays\>*. When *<workdays\>* is negative, the resulting calculated date is the previous working day before the period defined by the number of *<workdays\>*.



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



<a name="loiod22c8391d2951014815a84e76cf66501__sql_function_add_workdays_1sql_function_add_workdays_returns"/>

## Return Type

DATE



<a name="loiod22c8391d2951014815a84e76cf66501__sql_function_add_workdays_1sql_function_add_workdays_description"/>

## Description

There are two different implementations for workday calculation in ABAP based systems like SAP S/4HANA:

-   The Factory Calendar that stores its data in a single table TFACS.
-   The Factory And Holiday Calendar that stores its data in multiple tables \(FHC\*\).

By default, the ADD\_WORKDAYS function assumes that the Factory Calendar is active. Once table FHC\_CONFIG \(or FHC\_CONFIG *<table\_suffix\>* where *<table\_suffix\>* is specified\) is available in the system and contains an entry with KEY\_FIELD = ‘MIGRATION\_COMPLETED' and VALUE = ‘X’ for the specified client, the ADD\_WORKDAYS function assumes that the newer Factory And Holiday Calendar is active.

The respective tables must be available in the SAP HANA database to use the ADD\_WORKDAYS function. In SAP BW, SAP CRM, and SAP ERP running on an SAP HANA database, these tables are located in the ABAP schema SAP*<SID\>*. For other SAP HANA database systems, these tables can be replicated from an SAP Business Suite system.

When the Factory Calendar is active, ADD\_WORKDAYS accesses the table TFACS \(or TFACS*<table\_suffix\>* if *<table\_suffix\>* is specified\). When the Factory And Holiday Calendar is active, ADD\_WORKDAYS accesses the following tables, which must be available in the system with *<table\_suffix\>* appended to their respective names if *<table\_suffix\>* is specified:

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



<a name="loiod22c8391d2951014815a84e76cf66501__sql_function_add_workdays_1sql_function_add_workdays_examples"/>

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

The following example returns the value 10.01.2014. From this result you can see that a single workday was added to the start date of the ninth, with the result being the tenth.

```
SELECT ADD_WORKDAYS('01', '2014-01-09', 1, 'FCTEST') "result date" FROM DUMMY;
```

The following example returns the value 09.01.2014. From this result you can see that the tenth was considered to be a working day, producing a final result of the ninth.

```
SELECT ADD_WORKDAYS('01', '2014-01-10', -1, 'FCTEST') "result date" FROM DUMMY;
```

The following example takes positive workday input and returns the value 20.01.2014, a result after a non-working weekend period. From this result you can see that a single workday was added to the start date of the 17th. This produced the resulting day of the 20th, which allowed for the non-working period of the weekend.

```
SELECT ADD_WORKDAYS('01', '2014-01-17', 1, 'FCTEST') "result date" FROM DUMMY;
```

The following example takes negative workday input and returns the value 17.01.2014, showing a result after a non-working weekend period. From this result you can see that the 20th was considered to be the working day, producing a result of the 17th. This result takes into account the non-working time of the weekend.

```
SELECT ADD_WORKDAYS('01', '2014-01-20', -1, 'FCTEST') "result date" FROM DUMMY;
```

The following complex example returns the value 27.01.2014. The statement above adds 16 working days to the start date of the first. The system takes into account the weekends \(4th, 5th, 11th, 12th, 18th and 19th\) and public holidays \(1st and 6th\) during the working period, which gives the last working day as the 24th. The system then returns the next possible working day after this, which is the 27th.

```
SELECT ADD_WORKDAYS('01', '2014-01-01', 16, 'FCTEST') "result date" FROM DUMMY;
```

The following example uses a table for input and returns the values 4.02.2014, 14.05.2014, 05.08.2014, and 30.10.2014.

```
CREATE SCHEMA SAPABC;
 SET SCHEMA "SAPABC";
 CREATE ROW TABLE MY_DATES (FCID NVARCHAR(2), STARTDATE DATE, DURATION INTEGER);
 INSERT INTO MY_DATES VALUES ('01', '2014-01-01', 30);
 INSERT INTO MY_DATES VALUES ('01', '2014-04-01', 28);
 INSERT INTO MY_DATES VALUES ('01', '2014-07-01', 25);
 INSERT INTO MY_DATES VALUES ('01', '2014-10-01', 20);
 
 SELECT ADD_WORKDAYS(FCID, STARTDATE, DURATION) "shipment date" FROM MY_DATES;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

[WORKDAYS\_BETWEEN Function \(Datetime\)](workdays-between-function-datetime-d232c25.md "Computes the number of workdays between a specified start date and a specified end date.")

[ALTER USER Statement \(Access Control\)](../012-SQL-Statements/alter-user-statement-access-control-20d3459.md "Modifies the database user.")

