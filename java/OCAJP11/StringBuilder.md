# StringBuilder
The StringBuilder class creates a String without storing all those interim String values. Unlike the String class,
StringBuilder is not immutable.

```
StringBuilder a = new StringBuilder();
a.append("ab");
System.out.println(a); // ab
```

StringBuilder changes its own state and returns a reference to itself
```
StringBuilder a = new StringBuilder("a");
a.append("b"); 
System.out.println(a); // ab

StringBuilder abc = a.append("c"); 
System.out.println(abc); // abc
```

## Creating a StringBuilder
```
StringBuilder sb1 = new StringBuilder(); // empty char sequence
StringBuilder sb2 = new StringBuilder("animal"); // contains the specific value
StringBuilder sb3 = new StringBuilder(10); // reserve a certain number of slots for characters
```
__Size__ is the number of characters currently in the sequence, and __capacity__ is the number
of characters the sequence can currently hold. For _StringBuilder_, Java knows the size is likely to change as the object is used. When
_StringBuilder_ is constructed, it may start at the default capacity (which happens to be
16) or one of the programmer’s choosing.

## Methods

### charAt(), indexOf(), length(), and substring()
These four methods work exactly the same as in the String class.

### append()
it adds the parameter to the StringBuilder and returns a reference
to the current StringBuilder

### insert()
adds characters to the StringBuilder at the requested index and returns a reference to the current StringBuilder.
`StringBuilder insert(int offset, String str)`

```
StringBuilder sb = new StringBuilder("animals");
sb.insert(7, "-"); // sb = animals- : You can insert the end of sequence of characters
sb.insert(0, "-"); // sb = -animals-
sb.insert(4, "-"); // sb = -ani-mals
```

__Note:__ As we add and remove characters, their indexes change. 

### delete() and deleteCharAt()
removes characters from the sequence and returns a reference to the current StringBuilder.
```
StringBuilder delete(int start, int end)
StringBuilder deleteCharAt(int index)
```

```
StringBuilder sb = new StringBuilder("abcdef");
sb.delete(1, 3); // sb = adef
sb.deleteCharAt(5); // throws StringIndexOutOfBoundsException.
```

### reverse()
it reverses the characters in the sequences and returns a reference to the current StringBuilder
`StringBuilder reverse()`

### toString()
converts a StringBuilder into a String.
`String toString()`

## StringBuilder vs. StringBuffer
StringBuilder was added to Java in Java 5. If you come across older code, 
you will see StringBuffer used for this purpose. __StringBuffer does the same thing
but more slowly because it is thread safe.__

