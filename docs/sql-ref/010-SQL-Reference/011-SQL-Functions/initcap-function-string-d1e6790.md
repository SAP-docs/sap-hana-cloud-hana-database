<!-- loiod1e67902534d426180459ae45a264667 -->

# INITCAP Function \(String\)

Converts the first character of each word in a specified string to uppercase and converts remaining characters to lowercase.



## Syntax

```
INITCAP(<inputString>)
```



## Syntax Elements


<dl>
<dt><b>

*<inputString\>*

</b></dt>
<dd>

Specifies the NVARCHAR string to be converted.

```
<inputString> ::= <string>
```



</dd>
</dl>



## Description

A word is delimited by any of the following characters:

-   Blank space

-   New line

-   Form feed

-   Carriage return

-   Line feed

-   Any of the following: `! " # $ % & ' ( ) * + , − . / : ; < = > ? @ [ \ ] ^ _ ` { | } ~`




## Example

The following query returns ***The Example One***:

```
SELECT INITCAP('the EXAMPLE one') FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

