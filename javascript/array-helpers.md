## reduce()
The __reduce()__ method executes a reducer function (that you provide) on each member of the array resulting in a single output value.
```
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// expected output: 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));
// expected output: 15
```
The reducer function takes four arguments:
1. Accumulator (acc)
2. Current Value (cur)
3. Current Index (idx)
4. Source Array (src)
Your reducer function's returned value is assigned to the accumulator, whose value is remembered across each iteration throughout the array and ultimately becomes the final, single resulting value.

### Syntax
`arr.reduce(callback[, initialValue])`

* callback: Function to execute on each element in the array, taking four arguments:
  * accumulator: The accumulator accumulates the callback's return values; it is the accumulated value previously returned in the last invocation of the callback, or initialValue, if supplied (see below).
  * currentValue: The current element being processed in the array.
  * currentIndex Optional: The index of the current element being processed in the array. Starts at index 0, if an initialValue is provided, and at index 1 otherwise.
  * array Optional: The array reduce() was called upon.
* initialValue Optional: Value to use as the first argument to the first call of the callback. If no initial value is supplied, the first element in the array will be used. Calling reduce() on an empty array without an initial value is an error.

Return the value that results from the reduction.


### Notes
* The first time the callback is called, __accumulator__ and __currentValue__ can be one of two values. If initialValue is provided in the call to __reduce()__, then accumulator will be equal to initialValue, and currentValue will be equal to the first value in the array. If no initialValue is provided, then accumulator will be equal to the first value in the array, and currentValue will be equal to the second.
* If initialValue is provided in the call to __reduce()__, then accumulator will be equal to initialValue, and currentValue will be equal to the first value in the array. If no initialValue is provided, then accumulator will be equal to the first value in the array, and currentValue will be equal to the second.
* If initialValue isn't provided, reduce() will execute the callback function starting at index 1, skipping the first index. If initialValue is provided, it will start at index 0.
* If the array is empty and no initialValue is provided, __TypeError__ will be thrown.
* It is usually safer to provide an initial value because there are three possible outputs without initialValue.
```
var maxCallback = ( acc, cur ) => Math.max( acc.x, cur.x );
var maxCallback2 = ( max, cur ) => Math.max( max, cur );

// reduce() without initialValue
[ { x: 22 }, { x: 42 } ].reduce( maxCallback ); // 42
[ { x: 22 }            ].reduce( maxCallback ); // { x: 22 }
[                      ].reduce( maxCallback ); // TypeError

// map/reduce; better solution, also works for empty or larger arrays
[ { x: 22 }, { x: 42 } ].map( el => el.x )
                        .reduce( maxCallback2, -Infinity );
```


## forEach()

The __forEach()__ method executes a provided function once for each array element.

```
const colors = ['red', 'blue', 'green'];

colors.forEach(function(color) {
  console.log(color);
});
```

### Syntax

```
arr.forEach(function callback(currentValue [, index [, array]]) {
    //your iterator
}[, thisArg]);
```

* callback: Function to execute on each element, taking three arguments:
  * currentValue: The current element being processed in the array. 
  * index Optional: The index of the current element being processed in the array.
  * array Optional: The array forEach() was called upon.
* thisArg Optional: Value to use as this when executing callback.

### Notes
* Always returns null
* forEach() does not mutate the array on which it is called (although callback, if invoked, may do so).
* Elements which are appended to the array after the call to forEach() begins will not be visited by callback.
* There is no way to stop or break a forEach() loop other than by throwing an exception.


## map()
The __map()__ method creates a new array with the results of calling a provided function on every element in the calling array.
```
var array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);
// expected output: Array [2, 8, 18, 32]
```

### Syntax
```
var new_array = arr.map(function callback(currentValue[, index[, array]]) {
    // Return element for new_array
}[, thisArg])
```
* callback:Function that produces an element of the new Array, taking three arguments:
  * currentValue: The current element being processed in the array.
  * index Optional: The index of the current element being processed in the array.
  * array Optional: The array map was called upon.
* thisArg Optional: Value to use as this when executing callback.

Return a new array with each element being the result of the callback function.

### Notes
* _callback_ is invoked only for indexes of the array which have assigned values, including _undefined_. It is not called for missing elements of the array (that is, indexes that have never been set, which have been deleted or which have never been assigned a value).
* Since map builds a new array, using it when you aren't using the returned array is an anti-pattern;
* map does not mutate the array on which it is called (although callback, if invoked, may do so).
* If a thisArg parameter is provided to map, it will be used as callback's this value, otherwise, the value undefined will be used.
* The range of elements processed by map is set before the first invocation of callback. 
* If the array which map was called upon is sparse, resulting array will also be sparse keeping same indices blank


## filter()
The filter() method creates a new array with all elements that pass the test implemented by the provided function.
```
var words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
```

### Syntax
`var newArray = arr.filter(callback(element[, index[, array]])[, thisArg])`

* callback: Function is a predicate, to test each element of the array. Return true to keep the element, false otherwise. It accepts three arguments:
  * element: The current element being processed in the array.
  * index Optional: The index of the current element being processed in the array.
  * array Optional: The array filter was called upon.
* thisArg Optional: Value to use as this when executing callback.

Return a new array with the elements that pass the test. If no elements pass the test, an empty array will be returned.

### Notes
* __callback__ is invoked only for indexes of the array which have assigned values; it is not invoked for indexes which have been deleted or which have never been assigned values.
* If a __thisArg__ parameter is provided to filter, it will be used as the callback's this value, otherwise, the value __undefined__ will be used as its this value.
* __filter()__ does not mutate the array on which it is called.
* The range of elements processed by filter() is set before the first invocation of callback. Elements which are appended to the array after the call to filter() begins will not be visited by callback.


## find()
The find() method returns the value of the first element in the array that satisfies the provided testing function. Otherwise undefined is returned.

```
var array1 = [5, 12, 8, 130, 44];

var found = array1.find(function(element) {
  return element > 10;
});

console.log(found);
// expected output: 12
```

### Syntax
`arr.find(callback[, thisArg])`

* callback: Function to execute on each value in the array, taking three arguments:
  * element: The current element being processed in the array.
  * index Optional: The index of the current element being processed in the array.
  * array Optional: The array find was called upon.
* thisArg Optional: Object to use as this when executing callback.

Returns the value of the first element in the array that satisfies the provided testing function; otherwise, undefined is returned.

### Notes
* If such an element is found, find immediately returns the value of that element. Otherwise, find returns undefined.
* __callback__ is invoked for every index of the array, not just those that have been assigned values (This may mean that it's less efficient for sparse arrays than other methods that only visit indexes that have been assigned a value).
* If a __thisArg__ parameter is provided to find, it will be used as the this for each invocation of the callback. If it is not provided, then undefined is used.


### Alternatives
* __findIndex()__ method, which returns the index of a found element in the array instead of its value.

## every()
The __every()__ method tests whether all elements in the array pass the test implemented by the provided function.

```
function isBelowThreshold(currentValue) {
  return currentValue < 40;
}

var array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));
// expected output: true
```
### Syntax
`arr.every(callback[, thisArg])`

* callback: Function to test for each element, taking three arguments:
  * element: The current element being processed in the array.
  * index Optional: The index of the current element being processed in the array.
  * array Optional: The array every was called upon.
* thisArg Optional: Value to use as this when executing callback

Returns __true__ if the callback function returns a truthy value for every array element; otherwise, __false__.

### Notes
* Executes the provided callback function once for each element present in the array until it finds one where callback returns a falsy value. If such an element is found, the every method immediately returns false.
* If a __thisArg__ parameter is provided to every, it will be used as callback's this value. Otherwise, the value _undefined_ will be used as its this value. 
* every does not mutate the array on which it is called.
* The range of elements processed by every is set before the first invocation of callback
* for an empty array, it returns true.

```
[12, 5, 8, 130, 44].every(x => x >= 10); // false
[12, 54, 18, 130, 44].every(x => x >= 10); // true
```

## some()
The some() method tests whether at least one element in the array passes the test implemented by the provided function.
```
var array = [1, 2, 3, 4, 5];

var even = function(element) {
  // checks whether an element is even
  return element % 2 === 0;
};

console.log(array.some(even));
// expected output: true

```
### Syntax
`arr.some(callback(element[, index[, array]])[, thisArg])`

* callback: Function to test for each element, taking three arguments:
  * element: The current element being processed in the array.
  * index Optional: The index of the current element being processed in the array.
  * array Optional: The array some() was called upon.
* thisArg Optional: Value to use as this when executing callback.

Returns true if the callback function returns a truthy value for any array element; otherwise, false.

### Notes
* If such an element is found, some() immediately returns true. Otherwise, some() returns false. 
* callback is invoked only for indexes of the array which have assigned values; it is not invoked for indexes which have been deleted or which have never been assigned values.
* If a thisArg parameter is provided to some(), it will be used as callbacks' this value. Otherwise, the value undefined will be used as its this value.
* some() does not mutate the array on which it is called.
* The range of elements processed by some() is set before the first invocation of callback.
