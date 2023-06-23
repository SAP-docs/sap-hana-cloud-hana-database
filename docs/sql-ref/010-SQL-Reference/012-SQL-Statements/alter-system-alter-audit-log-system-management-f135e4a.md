<!-- loiof135e4a7883746f4b4b7c06b8605a589 -->

# ALTER SYSTEM ALTER AUDIT LOG \(System Management\)

Change the internal table of the audit log to use SAP HANA Native Storage Extension \(NSE\).



<a name="loiof135e4a7883746f4b4b7c06b8605a589__section_udc_q3t_nvb"/>

## Syntax

```
ALTER SYSTEM ALTER AUDIT LOG <load_unit>

```



<a name="loiof135e4a7883746f4b4b7c06b8605a589__section_vdc_q3t_nvb"/>

## Syntax Element


<dl>
<dt><b>

*<load\_unit\>*

</b></dt>
<dd>

Configures how NSE loads the audit log table into memory.

```
<load_unit> ::= [ {PAGE | DEFAULT } ] LOADABLE

```

For instances created or upgraded in QRC 4/2022 and later, by default, the audit log table is configured with the PAGE LOADABLE value. For instances created prior to QRC 4/2022, by default, the audit log table is configured with the DEFAULT LOADABLE value.



</dd>
</dl>



<a name="loiof135e4a7883746f4b4b7c06b8605a589__section_wdc_q3t_nvb"/>

## Description

When *<load\_unit\>* is configured to PAGE LOADABLE, SAP HANA NSE only loads into memory those pages of the audit log table that are relevant to the queries on audit log. When configured to DEFAULT LOADABLE, the entire audit log table is loaded into memory.

Execution of the statement is audited as a mandatory audit event.

To determine the current value for *<load\_unit\>*, execute:

```
SELECT SCHEMA_NAME, TABLE_NAME, LOAD_UNIT
   FROM SYS.TABLES WHERE SCHEMA_NAME = '_SYS_AUDIT' AND TABLE_NAME = 'CS_AUDIT_LOG_'
```



<a name="loiof135e4a7883746f4b4b7c06b8605a589__section_xdc_q3t_nvb"/>

## Privileges

Requires the AUDIT ADMIN system privilege.

**Related Information**  


[SAP HANA Native Storage Extension](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/4efaa94f8057425c8c7021da6fc2ddf5.html "SAP HANA native storage extension is a general-purpose, built-in warm data store in SAP HANA that lets you manage less-frequently accessed data without fully loading it into memory. It integrates disk-based or flash-drive based database technology with the SAP HANA in-memory database for an improved price-performance ratio.") :arrow_upper_right:

