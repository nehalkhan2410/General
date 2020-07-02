_[General](../README.md) > [JavaScript](./main.md) > [Array Methods](./ArrayMethods.md)_

# **JavaScript**

## **Array Methods**

In a conventional way to perform some operations over an array, you iterate each item to perform the needed computation.

In the example, we have a few items in the array and, the task is to perform some calculation on the array elements to get the results. In a normal way, we iterate over the array using a conventional for loop and perform some calculation with each item of the array. The same calculation can be done in a single line without writing a for-loop.

```javascript
const orders = [500, 30, 99, 15, 223];

// Conventional way of doing things 💩
let total = 0;
let withTax = [];
let highValue = [];

for (let i = 0; i < orders.length; i++) {
  total += orders[i];

  withTax.push(orders[i] * 1.1);

  if (orders[i] > 100) {
    highValue.push(orders[i]);
  }
}

console.log(total, withTax, highValue);

// A cleaner and easy way to do things ✅
const _total = orders.reduce((acc, cur) => acc + cur);

const _withTax = orders.map((v) => v * 1.1);

const _highValue = orders.filter((v) => v > 100);

console.log(_total, _withTax, _highValue);
```

_Output:_

```javascript
867 [550, 33, 108.9, 16.5, 245.3][500, 223];
867 [550, 33, 108.9, 16.5, 245.3][500, 223];
```

### **Now let's take a look at a few built-in array methods that can do most of the tasks in a better and much cleaner way.**

We would be using the following two arrays throughout our examples.

```javascript
const items = [
  { name: "Bike", price: 100 },
  { name: "TV", price: 200 },
  { name: "Album", price: 10 },
  { name: "Book", price: 5 },
  { name: "Phone", price: 500 },
  { name: "Computer", price: 1000 },
  { name: "Keyboard", price: 25 },
];

const faces = ["😀", "😃", "😄", "💩", "😁", "😆", "😅"];
```

`filter` method iterates over each element in the array and takes that item as a parameter and checks a given condition to return a boolean value based on the result of that condition. If it is true, then that particular item gets filtered out into the resulting array.

**In the example, we filter out the items whose price is less than or equal to 100.**

```javascript
const filteredItems = items.filter((item) => {
  return item.price <= 100;
});
console.log(filteredItems);
```

_Output:_

```javascript
[
  { name: "Bike", price: 100 },
  { name: "Album", price: 10 },
  { name: "Book", price: 5 },
  { name: "Keyboard", price: 25 },
]
```

**In the example, we filter out the item which is an odd one out.**

```javascript
const feces = faces.filter((v) => v === "💩");
console.log(feces);
```

_Output:_

```javascript
["💩"]
```

`map` method iterates over each element in the array and takes that item as a parameter and performs some given action on it and returns it.

**In the example, we return the name from the object to be part of the resulting array.**

```javascript
const itemNames = items.map((item) => {
  return item.name;
});
console.log(itemNames);
```

_Output:_

```javascript
["Bike", "TV", "Album", "Book", "Phone", "Computer", "Keyboard"]
```

**In the example, we replace each item in the array with a new value to be part of the resulting array.**

```javascript
const feces = ["💩"];
const cleaned = feces.map((v) => "⛅");
console.log(cleaned);
```

_Output:_

```javascript
["⛅"]
```

`find` method iterates over each element in the array and takes that item as a parameter and checks a given condition to return a boolean value as output based on the result of that condition.

**In the example, we check for a condition on each item and return a boolean output.**

```javascript
const foundItem = items.find((item) => {
  return item.name === "Book";
});
console.log(foundItem);
```

_Output:_

```javascript
{ name: 'Book', price: 5 }
```

`forEach` is a shorter way to iterate over an array and perform some action with each element.

**In the example, we iterate over the elements of the array and print the name from each item.**

```javascript
items.forEach((item) => {
  console.log(item.name);
});
```

_Output:_

```javascript
Bike
TV
Album
Book
Phone
Computer
Keyboard
```

`some` method iterates over each element in the array and takes that item as a parameter and returns true as output if the given condition is satisfied at least one time.

