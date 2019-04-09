# Use Strict 

## Enabling Strict mode

### Globally
```
'use strict'
const name = 'Flavio'
const hello = () => 'hey'
```

### For a function
```
function hello() {
  'use strict'
  return 'hey'
}
```

## Changes in Strict Mode

### Raises __ReferenceError__ when assigning a value to an undeclared variable.
```
'use strict'
variable = 'hey'
```
### Silent assignment errors are raised
```
const undefined = 1(() => {
  'use strict'
  undefined = 1; // TypeError: Cannot assign to read only property
})()
```
The same applies to Infinity, NaN, eval, arguments and more.

### Writing a read-only property of an object raises error

```
'use strict'
const car = {}
Object.defineProperty(car, 'color', { value: 'blue', writable: false })
car.color = 'test'; //TypeError: Cannot assign to read only property
```

#### And the same for getters
```
const car = {
  get color() {
    return 'blue'
  }
}
car.color = 'red'(
  //ok
  () => {
    'use strict'
    car.color = 'yellow' //TypeError: Cannot set property color of #<Object> which has only a getter
  }
)()
```

### Prevents extending a non-extensible object
```
const car = { color: 'blue' }
Object.preventExtensions(car)
car.model = 'Fiesta'(
  //ok
  () => {
    'use strict'
    car.owner = 'Flavio' //TypeError: Cannot add property owner, object is not extensible
  }
)()
```
### Prevents setting properties on primitive values
```
;(() => {
  'use strict'
  true.false = ''(
    //TypeError: Cannot create property 'false' on boolean 'true'
    1
  ).name =
    'xxx' //TypeError: Cannot create property 'name' on number '1'
  'test'.testing = true //TypeError: Cannot create property 'testing' on string 'test'
})()
```

### Prevents deleting a property that cannot be deleted

```
delete Object.prototype(
  //false
  () => {
    'use strict'
    delete Object.prototype //TypeError: Cannot delete property 'prototype' of function Object() { [native code] }
  }
)()
```

### Prevents using function arguments with the same name
```
(function(a, a, b) {
  'use strict'
  console.log(a, b)
})(1, 2, 3)
//Uncaught SyntaxError: Duplicate parameter name not allowed in this context
```
### Disables Octal Syntax
```
(() => {
  'use strict'
  console.log(010)
})()
//Uncaught SyntaxError: Octal literals are not allowed in strict mode.
```
By default, prepending a 0 to a number compatible with the octal numeric format makes it (sometimes confusingly) interpreted as an octal number.
You can still enable octal numbers in Strict Mode using the __0oXX__ syntax.

### Disables _with_ keyword
Strict Mode disables the with keyword, to remove some edge cases and allow more optimization at the compiler level.
