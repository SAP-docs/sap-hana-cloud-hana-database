<!-- loiod4160799a5564fc0b901e499c29dc5b4 -->

# DROP LIBRARY Statement \(SQLScript\)

Drops a SQLScript user-defined library.



<a name="loiod4160799a5564fc0b901e499c29dc5b4__section_wtr_2lf_scb"/>

## Syntax

```
DROP LIBRARY [ <schema_name>.]<library_name>
```



<a name="loiod4160799a5564fc0b901e499c29dc5b4__section_hcs_2lf_scb"/>

## Syntax Elements


<dl>
<dt><b>

*<library\_name\>*

</b></dt>
<dd>

Specifies the name of the SQLScript user-defined library to drop.



</dd>
</dl>



<a name="loiod4160799a5564fc0b901e499c29dc5b4__section_cks_2lf_scb"/>

## Description

For more information on SQLScript user-defined libaries, see the *SAP HANA Cloud, SAP HANA Database SQLScript Reference*.



<a name="loiod4160799a5564fc0b901e499c29dc5b4__section_pbd_mlf_scb"/>

## Examples

The following example drops the mylib library;

```
DROP LIBRARY mylib;
```

**Related Information**  


[User-Defined Libraries](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/7cd14f1931404738a05c5e93e22564af.html "") :arrow_upper_right:

[SAP HANA Cloud, SAP HANA SQLScript Reference](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/28f2d64d4fab4e789ee0070be418419d.html "This reference describes how to use the SQL extension SAP HANA SQLScript to embed data-intensive application logic into SAP HANA.") :arrow_upper_right:

[CREATE LIBRARY Statement \(SQLScript\)](create-library-statement-sqlscript-62263ce.md "Creates a SQLScript user-defined library.")

[ALTER LIBRARY Statement \(SQLScript\)](alter-library-statement-sqlscript-d0b979c.md "Alters a SQLScript user-defined library.")

[LIBRARIES System View](../../020-System-Views-Reference/021-System-Views/libraries-system-view-7e48a10.md "Provides information about available public language libraries.")

[LIBRARY\_MEMBERS System View](../../020-System-Views-Reference/021-System-Views/library-members-system-view-215c8db.md "Provides member information for SQLScript user-defined libraries.")

