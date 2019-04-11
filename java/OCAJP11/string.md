# Creating and Manipulating Strings

```
String name = "Fluffy";
String name = new String("Fluffy");
```

## Concatentation

1. If both operands are numeric, + means numeric addition.  `System.out.println(1 + 2); // 3`
2. If either operand is a String, + means concatenation.  `System.out.println("a" + "b"); // ab`
3. The expression is evaluated left to right. 
```
System.out.println("a" + "b" + 3); // ab3
System.out.println(1 + 2 + "c"); // 3c

String s = "1"; // s holds "1"
s += "2"; // s currently holds "12"
s += 3; // s currently holds "123"
System.out.println(s); // 123

String s1 = "1";
String s2 = s1.concat("2");
s2.concat("3");
System.out.println(s2); // 12

```

## Immutability
Once a String object is created, it is not allowed to change. It cannot be made larger or
smaller, and you cannot change one of the characters inside it.

* Immutable only has a getter.
* Also, immutable classes in Java are fi nal, and subclasses can’t add mutable behavior.

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
        
