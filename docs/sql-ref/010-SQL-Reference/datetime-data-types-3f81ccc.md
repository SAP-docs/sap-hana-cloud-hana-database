<!-- loio3f81ccc7e35d44cbbc595c7d552c202a -->

# Datetime Data Types

Datetime data types are used to store date and time information.




<dl>
<dt><b>

DATE

</b></dt>
<dd>

The DATE data type consists of year, month, and day information to represent a date value. The default format for the DATE data type is YYYY-MM-DD. YYYY represents the year, MM represents the month, and DD represents the day. The range of the date value is between 0001-01-01 and 9999-12-31.

DATE is a synonym for DAYDATE.



</dd><dt><b>

TIME

</b></dt>
<dd>

The TIME data type consists of hour, minute, and second information to represent a time value. The default format for the TIME data type is HH24:MI:SS. HH24 represents the hour from 0 to 24, MI represents the minute from 0 to 59, and SS represents the second from 0 to 59.



</dd><dt><b>

SECONDDATE

</b></dt>
<dd>

The SECONDDATE data type consists of year, month, day, hour, minute and second information to represent a date with a time value. The default format for the SECONDDATE data type is YYYY-MM-DD HH24:MI:SS. YYYY represents the year, MM represents the month, DD represents the day, HH24 represents hours, MI represents minutes, and SS represents seconds. The range of the date value is between 0001-01-01 00:00:01 and 9999-12-31 24:00:00.



</dd><dt><b>

TIMESTAMP

</b></dt>
<dd>

The TIMESTAMP data type consists of date and time information. Its default format is YYYY-MM-DD HH24:MI:SS.FF7. FF*<n\>* represents the fractional seconds where *<n\>* indicates the number of digits in fractional part. The range of the time stamp value is between 0001-01-01 00:00:00.0000000 and 9999-12-31 23:59:59.9999999. LONGDATE is a synonym of TIMESTAMP.



</dd>
</dl>

The EMPTY value refers to the lowest possible value of each datetime type and ensures compatibility with ABAP.



<a name="loio3f81ccc7e35d44cbbc595c7d552c202a__section_pnk_5rg_qcb"/>

## Datetime Session Variables

The following datetime session variables can be used to override the system default datetime formats for the session. Use the SET statements to set session variables.


<dl>
<dt><b>

DATE\_FORMAT

</b></dt>
<dd>

Specifies the default DATE format to apply for the session.



</dd><dt><b>

TIME\_FORMAT

</b></dt>
<dd>

Specifies the default TIME format to apply for the session.



</dd><dt><b>

SECONDDATE\_FORMAT

</b></dt>
<dd>

Specifies the default SECONDDATE format to apply for the session.



</dd><dt><b>

TIMESTAMP\_FORMAT

</b></dt>
<dd>

Specifies the default TIMESTAMP format to apply for the session.



</dd>
</dl>

When setting the TIMESTAMP\_FORMAT session variables, if you do not want to lose decimal point seconds when converting values, then specify SS.FF7 as the format for seconds instead of SS.

**Example of how setting the session variable affects a default format:**:

```
CREATE TABLE T1(A TIMESTAMP);
INSERT INTO T1 VALUES ('2018/01/02 10:00:00'); 	--> OK
INSERT INTO T1 VALUES ('02/01/2018 10:00:00'); 	--> ERROR
SELECT TO_VARCHAR(A) FROM T1; 				  --> 2018-01-02 10:00:00.0000000

SET 'TIMESTAMP_FORMAT' = 'DD/MM/YYYY HH:MI:SS';

CREATE TABLE T2(A TIMESTAMP);
INSERT INTO T2 VALUES ('2018/01/02 10:00:00'); 	--> ERROR
INSERT INTO T2 VALUES ('02/01/2018 10:00:00'); 	--> OK

SELECT TO_VARCHAR(A) FROM T2; 	--> 02/01/2018 10:00:00 
```



## Date Formats

The following datetime formats can be used when parsing a string into a DATETIME type and converting a DATETIME type value into a string value. The format for TIMESTAMP is the combination of DATE and TIME with additional support for fractional seconds. An empty date \(0000-00-00\) is a special value in SAP HANA. Even though an empty date looks like a NULL or unknown value, it is not. For example, the empty date can be represented as `''`, which behaves like an empty string. It also satisfies a IS NOT NULL predicate. Use the following statements to test the behavior of the empty date value:

