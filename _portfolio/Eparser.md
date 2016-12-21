---
title: "Eparser"
header:
  <!-- image: assets/images/profile.jpg -->
  teaser: assets/images/code.jpg
---
Translates a fictional language, E, to compile-ready C code, using Java. Extensive use of EBNF grammar and syntax.  

Scanning, parsing, symbol tables, and code generation.  

[Full specs here](/assets/docs/hw2.pdf)  

### BNF grammar specification:
```
program ::= block
block ::= declaration_list statement_list
declaration_list ::= {declaration}
statement_list ::= {statement}
declaration ::= ’@’ id { ’,’ id }
statement ::= assignment | print | do | if
print ::= ’!’ expr
assignment ::= ref_id ’=’ expr
ref_id ::= [ ’˜’ [ number ] ] id
do ::= ’<’ guarded_command ’>’
if ::= ’[’ guarded_command { ’|’ guarded_command } [ ’%’ block ] ’]’
guarded_command ::= expr ’:’ block
expr ::= term { addop term }
term ::= factor { multop factor }
factor ::= ’(’ expr ’)’ | ref_id | number
addop ::= ’+’ | ’-’
multop ::= ’ * ’ | ’/’
```

### comparison() function, equivalent to < and > operators:
```java
private void comparison()
  { //checks whether the token recieved is less than or greater than
    //checks for which two values are being compared
    
    ref_id(); //first part of compare
    
    if (is(TK.LESS)) //token is less than
    {
     System.out.print(" < ");
     mustbe(TK.LESS);
     ref_id(); //string that is second part of compare
     System.out.print("; ");
     //System.out.print(firstid + "_" + savedScope + "++");
    }
    
    else if (is(TK.GREATER)) //token is greater than
    {
     System.out.print(" > "); 
     mustbe(TK.GREATER);
     ref_id(); //string that is second part of compare
     System.out.print("; ");
    }
    else //invalid token recieved - throws parse error
    {
      System.out.println();
      parse_error("Error: nonvalid forloop declaration comparison!");
      System.exit(1); //exits program
    }
  }
```
Full source available on request.