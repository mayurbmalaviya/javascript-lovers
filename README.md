# JavaScript Lovers

---

## Table of Contents

1. [Why for..in method is not best solution to iterate array?](#forin_drawback)
2. [Why for..in method is slower than other methods?](#forin_slower)
3. [Associative array in JavaScript](#associative_array)
4. [Why [] == [] returns false?](#array_comparison)

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
