# Variables

## Declare variables
When you declare a variable, you need to state the variable type along with giving it a
name

```
String s1;
int i1;
i2; // Compile error - missing type
```

### Identifier names 
* Case-sensitive
* Must begin with letter, or $ or _
* Subsequent characters may be numbers
* Cannot use any Java reserved keyword

```
3DPointClass // identifiers cannot begin with a number
hollywood@vine // @ is not a letter, digit, $ or _
*$coffee // * is not a letter, digit, $ or _
public // public is a reserved word 
```

## Initialize variables
```
String s1;
s1= "text";

String s1="text"
```

## Declare and initialize multiple variables
You can declare and initialize multiple variables in the same statement. 
```
boolean b1, b2;  // Valid
String s1 = "1", s2; // Valid, only s1 is initialized
double d1, double d2; // Compile error: must not repeat type in a single statement
int i1; int i2; // Valid. It's two statements.
int i3; i4; // Compile error: i4 is missing type
```

## Variable scope

* Local: defined within a method, including method parameters
* Instance: fields
* Class: static

### Default initial values
boolean | false 
byte, short, int, long | 0 
float, double | 0.0 
char | '\u0000' 
any object ref | null
