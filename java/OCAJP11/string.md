# Creating and Manipulating Strings

```
String name = "Fluffy";
String name = new String("Fluffy");
```
## Immutability
Once a String object is created, it is not allowed to change. It cannot be made larger or
smaller, and you cannot change one of the characters inside it.

* An Immutable class has no setter methods.
* Also, immutable classes are final, and subclasses can’t add mutable behavior.

## String Pools
Java realizes that many strings repeat in the program and solves this issue by reusing common ones. The 
string pool, also known as the intern pool, is a location in the Java virtual machine (JVM)
that collects all these strings.
```
String s1 = "Fluffy";
String s2 = "Fluffy";
String s3 = new String("Fluffy");

System.out.println(s1==s2); // true
System.out.println(s1==s3); // false
```

__The string pool contains literal values that appear in your program.__  

```
String s1 = "ab";
var s4 = new Object(){
    String a = "a", b="b";
    public String toString() {
        return a+b;
    }
};

System.out.println(s1.equals(s4.toString())); // true
System.out.println(s1==s4.toString());  // false
```

For example, _s1_ is a literal and therefore goes into the string pool. _s4.toString()_ is a string
but not a literal, so it does not go into the string pool. 
Note that calling _toString()_ on a String will return the same object.
```
String s1 = "ab";
String s2 = "ab";
String s3 = new String("ab");
System.out.println(s1==s2.toString()); // true
System.out.println(s1==s3.toString()); // false
```

## Concatentation
the + operator can be used in two ways within the same line of code

1. If both operands are numeric, + means numeric addition.  `System.out.println(1 + 2); // 3`
2. If either operand is a String, + means concatenation.  `System.out.println("a" + "b"); // ab`
3. The expression is evaluated left to right. 
```
System.out.println("a" + "b" + 3); // ab3
System.out.println("a" + 1 + 2);   // a12
System.out.println(1 + 2 + "c");   // 3c

String s = "1"; // s holds "1"
s += "2"; // s currently holds "12"
s += 3; // s currently holds "123"
System.out.println(s); // 123

String s1 = "1";
String s2 = s1.concat("2");
s2.concat("3");
System.out.println(s2); // 12

```

## Important String Methods

### int length()
returns the number of characters in the String

### char charAt(int index)
queries the character is at a specific index
```
String string = "animals";
System.out.println(string.charAt(0)); // a
System.out.println(string.charAt(6)); // s
System.out.println(string.charAt(7)); // java.lang.StringIndexOutOfBoundsException: String index out of range: 7
```
### indexOf()
finds the first index that matches the desired value. __It returns –1 when no match is found.__
```
int indexOf(char ch)
int indexOf(char ch, index fromIndex)
int indexOf(String str)
int indexOf(String str, index fromIndex)
```
### substring()
returns parts of the string. The first parameter is the index to start with for the returned string.
```
int substring(int beginIndex)
int substring(int beginIndex, int endIndex)  // endIndex not included => allowed to be 1 past the end of the sequence
```

```
String string = "animals";
System.out.println(string.substring(3, 3)); // empty string
System.out.println(string.substring(3, 2)); // throws exception
System.out.println(string.substring(3, 8)); // throws exception
```
### toLowerCase() and toUpperCase()
```
String toLowerCase(String str)
String toUpperCase(String str)
```
### equals() and equalsIgnoreCase()
checks whether two String objects contain exactly the same characters in the same order.
```
boolean equals(String str)
boolean equalsIgnoreCase(String str)
```
### startsWith() and endsWith()
look at whether the provided value matches part of the String. case-sensitive
```
boolean startsWith(String prefix)
boolean endsWith(String suffix)
```
### contains()
case-sensitive search for matches in the String
```
boolean contains(String str)
```
### replace()
Does a simple search and replace on the string.
```
String replace(char oldChar, char newChar)
String replace(CharSequence oldChar, CharSequence newChar)
```
### trim()
removes whitespace from the beginning and end of a String.
`public String trim()`

## Method chaining
```
String result = "AniMaL ".trim().toLowerCase().replace('a', 'A');
System.out.println(result); // "Animal"
```


