<!-- loiod0b979ccbbd14377983f254e85241ff4 -->

# ALTER LIBRARY Statement \(SQLScript\)

Alters a SQLScript user-defined library.



<a name="loiod0b979ccbbd14377983f254e85241ff4__section_wtr_2lf_scb"/>

## Syntax

```
ALTER LIBRARY [ <schema_name>.]<library_name>
 [ LANGUAGE SQLSCRIPT ]
 AS BEGIN
   [ <sqlscript_user_defined_library_spec> ]
 END;
```



<a name="loiod0b979ccbbd14377983f254e85241ff4__section_hcs_2lf_scb"/>

## Syntax Elements


<dl>
<dt><b>

*<library\_name\>*

</b></dt>
<dd>

Specifies the name of the SQLScript user-defined library.



</dd>
</dl>


<dl>
<dt><b>

*<sqlscript\_user\_defined\_library\_spec\>*

</b></dt>
<dd>

Specifies the body of the new SQLScript user-defined library. See the *SAP HANA Cloud, SAP HANA Database SQLScript Reference* for the syntax allowed in a SQLScript language library.



</dd>
</dl>



<a name="loiod0b979ccbbd14377983f254e85241ff4__section_cks_2lf_scb"/>

## Description

Use this statement to alter a SQLScript user-defined library in an SAP HANA database.



<a name="loiod0b979ccbbd14377983f254e85241ff4__section_omw_k3b_2gb"/>

## Examples

The following example creates a table, creates a SQLScript user-defined library that operates on the table, and then alters the body of the library, replacing it to be BEGIN END:

```
CREATE TABLE data_table(col1 INT);
				
CREATE LIBRARY mylib AS BEGIN
   PUBLIC VARIABLE maxval CONSTANT INT = 100;
   PUBLIC PROCEDURE get_data(IN size INT, OUT result table(col1 INT)) AS 
      BEGIN
    	RESULT = SELECT TOP :size col1 FROM data_table;
	  END;
   END;
				
ALTER LIBRARY mylib AS BEGIN END;
```

**Related Information**  


[User-Defined Libraries](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/7cd14f1931404738a05c5e93e22564af.html "") :arrow_upper_right:

[SAP HANA Cloud, SAP HANA SQLScript Reference](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/28f2d64d4fab4e789ee0070be418419d.html "This reference describes how to use the SQL extension SAP HANA SQLScript to embed data-intensive application logic into SAP HANA.") :arrow_upper_right:

[CREATE LIBRARY Statement \(SQLScript\)](create-library-statement-sqlscript-62263ce.md "Creates a SQLScript user-defined library.")

[DROP LIBRARY Statement \(SQLScript\)](drop-library-statement-sqlscript-d416079.md "Drops a SQLScript user-defined library.")

[LIBRARIES System View](../../020-System-Views-Reference/021-System-Views/libraries-system-view-7e48a10.md "Provides information about available public language libraries.")

[LIBRARY\_MEMBERS System View](../../020-System-Views-Reference/021-System-Views/library-members-system-view-215c8db.md "Provides member information for SQLScript user-defined libraries.")

