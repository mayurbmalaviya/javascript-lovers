# JavaScript Lovers

---

## Table of Contents

1. [Why for..in method is not best solution to iterate array?](#forin_drawback)
2. [Why for..in method is slower than other methods?](#forin_slower)
3. [Associative array in JavaScript](#associative_array)
4. [Why [] == [] returns false?](#array_comparison)
5. [Explain about setTimeout with best example.](#setTimeout_explain)
6. [Difference between `null` and `undefined`](#diff_null_and_undefined)
7. [Difference between `REST` and `SPREAD` operators](#difference_rest_and_spread)

### Why for..in method is not best solution to iterate array?<a name="forin_drawback"></a>

---

```javascript
Array.prototype.testingVariable = 1;
Array.prototype.testingMethod = function () {
  console.log("testing method");
};

let arrayTestToResizeArray = [10, 20];

//Resize the array
arrayTestToResizeArray[5] = "Javascript Lovers";

//Array iterate using for loop
console.log(`index: value`);
for (let index = 0; index < arrayTestToResizeArray.length; index++) {
  // Iterate over numeric indexes from 0 to 5, as everyone expects.
  console.log(`${index}: ${arrayTestToResizeArray[index]}`);
}
/* Will display output like:
    index: value
    0 : 10
    1 : 20
    2 : undefined
    3 : undefined
    4 : undefined
    5 : Javascript Lovers
*/

//Similarly, array iterate using for..in method
console.log(`index: value`);
for (let index in arrayTestToResizeArray) {
  // Iterate over numeric indexes from 0 to 5, as everyone expects.
  console.log(`${index}: ${arrayTestToResizeArray[index]}`);
}
/* Will display output like:
    index: value
    0 : 10
    1 : 20
    5 : Javascript Lovers
    testingVariable: 1
    testingMethod: function() {
        console.log("testing method");
    }
*/
```

### Explanation about for_in and for loop difference:

---

- `for loop` counts from 0 to 6, and also ignores `Array.prototype.testingVariable` and `Array.prototype.testingMethod`. It shows array values.

- `for...in` lists only the `10, 20 and Javascript Lovers`, ignoring undefined array indexes, but adding `Array.prototype.testingVariable` and `Array.prototype.testingMethod`. It shows array property names.

### Note:

While using `for...in` loop we have to use `hasOwnProperty()` to check current object property.

### Conclusion:

All `objects` in JS are `associative`. A `JS Array` is an `object`, so yes, it’s `associative too`. If you want to iterate over an object's keys, use `for (var key in object)`. Hence, `For...in` loop is find the `elements` from the array as well as `property` from prototype because parent class is an object.

## Why for_in loop is slower than other methods?<a name="forin_slower"></a>

---

For..in method is slower because it `iterates an associative array or object properties`. In other words, in js everything is object. Even `array is also object` in js which inherits prototype of object. Hence, it will check all property of the object as well. Therefore, for..in loop is slower than other loops.

## Associative array in JavaScript<a name="associative_array"></a>

---

- Associative arrays are `basically objects` in JavaScript where `indexes` are replaced by `user-defined keys`. They do `not` have a `length property` like a normal array and cannot be traversed using a normal for loop.

### Syntax:

```javascript
let arr = { key1: "value1", key2: "value2" };
```

### Example:

```javascript
var arr = { "Company Name": ‘Javascript Lovers’, "ID": 123};
```

## Why [] == [] returns false?<a name="array_comparison"></a>

---

### Example:

```javascript
[] == []; // false
```

### Explanation:

- It returns false because all `objects` in JS are `associative`. A `JS Array` is an `object`, so yes, it’s `associative too`.

- [] creates a new array, so you are` comparing one array object with another array object`. It's `not the contents of the arrays` that is compared, the `object references are compared`. As a result, `they are not equal because it's not the same object instance.`

## Explain about setTimeout with best example.<a name="setTimeout_explain"></a>

---

### Example

```javascript
let x = true;
setTimeout(() => {
  x = false;
}, 0);
while (x) {
  console.log(`Hello`);
}
console.log(`End of the task execution`);
/* Will display output like:
    Hello for infinit times
*/
```

### Explanation

This code will iterate the loop for `infinite times` because for setTimeout it will `wait 0 seconds` to perform task execution. Meanwhile, call stack will `execute further loop` and it will `occupy the callstack` for infinite loop. Hence, it will `not execute setTimeout callback eventhough waiting is over` because callstack is occupied by while loop.

## Difference between `null` and `undefined`.<a name="diff_null_and_undefined"></a>

---

### Definition

`null` is an `assigned value`. It means nothing. `undefined` means a `variable has been declared` but `not defined yet`.

### Example

```javascript
var testVar;
alert(testVar); //shows undefined
alert(typeof testVar); //shows undefined
```

`null` is an `assignment value`. It can be assigned to a variable as a representation of no value:

```javascript
var testVar = null;
alert(testVar); //shows null
alert(typeof testVar); //shows object
```

From the preceding examples, it is clear that `undefined` and `null` are `two distinct types`: `undefined` is a type itself `(undefined)` while `null` is an `object.`

```javascript
null == undefined; // true
null === undefined; // false

typeof null; // object

typeof undefined; // undefined
```

## Difference between `REST` and `SPREAD` operators.<a name="difference_rest_and_spread"></a>

---

### Definition

JavaScript uses `three dots (...) for both the rest and spread operators`. But these `two operators` are `not the same`.

The `main difference` between rest and spread is that the `rest operator` puts `the rest of some specific user-supplied values into a JavaScript array`. But the `spread syntax expands iterables into individual elements`.

### Example

```javascript
function myBio(firstName, lastName, ...otherInfo) {
  return otherInfo;
}

// Invoke myBio function while passing five arguments to its parameters:
myBio("Javascript", "lovers", "Mayurkumar", "Malaviya", "Author");
```

In the snippet above, we used the `...otherInfo rest parameter` to put `"Mayurkumar", "Malaviya", and "Author" into an array.`

Now, consider this `example of a spread operator`:

```javascript
// Define a function with three parameters:
function myBio(firstName, lastName, company) {
  return `${firstName} ${lastName} runs by ${company}`;
}

// Use spread to expand an array’s items into individual arguments:
myBio(...["Javascript", "Lovers", "Mayurkumar"]);
```

In the snippet above, we used the `spread operator (...)` to spread `["Javascript", "Lovers", "Mayurkumar"]’s` content across `myBio()’s parameters.`

```javascript
const [a, b, ...{ pop, push }] = [1, 2];
console.log(a, b); // 1 2
console.log(pop, push); // [Function pop] [Function push]
```

In the snippet above, the rest property of `array destructuring assignment` can be another `array or object binding pattern`. This allows you to simultaneously `unpack the properties and indices of arrays`.

```javascript
const name = "Javascript lovers";
console.log([...name]); // ['J','a','v','a','s','c','r','i','p','t','','l','o','v','e','r','s';
```

In the snippet above, it will return and array with splited each characters.

```javascript
const myName = { firstName: "Javascript", lastName: "Lovers" };
const bio = { ...myName };

myName.firstName = "JS";

console.log(myName); // { firstName: "JS", lastName: "Lovers" }

console.log(bio); // { firstName: "Javascript", lastName: "Lovers" }
```

In the snippet above, myName’s update `did not reflect` in bio because we used the `spread operator on an object` that contains `primitive(old) values only`.

Note: A developer would call `myName a shallow object` because it contains only `primitive(old) items`.

`Here is one more example to understand rest operator with object reference:`

```javascript
const myName = {
  fullName: { firstName: "Javascript", lastName: "Lovers" },
};

const bio = { ...myName };

myName.fullName.firstName = "JS";

console.log(myName); // { fullName: { firstName: "JS", lastName: "Lovers" } }

console.log(bio); // { fullName: { firstName: "JS", lastName: "Lovers" } }
```

In the snippet above, myName’s update `is reflected` in bio because we used the spread operator on an object that contains a `non-primitive value.`

### `Note:`

- We call myName a `deep object` because it contains a non-primitive item.

- You do `shallow copy` when you create references while cloning one object into another. For instance, `...myName` produces a shallow copy of the `myName` object because whatever alteration you make in one will reflect in the other.

- You do `deep copy` when you clone objects without creating references. For instance, I could deep copy `myName` into `bio` by doing `const bio = JSON.parse(JSON.stringify(myName))`. By doing so, the computer will clone `myName` into `bio` without creating any reference.