**In the example, we iterate over the elements and return true if the condition is satisfied at least once.**

```javascript
const hasInexpensiveItems = items.some((item) => {
  return item.price <= 100;
});
console.log(hasInexpensiveItems);
```

_Output:_

```javascript
true
```

**In the example, we iterate over the elements and return true if the item matches with given character at least once.**

```javascript
const isPoopy = faces.some((v) => v === "💩");
console.log(isPoopy);
```

_Output:_

```javascript
true
```

`every` method iterates over each element in the array and takes that item as a parameter and returns true as output if the given condition is satisfied for every item.

**In the example, we iterate over the elements and return true if the condition is satisfied for every item.**

```javascript
const _hasInexpensiveItems = items.every((item) => {
  return item.price <= 1000;
});
console.log(_hasInexpensiveItems);
```

_Output:_

```javascript
true
```

**In the example, we iterate over the elements and return true if the character of the item is greater than the given character every time.**

```javascript
const isEmoji = aces.every((v) => v > "ÿ");
console.log(isEmoji);
```

_Output:_

```javascript
true
```

`reduce` method iterates over each element in the array and takes two parameters, first a function with an accumulator value and the item itself as two parameters, and initial value for the accumulator as the second parameter. And perform some calculation on each item to change the accumulated value for each iteration to return the desired output.

**In the example, we iterate over each item to add up the price to the initial value of the accumulator.**

```javascript
const total = items.reduce((currentTotal, item) => {
  return item.price + currentTotal;
}, 0); // 0 is the initial value for the accumulator
console.log(total);
```

_Output:_

```javascript
1840
```

**In the example, we iterate over each item to increment the initial value of the accumulator by one, if the current one matches with the given character.**

```javascript
const pooCount = faces.reduce((acc, cur) => {
  return acc + (cur === "💩" ? 1 : 0);
}, 0); // 0 is the initial value for the accumulator

console.log(pooCount);
```

_Output:_

```javascript
1
```

`includes` method checks if the given value is present in the array or not to return a boolean output.

**In the example, we iterate over each item to check if the given element is included or not**

```javascript
const numbers = [1, 2, 3, 4, 5];

const includesTwo = numbers.includes(2);
console.log(includesTwo);
```

_Output:_

```javascript
true
```

`sort` method sorts the given array in ascending order by default or according to the comaprator function that is provided.

**In the example, we iterate over each item to sort it in ascending order**

```javascript
const a = ["dom", "apple", "bottle"];
const sorted = a.sort();

console.log(sorted);
```

_Output:_

```javascript
["apple", "bottle", "dom"]
```

**In the example, we iterate over each item to sort it according to the comparator function's logic**

We pass two elements at a time as parameters to the comparator function and they are sorted based upon the returned value of the comparison i.e.,
If the comparison returns negative result then the first parameter will be placed before the second parameter in the sorted array.
If the comparison returns positive result then the first parameter will be placed after the second parameter in the sorted array.
If the comparison is to be equal then they will be placed the same as in the original array.

```javascript
const people = [
  {
    name: "Dom",
    age: 55,
  },
  {
    name: "Sophie",
    age: 96,
  },
  {
    name: "Mark",
    age: 27,
  },
];

const sortedByAge = people.sort(function (a, b) {
  return a.age - b.age;
});

console.log(sortedByAge);
```

_Output:_

```javascript
[
  { name: "Mark", age: 27 },
  { name: "Dom", age: 55 },
  { name: "Sophie", age: 96 },
]
```

In case we need them to be sorted in descending order then

```javascript
const sortedByAgeDescending = people.sort(function (a, b) {
  return b.age - a.age;
});

console.log(sortedByAgeDescending);
```

_Output:_

```javascript
[
  { name: 'Sophie', age: 96 },
  { name: 'Dom', age: 55 },
  { name: 'Mark', age: 27 }
]
```

We can write comparisons on other types of values as well to return numeric results such as

```javascript
const faces = ["😀", "💩", "😃", "😄", "💩", "😁", "😆", "😅", "💩"];

const sorted = faces.sort((a, b) => {
  if (a < b) {
    return -1;
  } else if (a > b) {
    return 1;
  } else {
    return 0;
  }
});
console.log(sorted);
```

