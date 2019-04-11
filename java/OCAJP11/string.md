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
```
