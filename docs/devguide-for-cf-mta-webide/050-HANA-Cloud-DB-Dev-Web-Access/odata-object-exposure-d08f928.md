<!-- loiod08f928ac047443e8c2b0a7070ac1d0b -->

# OData Object Exposure

In the examples provided to illustrate object exposure, the following definition of a table applies:

Table definition`sample.odata:table.hdbtable`

```
COLUMN TABLE "sample.odata::table" (
	"ID" INTEGER,
	"Text" NVARCHAR(1000),
	"Time" TIMESTAMP,
	PRIMARY KEY ("ID")
);
```



<a name="loiod08f928ac047443e8c2b0a7070ac1d0b__section_N10072_N1000E_N10001"/>

## Database Objects

Similar to the exposure of an object by using the repository design-time name is the exposure by the database name:

Service definition `sample.odata:db.xsodata`

```
 service { 
	"sample.odata::table" as "MyTable";
 }
```

The service exposes the same table by using the database catalog name of the object and the name of the schema where the table is created in.

