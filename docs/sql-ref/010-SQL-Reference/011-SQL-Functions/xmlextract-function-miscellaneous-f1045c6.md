<!-- loiof1045c62108c449a835adba32c279090 -->

# XMLEXTRACT Function \(Miscellaneous\)

Returns an XML element that matches the specified XPath query.



## Syntax

```
XMLEXTRACT(<XML_document>, <XPath_query> [,<NamespaceDeclarations>])
```



## Syntax Elements


<dl>
<dt><b>

*<XML\_document\>*

</b></dt>
<dd>

Specifies an XML document of type CLOB, NCLOB, NVARCHAR.



</dd><dt><b>

*<XPath\_query\>*

</b></dt>
<dd>

Specifies an XPath expression of type NVARCHAR.



</dd><dt><b>

*<NamespaceDeclarations\>*

</b></dt>
<dd>

Specifies a namespace declaration of type NVARCHAR.



</dd>
</dl>



## Description

Returns the matching XML element. The return value is of type NVARCHAR or CLOB/NCLOB depending on the type given for *<XML\_document\>*.

If an XML element is empty \(for example, `<name></name>`\), then an empty result is returned. If an XML element is not found, then the function returns an error.



## Example

The following statement returns the `<name>` element from item 2 \(the example returns ***<name\>Jar</name\>***\):

```
SELECT XMLEXTRACT(
   '<doc>
      <item><id>1</id><name>Box</name></item>
      <item><id>2</id><name>Jar</name></item>
   </doc>',
   '/doc/item[2]/name'
) FROM DUMMY;
```

The following statement returns ***<ns1:name\>Jar</ns1:name\>***:

```
SELECT XMLEXTRACT(                         
   '<doc xmlns:ns1="http://namespace1.sap.com" xmlns:ns2="http://namespace2.sap.com">
      <ns1:item><ns1:id>1</ns1:id><ns1:name>Box</ns1:name></ns1:item>
      <ns1:item><ns1:id>2</ns1:id><ns1:name>Jar</ns1:name></ns1:item>
      <ns2:item><ns2:id>3</ns2:id><ns2:name>Table</ns2:name></ns2:item>
   </doc>',
   '/doc/ns1:item[2]/ns1:name',
   'xmlns:ns1="http://namespace1.sap.com" xmlns:ns2="http://namespace2.sap.com"'
) FROM DUMMY;
```

**Related Information**  


[XMLEXTRACTVALUE Function \(Miscellaneous\)](xmlextractvalue-function-miscellaneous-85ee008.md "Returns an XML value that matches the specified XPath query.")

