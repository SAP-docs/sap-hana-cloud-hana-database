<!-- loio85ee0084ac014a63aa2680b384466f39 -->

# XMLEXTRACTVALUE Function \(Miscellaneous\)

Returns an XML value that matches the specified XPath query.



## Syntax

```
XMLEXTRACTVALUE(<XML_document>, <XPath_query> [,<NamespaceDeclarations>])
```



## Syntax Elements


<dl>
<dt><b>

*<XML\_document\>*

</b></dt>
<dd>

Specifies an XML document of type NVARCHAR or NCLOB \(or CLOB which is alias of NCLOB\).



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

Returns the text contents of the matching XML element. The return value is of type NVARCHAR or NCLOB depending on the type given for*<XML\_document\>*.

If an XML element is empty \(for example, `<name></name>`\), then an empty result is returned. If an XML element is not found, then the function returns an error.

This function is only supported for single elements of child XML nodes. For example, you can use XMLEXTRACTVALUE to query the `<name>` and `<age>` elements in the XML document below, as these are single elements of child nodes. However, you cannot query the `<parent>` or `<child>` elements of the document, as both of these elements contain multiple child nodes.

```
<parent>
 <child>
   <name>Tom<name>
   <age>18<age>
 <child>
<parent>
```



## Example

The following example extracts the value from the ***<name\>*** element from item 2 \(and returns ***Jar***\):

```
SELECT XMLEXTRACTVALUE(
   '<doc>
      <item><id>1</id><name>Box</name></item>
      <item><id>2</id><name>Jar</name></item>
   </doc>',
   '/doc/item[2]/name'
) FROM DUMMY;
```

The following example extracts the value from the ***<name\>*** element in item 2 \(and returns ***Jar***\):

```
SELECT XMLEXTRACTVALUE(         
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


[XMLEXTRACT Function \(Miscellaneous\)](xmlextract-function-miscellaneous-f1045c6.md "Returns an XML element that matches the specified XPath query.")