_Output:_

```javascript
["💩", "💩", "💩", "😀", "😁", "😃", "😄", "😅", "😆"]
```

`concat` method is used to merge two or more arrays

**In the example, we merge the items of both the arrays**

```javascript
const arr1 = ["😀", "😁"];
const arr2 = ["😃", "😄"];

const newArray = arr1.concat(arr2);
console.log(newArray);
```

_Output:_

```javascript
[ '😀', '😁', '😃', '😄' ]
```

**In the example, we merge the items from the three arrays**

```javascript
const arr1 = ["😀", "😁"];
const arr2 = ["😃", "😄"];
const arr3 = ["😅", "😆"];

const newArray = arr1.concat(arr2, arr3);
console.log(newArray);
```

_Output:_

```javascript
[ '😀', '😁', '😃', '😄', '😅', '😆' ]
```

**In the example, we merge new values to the array**

```javascript
const arr1 = ["😀", "😁"];

const newArray = arr1.concat("💩", ["😃", "😄"]);
console.log(newArray);
```

_Output:_

```javascript
[ '😀', '😁', '💩', '😃', '😄' ]
```

**In the example, we merge concatenated arrays**

```javascript
const num1 = [[1]];
const num2 = [2, [3]];

const numbers = num1.concat(num2);

console.log(numbers);

// adding a value to nested array
num1[0].push(4);

console.log(numbers);
```

_Output:_

```javascript
[ [ 1 ], 2, [ 3 ] ]
[ [ 1, 4 ], 2, [ 3 ] ]
```

`join` method creates and returns a new string by concatenating all of the elements in an array, separated by commas or a specified separator string.

**In the example we join the elements using different separators** 

```javascript
const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join());

console.log(elements.join(''));

console.log(elements.join('-'));
```

_Output:_

```javascript
Fire,Air,Water
FireAirWater
Fire-Air-Water
```

**In the example we join the elements inside a string literal**

```javascript
const horse = {
  name: "Topher 🐴 ",
  size: "large",
  skills: ["jousting", "racing"],
  age: 7,
};

const { name, size, skills } = horse;

const bio = `${name} is a ${size} horse skilled in ${skills.join(" & ")}`;
console.log(bio);
```

_Output:_

```javascript
Topher 🐴  is a large horse skilled in jousting & racing
```

**In the example we join an array-like object**

```javascript
function f(a, b, c) {
  var s = Array.prototype.join.call(arguments);
  console.log(s);
}
f(1, "a", true);
```

_Output:_

```javascript
1,a,true
```

`slice` method returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included) where start and end represent the index of items in that array.

The _`start`_ parameter is the zero-based index at which to start extraction.

A negative index can be used, indicating an offset from the end of the sequence. 

**In the example, slice(-2) extracts the last two elements in the sequence**

```javascript
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(-2));
```

_Output:_

```javascript
[ 'duck', 'elephant' ]
```

**If the _`start`_ is undefined, slice starts from index 0**

```javascript
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice());
```

_Output:_

```javascript
[ 'ant', 'bison', 'camel', 'duck', 'elephant' ]
```

**If _`start`_ is greater than the index range of the sequence, an empty array is returned**

```javascript
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice());
```

_Output:_

```javascript
[]
```

The _`end`_ parameter is the zero-based index before which to end extraction. slice extracts up to but not including end.

**In the example, slice(1,4) extracts the second element through the fourth element (elements indexed 1, 2, and 3).**

```javascript
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(1,4));
```

_Output:_

```javascript
[ 'bison', 'camel', 'duck' ]
```

A negative index can be used, indicating an offset from the end of the sequence. 

**In the example, slice(2,-1) extracts the third element through the second-to-last element in the sequence.**

```javascript
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2,-1));
```

_Output:_

```javascript
[ 'camel', 'duck' ]
```

**If the end is omitted, slice extracts through the end of the sequence**

```javascript
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
```

_Output:_

```javascript
[ 'camel', 'duck', 'elephant' ]
```

