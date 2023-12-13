<!-- loio209e0cde751910149114be53649a1fb7 -->

# SQL Notation Conventions

SQL syntax notation conventions used in this guide.



This reference uses syntax notation very similar to BNF \(Backus-Naur Form\), a notation technique used to define programming languages.



<a name="loio209e0cde751910149114be53649a1fb7___asql_notation_1sql_notation_symbols"/>

## Symbols


<table>
<tr>
<th valign="top">

Symbol

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

< \>

</td>
<td valign="top">

Angle brackets are used to surround the name of a syntactic element \(BNF nonterminal\) of the SQL language.

</td>
</tr>
<tr>
<td valign="top">

::=

</td>
<td valign="top">

The definition operator is used to provide definitions of the element appearing on the left side of the operator in a production rule.

</td>
</tr>
<tr>
<td valign="top">

\[ \]

</td>
<td valign="top">

Square brackets are used to indicate optional elements in a formula. Optional elements can be specified or omitted.

</td>
</tr>
<tr>
<td valign="top">

\{ \}

</td>
<td valign="top">

Braces group elements in a formula. Repetitive elements \(zero or more elements\) can be specified within brace symbols.

</td>
</tr>
<tr>
<td valign="top">

|

</td>
<td valign="top">

The alternative operator indicates that the portion of the formula following the bar is an alternative to the portion preceding it.

</td>
</tr>
<tr>
<td valign="top">

\[…\]

</td>
<td valign="top">

Ellipsis with square brackets around it indicates optional repetition of the preceding element or grouped elements. For example, if you can specify one or more columns for an option and must separate them by commas, this is expressed as <code><i class="varname">&lt;column_name&gt;</i> [,…]</code>. An example of grouped elements where a comma separator is not required looks like this: <code>{ <i class="varname">&lt;column_name&gt;</i> <i class="varname">&lt;data_type&gt;</i> } […]</code> 

</td>
</tr>
<tr>
<td valign="top">

!!

</td>
<td valign="top">

Introduces normal English text. This is used when the definition of a syntactic element is not expressed in BNF.

</td>
</tr>
</table>



<a name="loio209e0cde751910149114be53649a1fb7___asql_notation_1sql_notation_terms"/>

## Lowest Terms Representations

Throughout this manual, each syntax term is defined to one of the lowest term representations shown below.

```
<digit> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
  
<letter> ::= a | b | c | d | e | f | g | h | i | j | k | l | m | n | o | p | q | r | s | t | u | v | w | x | y | z 
           | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z
               
<any_character> ::= !!any character.
  
<comma> ::= ,
    
<dollar_sign> ::= $
  
<double_quotes> ::= "
  
<greater_than_sign> ::= >
    
<hash_symbol> ::= #
    
<left_bracket> ::= [
  
<left_curly_bracket> ::= {
   
<lower_than_sign> ::= <
  
<period> ::= .
    
<pipe_sign> ::= |
  
<right_bracket> ::= ]
  
<right_curly_bracket> ::= }
   
<sign> ::= + | -
    
<single_quote> ::= '
  
<underscore> ::= _
      
<apostrophe> ::= <single_quote>
      
<approximate_numeric_literal> ::= <mantissa>E<exponent>
    
<cesu8_restricted_characters> ::= <double_quote> | <dollar_sign> | <single_quote> | <sign> | <period> | <greater_than_sign> | <lower_than_sign> | <pipe_sign> | <left_bracket> | <right_bracket> | <left_curly_bracket> | <right_curly_bracket> | ( | ) | ! | % | * |  , |  / | : | ; |  = | ? | @ | \ | ^ |  ` 
      
<exact_numeric_literal> ::= <unsigned_integer>[<period>[<unsigned_integer>]]
                          | <period><unsigned_integer>
      
<exponent> ::= <signed_integer>
  
<hostname> ::= {<letter> | <digit>}[{ <letter> | <digit> | <period> | - } […] ]
    
<identifier> ::= <simple_identifier> | <special_identifier>
      
<mantissa> ::= <exact_numeric_literal> 
  
<numeric_literal> ::= <signed_numeric_literal> | <signed_integer>
   
<password> ::= { 
  <letter> [ { <letter_or_digit> | # | $ }[…] ]
  | <digit> [ <letter_or_digit> […] ]
  | <special_identifier> }
 
<port_number> ::= <unsigned_integer>
  
<schema_name> ::= <unicode_name>
              
<simple_identifier> ::= {<letter> | <underscore>} [{<letter> | <digit> | <underscore> | <hash_symbol> | <dollar_sign>}...]
    
<special_identifier> ::= <double_quotes><any_character>...<double_quotes>
   
<signed_integer> ::= [<sign>] <unsigned_integer>
  
<signed_numeric_literal> ::= [<sign>] <unsigned_numeric_literal>
    
<string_literal> ::= <single_quote>[<any_character>...]<single_quote>  
  
<unicode_name> ::= !! CESU-8 string excluding any characters listed in <cesu8_restricted_characters>
  
<unsigned_integer> ::= <digit>... 
  
<unsigned_numeric_literal> ::= <exact_numeric_literal> | <approximate_numeric_literal>
  
<user_name> ::= <unicode_name>


```

