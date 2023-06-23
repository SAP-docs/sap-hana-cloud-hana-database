<!-- loio3ca8ac5cb49d401993b5dfcca925c22f -->

# SOUNDEX Function \(String\)

Converts alphabet characters into a sound code that represents their sound.



<a name="loio3ca8ac5cb49d401993b5dfcca925c22f__sql_function_soundex_1sql_function_soundex_syntax"/>

## Syntax

```
SOUNDEX(<string>)
```



## Syntax Elements


<dl>
<dt><b>

*<string\>*

</b></dt>
<dd>

Specifies the string to be converted into sound code.



</dd>
</dl>



<a name="loio3ca8ac5cb49d401993b5dfcca925c22f__sql_function_soundex_1sql_function_soundex_description"/>

## Description

Use the SOUNDEX function to find names that sound the same but are spelled differently.

SOUNDEX returns a code consisting of one letter and three numbers. The letter is the first letter of the word, and the numbers represent the next three consonants of the word, other than H, W, and Y, which are ignored. Vowels are also ignored, unless they are the first letter of the string. Double letters are counted as one letter. If necessary, zeroes are added at the end to ensure a four-character code.

The following characters are ignored:

-   Blank spaces
-   New lines
-   Form feeds
-   Carriage returns
-   Line feeds
-   Any of the following: ! " \# $ % & ' \( \) \* + , - . / : ; < = \> ? @ \[ \] ^ \_ \` \{ | \} ~



<a name="loio3ca8ac5cb49d401993b5dfcca925c22f__sql_function_char_1sql_function_char_examples"/>

## Example

The following fictitious example returns two identical codes, ***S530***, which represent the sound of each name:

```
SELECT SOUNDEX ('Smith'), SOUNDEX ('Smythe') FROM DUMMY;
```

This fictitious example searches MyTable.MyColumn for values that sound like Smith:

```
SELECT * FROM MyTable WHERE SOUNDEX(MyColumn) = SOUNDEX('SMITH');
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