**If the end is greater than the length of the sequence, slice extracts through to the end of the sequence**

```javascript
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(0,10));
```

_Output:_

```javascript
[ 'ant', 'bison', 'camel', 'duck', 'elephant' ]
```

`splice` method changes the contents of an array by removing or replacing existing elements and/or adding new elements in place.

_`start`_ parameter is the index at which to start changing the array.

If greater than the length of the array, the start will be set to the length of the array. In this case, no element will be deleted but the method will behave as an adding function, adding as many elements as item[n*] provided.

```javascript
const animals = ["ant", "bison", "camel", "duck", "elephant"];
animals.splice(10, 0, "Giraffe");
console.log(animals);
```

_Output:_

```javascript
[ 'ant', 'bison', 'camel', 'duck', 'elephant', 'Giraffe' ]
```

If negative, it will begin that many elements from the end of the array. 

**In this case, the origin -2, meaning -n is the index of the nth last element and is therefore equivalent to the index of array.length - n**

```javascript
const animals = ["ant", "bison", "camel", "duck", "elephant"];
animals.splice(-2, 0, "Giraffe");
console.log(animals);
```

_Output:_

```javascript
[ 'ant', 'bison', 'camel', 'Giraffe', 'duck', 'elephant' ]
```

**If array.length + start is less than 0, it will begin from index 0**

```javascript
const animals = ["ant", "bison", "camel", "duck", "elephant"];
animals.splice(-7, 0, "Giraffe");
console.log(animals);
```

_Output:_

```javascript
[ 'Giraffe', 'ant', 'bison', 'camel', 'duck', 'elephant' ]
```

_`deleteCount`_ parameter is the integer indicating the number of elements in the array to remove from the start.

If _`deleteCount`_ is omitted, or if its value is equal to or larger than array.length - start (that is if it is equal to or greater than the number of elements left in the array, starting at the start), then all the elements from start to the end of the array will be deleted.

> **Note:** In IE8, it won't delete all when deleteCount is omitted.

```javascript
const animals = ["ant", "bison", "camel", "duck", "elephant"];
animals.splice(1);
console.log(animals);
```

_Output:_

```javascript
[ 'ant' ]
```


If _`deleteCount`_ is 0 or negative, no elements are removed. In this case, you should specify at least one new element (see below).


```javascript
const animals = ["ant", "bison", "camel", "duck", "elephant"];
animals.splice(1,0,"Giraffe");
console.log(animals);
```

_Output:_

```javascript
[ 'ant', 'Giraffe', 'bison', 'camel', 'duck', 'elephant' ]
```

_`item1, item2,...`_ the parameter is the elements to add to the array, beginning from start. 


```javascript
const animals = ["ant", "bison", "camel", "duck", "elephant"];
animals.splice(1, 2, "Giraffe");
console.log(animals);
```

_Output:_

```javascript
[ 'ant', 'Giraffe', 'duck', 'elephant' ]
```

**If you do not specify any elements, splice() will only remove elements from the array.**

```javascript
const animals = ["ant", "bison", "camel", "duck", "elephant"];
animals.splice(1,2);
console.log(animals);
```

_Output:_

```javascript
[ 'ant', 'duck', 'elephant' ]
```

`shift` method removes the first element from an array and returns that removed element. This method changes the length of the array.

```javascript
const array1 = [1, 2, 3];

const firstElement = array1.shift();

console.log(firstElement);

console.log(array1);
```

_Output:_

```javascript
1
[ 2, 3 ]
```

`unshift` method adds one or more elements to the beginning of an array and returns the new length of the array.

```javascript
let arr = [1, 2];

arr.unshift(0);
console.log(arr);

arr.unshift(-2, -1);
console.log(arr);

arr.unshift([-4, -3]);
console.log(arr);

arr.unshift([-7, -6], [-5]);
console.log(arr);
```

_Output:_

```javascript
[ 0, 1, 2 ]
[ -2, -1, 0, 1, 2 ]
[ [ -4, -3 ], -2, -1, 0, 1, 2 ]
[ [ -7, -6 ], [ -5 ], [ -4, -3 ], -2, -1, 0, 1, 2 ]
```


