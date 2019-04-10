# Local variable type inference
You can replace the type in a local-variable declaration with the keyword __var__, and the compiler fills in the appropriate type from the variable initializer.
```
var userChannels = new HashMap<User, List<String>>();
var channels = lookupUserChannels("Tom");
```

### Cannot use local variable type inference:
* For fields and method signatures `public long process(var list) { }`
* Without explicit initialization `var x;`
* When Initialized to null `var x = null;`

### Type Inference with Non-Denotable Types

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