```
CREATE ROW TABLE T (A INT, B DATE, C DATE);
INSERT INTO T VALUES (1, '', '0001-01-01');
INSERT INTO T VALUES (2, '0000-00-00', '0001-01-01');
INSERT INTO T VALUES (3, '0000-00-00', '0001-01-01');
INSERT INTO T VALUES (4, '0001-01-01', '0001-01-01');
INSERT INTO T VALUES (5, NULL, '0001-01-01');

SELECT * FROM T WHERE B = '00000000';
SELECT * FROM T WHERE B = '';
SELECT * FROM T WHERE B IS NOT NULL;
SELECT * FROM T;
SELECT DAYS_BETWEEN(B, C) FROM T;
```

**Supported Formats for DATE**


<table>
<tr>
<th valign="top">

Format



</th>
<th valign="top">

Description



</th>
<th valign="top">

Examples



</th>
</tr>
<tr>
<td valign="top">

YYYY-MM-DD



</td>
<td valign="top">

Default format.



</td>
<td valign="top">

```
INSERT INTO my_tbl VALUES ('1957-06-13'); 
```



</td>
</tr>
<tr>
<td valign="top">

YYYY/MM/DD

YYYY/MM-DD

YYYY-MM/DD



</td>
<td valign="top">

YYYY is from 0001 to 9999, MM is from 1 to 12, and DD is from 1 to 31. If year has less than four digits, month has less than two digits, or day has less than two digits, then values are padded by one or more zeros. For example, a two-digit year like 45 is saved as year 0045, while a one digit month like 9 is saved as 09, and a one digit day like 2 is saved as 02.



</td>
<td valign="top">

```
INSERT INTO my_tbl VALUES ('1957-06-13');
```

```
INSERT INTO my_tbl VALUES ('1957/06/13');
```

```
INSERT INTO my_tbl VALUES ('1957/06-13');
```

```
INSERT INTO my_tbl VALUES ('1957-06/13');
```



</td>
</tr>
<tr>
<td valign="top">

YYYYMMDD



</td>
<td valign="top">

The ABAP Data Type, DATES format.



</td>
<td valign="top">

```
INSERT INTO my_tbl VALUES ('19570613');
```



</td>
</tr>
<tr>
<td valign="top">

MON



</td>
<td valign="top">

The abbreviated name of month. For example, JAN. or DEC..



</td>
<td valign="top">

```
INSERT INTO my_tbl VALUES (TO_DATE('2040-Jan-10', 'YYYY-MON-DD'));
```

```
INSERT INTO my_tbl VALUES (TO_DATE('Jan-10', 'MON-DD'));
```



</td>
</tr>
<tr>
<td valign="top">

MONTH



</td>
<td valign="top">

The name of month. For example, JANUARY - DECEMBER.



</td>
<td valign="top">

```
INSERT INTO my_tbl VALUES (TO_DATE('2040-January-10', 'YYYY-MONTH-DD'));
```

```
INSERT INTO my_tbl VALUES (TO_DATE('January-10', 'MONTH-DD'));
```



</td>
</tr>
<tr>
<td valign="top">

RM



</td>
<td valign="top">

The Roman numeral month \(I-XII; JAN = I\).



</td>
<td valign="top">

```
INSERT INTO my_tbl VALUES (TO_DATE('2040-I-10', 'YYYY-RM-DD'));
```

```
INSERT INTO my_tbl VALUES (TO_DATE('I-10', 'RM-DD'));
```



</td>
</tr>
<tr>
<td valign="top">

DDD



</td>
<td valign="top">

The day of the year \(1-366\).



</td>
<td valign="top">

```
INSERT INTO my_tbl VALUES (TO_DATE('204', 'DDD'));
```

```
INSERT INTO my_tbl VALUES (TO_DATE('2001-204','YYYY-DDD'));
```



</td>
</tr>
</table>



## Time Formats

**Supported formats for TIME**


<table>
<tr>
<th valign="top">

Format



</th>
<th valign="top">

Description



</th>
<th valign="top">

Examples



