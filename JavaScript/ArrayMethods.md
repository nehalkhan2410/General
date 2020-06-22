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

Now let's take a look at a few built-in array methods that can do most of the tasks in a better and much cleaner way.

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

In the example, we filter out the items whose price is less than or equal to 100.

```javascript
const filteredItems = items.filter((item) => {
  return item.price <= 100;
});
console.log(filteredItems);
```

In the example, we filter out the item which is an odd one out.

```javascript
const feces = faces.filter((v) => v === "💩");
```

`map` method iterates over each element in the array and takes that item as a parameter and performs some given action on it and returns it.

In the example, we return the name from the object to be part of the resulting array.

```javascript
const itemNames = items.map((item) => {
  return item.name;
});
console.log(itemNames);
```

In the example, we replace each item in the array with a new value to be part of the resulting array.

```javascript
const faces = ["💩"];
const cleaned = feces.map((v) => "⛅");
```

`find` method iterates over each element in the array and takes that item as a parameter and checks a given condition to return a boolean value as output based on the result of that condition.

In the example, we check for a condition on each item and return a boolean output.

```javascript
const foundItem = items.find((item) => {
  return item.name === "Book";
});
console.log(foundItem);
```

`forEach` is a shorter way to iterate over an array and perform some action with each element.

In the example, we iterate over the elements of the array and print the name from each item.

```javascript
items.forEach((item) => {
  console.log(item.name);
});
```

`some` method iterates over each element in the array and takes that item as a parameter and returns true as output if the given condition is satisfied at least one time.

In the example, we iterate over the elements and return true if the condition is satisfied at least once.

```javascript
const hasInexpensiveItems = items.some((item) => {
  return item.price <= 100;
});
console.log(hasInexpensiveItems);
```

In the example, we iterate over the elements and return true if the item matches with given character at least once.

```javascript
const isPoopy = faces.some((v) => v === "💩");
console.log(isPoopy);
```

`every` method iterates over each element in the array and takes that item as a parameter and returns true as output if the given condition is satisfied for every item.

In the example, we iterate over the elements and return true if the condition is satisfied for every item.

```javascript
const _hasInexpensiveItems = items.every((item) => {
  return item.price <= 1000;
});
console.log(_hasInexpensiveItems);
```

In the example, we iterate over the elements and return true if the character of the item is greater than the given character every time.

```javascript
const isEmoji = faces.every((v) => v > "ÿ");
console.log(isEmoji);
```

`reduce` method iterates over each element in the array and takes two parameters, first a function with an accumulator value and the item itself as two parameters, and initial value for the accumulator as the second parameter. And perform some calculation on each item to change the accumulated value for each iteration to return the desired output.

In the example, we iterate over each item to add up the price to the initial value of the accumulator.

```javascript
const total = items.reduce((currentTotal, item) => {
  return item.price + currentTotal;
}, 0); // 0 is the initial value for the accumulator
console.log(total);
```

In the example, we iterate over each item to increment the initial value of the accumulator by one, if the current one matches with the given character. 

```javascript
const pooCount = _faces.reduce((acc, cur) => {
  return acc + (cur === "💩" ? 1 : 0);
}, 0); // 0 is the initial value for the accumulator

console.log(pooCount);
```

`includes` method checks if the given value is present in the array or not to return a boolean output.

```javascript
const numbers = [1, 2, 3, 4, 5];

const includesTwo = numbers.includes(2);
console.log(includesTwo);
```

sort 2
concat
join
slice 2
splice
shift
unshift
