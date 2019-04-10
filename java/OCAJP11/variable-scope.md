# Understand variable scope


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