</th>
</tr>
<tr>
<td valign="top">

HH24:MI:SS



</td>
<td valign="top">

The default format.



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

HH:MI\[:SS\]\[AM|PM\]

HH12:MI\[:SS\]\[AM|PM\]

HH24:MI\[:SS\]



</td>
<td valign="top">

HH is from 0 to 23. MI is from 0 to 59. SS is from 0 to 59.

If a one digit hour, minute, or second is specified, then 0 is also inserted into the value. For example, 9:9:9 is saved as 09:09:09.

HH12 indicates a 12 hour clock. HH24 indicates a 24 hour clock.

Specify AM or PM as a suffix to indicate that the time value is before or after midday.



</td>
<td valign="top">

```
INSERT INTO my_tbl VALUES ('23:59:59');
```

```
INSERT INTO my_tbl VALUES ('3:47:39 AM');
```

```
INSERT INTO my_tbl VALUES ('9:9:9 AM');
```

```
INSERT INTO my_tbl VALUES (TO_TIME('11:59:59','HH12:MI:SS');
```



</td>
</tr>
<tr>
<td valign="top">

SSSSS



</td>
<td valign="top">

The seconds past midnight \(0-86399\).



</td>
<td valign="top">

```
INSERT INTO my_tbl VALUES (TO_TIME('12345', 'SSSSS'));
```



</td>
</tr>
</table>



## Timestamp Formats

**Supported formats for TIMESTAMP**


<table>
<tr>
<th valign="top">

Format



</th>
<th valign="top">

Description



</th>
<th valign="top">

Examples



</th>
</tr>
<tr>
<td valign="top">

YYYY-MM-DD HH24:MI:SS.FF7



</td>
<td valign="top">

The default format.



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

FF \[1..7\]



</td>
<td valign="top">

Fractional seconds have the range of 1 to 7 after the FF parameter to specify the number of digits in the fractional second portion of the datetime value returned. If a digit is not specified, then an error is returned.



</td>
<td valign="top">

```
INSERT INTO my_tbl VALUES (TO_TIMESTAMP('2011-05-11 12:59.999','YYYY-MM-DD HH:MI:SS.FF'));
```



</td>
</tr>
</table>



## Additional Formats for DATETIME

The following additional formats for DATETIME are supported.

While all of the formats below can be converted to strings \(TO\_VARCHAR function\), conversion from string into D, DAY, DY, Q, W, and WW formats \(for example, using TO\_DATE and TO\_TIMESTAMP functions\) is not supported.


<table>
<tr>
<th valign="top">

Format



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

D



</td>
<td valign="top">

The day of the week \(1-7\).



</td>
</tr>
<tr>
<td valign="top">

DAY



</td>
<td valign="top">

The name of the day \(MONDAY - SUNDAY\).



</td>
</tr>
<tr>
<td valign="top">

DY



</td>
<td valign="top">

The abbreviated name of the day \(MON - SUN\).



</td>
</tr>
<tr>
<td valign="top">

MON



</td>
<td valign="top">

The abbreviated month name \(JAN - DEC\).



</td>
</tr>
<tr>
<td valign="top">

MONTH



</td>
<td valign="top">

The full month name \(JANUARY - DECEMBER\).



</td>
</tr>
<tr>
<td valign="top">

RM



</td>
<td valign="top">

The Roman numeral month \(I - XII; I is for January\).



</td>
</tr>
<tr>
<td valign="top">

Q



</td>
<td valign="top">

The quarter of the year \(1, 2, 3, 4\).



</td>
</tr>
<tr>
<td valign="top">

W



</td>
<td valign="top">

The week of the month \(1-6\).



</td>
</tr>
<tr>
<td valign="top">

WW



</td>
<td valign="top">

The week of the year \(1-54\).



</td>
</tr>
</table>

**Related Information**  


[SET \[SESSION\] Statement \(Session Management\)](012-SQL-Statements/set-session-statement-session-management-20fd82b.md "Sets a session variable for the current session.")

[M\_SESSION\_CONTEXT System View](../020-System-Views-Reference/022-Monitoring-Views/m-session-context-system-view-20c50b7.md "Displays the session variables set for each connection.")

[Session Variables](session-variables-a16678c.md " 		 		 		 		 		 		 	")

