# Local variable type inference
You can replace the type in a local-variable declaration with the keyword __var__, and the compiler fills in the appropriate type from the variable initializer.
```
var userChannels = new HashMap<User, List<String>>();
var channels = lookupUserChannels("Tom");
```

## Cannot use local variable type inference:
* For fields and method signatures `public long process(var list) { }`
* Without explicit initialization `var x;`
* When Initialized to null `var x = null;`

### Polymorphic code doesn’t play nice with var.
```
class Car extends Vehicle {
}

class Bike extends Vehicle {
}

var x = new Car();  

x = new Bike(); // Compile error

```

## Type Inference with Non-Denotable Types

The var keyword also enables us to use anonymous classes more effectively and refer to types that would otherwise be impossible to describe.
```
Object productInfo = new Object() {
        String name = "Apple";
        int total = 30;
};
System.out.println( productInfo.name );  // Compile error
```

When you assign an anonymous class to a var typed local variable it infers the type of the anonymous class, rather than its parent.
```
var productInfo = new Object() {
        String name = "Apple";
        int total = 30;
};
System.out.println( productInfo.name );  // Compile error
```

### Using an anonymous class as a store for intermediate values. 

```
var products = List.of(
    new Product(10, 3, "Apple"),
    new Product(5, 2, "Banana"),
    new Product(17, 5, "Pear"));
    
var productInfos = products
    .stream()
    .map(product -> new Object() {
        String name = product.getName();
        int total = product.getStock() * product.getValue();
    })
    .collect(toList());
    
productInfos.forEach(prod -> System.out.println("name = " + prod.name + ", total = " + prod.total));

// This outputs:
// name = Apple, total = 30
// name = Banana, total = 10
// name = Pear, total = 85
```

## Local Variable Syntax for Lambda Parameters
As of Java 11 the below syntax is supported. This makes the usage of var uniform in both local variables and lambda parameters.
`(var s1, var s2) -> s1 + s2`

### We can use modifiers with __var__:
`(@Nonnull var s1, @Nullable var s2) -> s1 + s2`
__We cannot use such annotations without specifying the types.__

### Limitations
* Cannot use var for some parameters and skip for others `(var s1, s2) -> s1 + s2   // Error`   
* Cannot mix var with explicit types `(var s1, String s2) -> s1 + s2 // Error`
* Can skip the parentheses in single parameter `var s1 -> s1.toUpperCase() // Error`


