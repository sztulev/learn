# Variables

## Declare variables
When you declare a variable, you need to state the variable type along with giving it a
name

```
String s1;
int i1;

i2; // Compile error: missing type
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

String s1="text"; 
```

### Default initial values
Type | Default value
--- | --- 
boolean | false 
byte, short, int, long | 0 
float, double | 0.0 
char | '\u0000' 
any object ref | null


## Declare and initialize multiple variables
You can declare and initialize multiple variables in the same statement. 
```
boolean b1, b2;  // Valid

String s1 = "1", s2; // Valid, only s1 is initialized

double d1, double d2; // Compile error: must not repeat type in a single statement

int i1; int i2; // Valid. It's two statements.

int i3; i4; // Compile error: i4 is missing type
```

## Literals

### Hexadecimal, Octal and Binary literals
```
int dec = 110; // no prefix --> decimal literal
int bin = 0b1101110; // '0b' prefix --> binary literal
int oct = 0156; // '0' prefix --> octal literal
int hex = 0x6E; // '0x' prefix --> hexadecimal literal
```

### Using underscore
You can use one or more underscores _ for separating groups of digits in a primitive
number literal to improve their readability.
```
byte color = 1_2_3;
short yearsAnnoDomini= 2_016;
int socialSecurtyNumber = 999_99_9999;
long creditCardNumber = 1234_5678_9012_3456L;
float piFourDecimals = 3.14_15F;
double piTenDecimals = 3.14_15_92_65_35;
```
This also works using prefixes for binary, octal and hexadecimal bases:
```
short binary= 0b0_1_0_1;
int octal = 07_7_7_7_7_7_7_7_0;
long hexBytes = 0xFF_EC_DE_5E;
```
__Placement of underscore is invalid:__
* At the beginning or end of a number (e.g. _123 or 123_ are not valid)
* Adjacent to a decimal point in a floating point literal (e.g. 1._23 or 1_.23 are not valid)
* Prior to an F or L suffix (e.g. 1.23_F or 9999999_L are not valid)
* In positions where a string of digits is expected (e.g. 0_xFFFF is not valid)


## Variable scope
* Local: defined within a method or in a block of code ({}), including method parameters
* Instance: fields
* Class: static

```
// two local variable
public void something(int i1) { 
 int i2 = 1; 
}

public void something(boolean b1) {
  int i1=1;
  if (b1) {
    int i2 = 2;
    System.out.println(i1);
    System.out.println(i2); 
  }
  System.out.println(i1);
  System.out.println(i2); // Compile error: variable out of scope
}
System.out.println(i1); // Compile error: variable out of scope
```

