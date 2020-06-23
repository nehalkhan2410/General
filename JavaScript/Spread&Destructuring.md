_[General](../README.md) > [JavaScript](./main.md) > [Spread Operator & Destructuring](./Spread&Destructuring.md)_

# **JavaScript**

## **Spread Operator & Destructuring**

### **Spread/Rest Operator:**

The spread operator allows an iterable such as an array expression, a string, or an object to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected.

If we want to pass arguments from an array then the normal would be to pass the array along with an index of each element and this could be done in a much easier way using the spread operator.

**Example for passing arguments**

```javascript
const nums = [3, 4, 5];

function addNumbers(a, b, c) {
  console.log(a + b + c);
}
// if we want to pass each element as parameter to the function in a conventional way
addNumbers(nums[0], nums[1], nums[2]);

// passing parameters using spread operator
addNumbers(...nums);
```

_Output:_

```javascript
12
12
```

**Example for shifting and pushing elements in an array**

```javascript
let pokemon = ["Arbok", "Raichu", "Sandshrew"];

// normal way to add something to the array 💩
pokemon.push("Bulbasaur");
pokemon.push("Metapod");
pokemon.push("Weedle");
console.log(pokemon);

// Using spread operator ✅
// push
let _pokemon = ["Arbok", "Raichu", "Sandshrew"];
_pokemon = [..._pokemon, "Bulbasaur", "Metapod", "Weedle"];
console.log(_pokemon);

// unshift
let __pokemon = ["Arbok", "Raichu", "Sandshrew"];
__pokemon = ["Bulbasaur", "Metapod", "Weedle", ...__pokemon];
console.log(__pokemon);
```

_Ouptut:_

```javascript
[ 'Arbok', 'Raichu', 'Sandshrew', 'Bulbasaur', 'Metapod', 'Weedle' ]
[ 'Arbok', 'Raichu', 'Sandshrew', 'Bulbasaur', 'Metapod', 'Weedle' ]
[ 'Bulbasaur', 'Metapod', 'Weedle', 'Arbok', 'Raichu', 'Sandshrew' ]
```

**Example for adding up two arrays**

```javascript
let one = [1, 2, 3];
let two = [4, 5, 6];

// if we want to add contents of both arrays to form a new array
let three = one.concat(two);
console.log(three);

// we can do the same thing using spread operator
three = [...one, ...two];
console.log(three);

// if we want to add contents of b into a instead of pushing each elements we can use spread operator
one.push(...two);
console.log(one);
```

_Output:_

```javascript
[ 1, 2, 3, 4, 5, 6 ]
[ 1, 2, 3, 4, 5, 6 ]
[ 1, 2, 3, 4, 5, 6 ]
```

**Example for inserting one array inside another array**

```javascript
let dowhatever = ["have fun", "have more fun", "have some more fun"];
let life = [
  "born",
  "learn to walk",
  "learn to speak",
  ...dowhatever,
  "go to heaven",
];

console.log(life);
```

_Output:_

```javascript
[
  "born",
  "learn to walk",
  "learn to speak",
  "have fun",
  "have more fun",
  "have some more fun",
  "go to heaven",
];
```

**Example for merging one object into another**

```javascript
const pikachu = { name: "Pikachu 🐹" };
const stats = { hp: 40, attack: 60, defense: 45 };

// normal way to assign new properties to an object 💩
pikachu["hp"] = stats.hp;
pikachu["attack"] = stats.attack;
pikachu["defense"] = stats.defense;
// this is mutating original object but we likely need to create a new immutable object
console.log(pikachu);

// merging from left to right to a new object using assign
const lvl10 = Object.assign(pikachu, stats);
console.log(lvl10);
// adding a new property at the end
const lvl11 = Object.assign(pikachu, { hp: 50 });
console.log(lvl11);

// Using spread operator ✅
const lvl12 = { ...pikachu, ...stats };
console.log(lvl12);
const lvl13 = { ...pikachu, hp: 60 };
console.log(lvl13);
```

_Ouptut:_

```javascript
{ name: 'Pikachu 🐹', hp: 40, attack: 60, defense: 45 }
{ name: 'Pikachu 🐹', hp: 40, attack: 60, defense: 45 }
{ name: 'Pikachu 🐹', hp: 50, attack: 60, defense: 45 }
{ name: 'Pikachu 🐹', hp: 40, attack: 60, defense: 45 }
{ name: 'Pikachu 🐹', hp: 60, attack: 60, defense: 45 }
```

Rest syntax looks exactly like spread syntax but is used for destructuring arrays and objects.

In a way, rest syntax is the opposite of spread syntax. Spread syntax "expands" an array into its elements, while rest syntax collects multiple elements and "condenses" them into a single element.

```javascript
// here the passed arguements are stored in `n` as array
let x = function (...n) {
  console.log(n);
};

x(1, 2, 3);

// here the first argument goes into `a` and all the rest are stored in `rest` as an array
x = function (a, ...rest) {
  console.log(a, rest);
};

x(1, 2, 3);
```

_Output:_

```javascript
[ 1, 2, 3 ]
1 [ 2, 3 ]
```

### **Destructuring:**

The destructuring assignment syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.

**Array Destructuring:**

In array destructuring, the elements are stored into variables in the order which they are assigned.

```javascript
const alphabets = ["A", "B", "C", "D", "E", "F"];
const numbers = ["1", "2", "3", "4", "5", "6"];

console.log(alphabets[0], alphabets[1]);

// here it takes based on position
let [a, b, ...rest] = alphabets;

console.log(a, b, rest);

// here if we skip the position of assignment then it also skips the element from the array itself
let [a, , c, ...rest] = alphabets;

console.log(a, c, rest);
```

_Ouptut:_

```javascript
A B [ 'C', 'D', 'E', 'F' ]
A C [ 'D', 'E', 'F' ]
```

**Example for destructuring array output from a function**

```javascript
// a function that returns sum and multiplication
function sumAndMultiply(a, b) {
  return [a + b, a * b];
}

// a function that returns sum, multiplication and division
function sumAndMultiplyDivision(a, b) {
  return [a + b, a * b, a / b];
}

// here it prints the output as a whole array
const result = sumAndMultiplyDivision(2, 3);
console.log(result);

// if we want to store the results separately for each of them
let [sum, multiply, division] = sumAndMultiply(2, 3);
console.log(sum, multiply, division); // since division is not returned it is undefined

// if we want to give a default value to the returned result whenever it not supplied
[sum, multiply, division = "No Division"] = sumAndMultiply(2, 3);
console.log(sum, multiply, division);

// the default value will be overriden if the function returns a value
[sum, multiply, division = "No Division"] = sumAndMultiplyDivision(2, 3);
console.log(sum, multiply, division);
```

_Ouptut:_

```javascript
[ 5, 6, 0.6666666666666666 ]
5 6 undefined
5 6 No Division
5 6 0.6666666666666666
```

**Object Destructuring:**

In object destructuring, the values are stored into variables as per the name of the keys in the object.

**Example for destructuring object**

```javascript
const personOne = {
  name: "Kyle",
  age: 24,
  favoriteFood: "Pasta",
  address: {
    city: "Some where",
    state: "One of them",
  },
};

const personTwo = {
  age: 32,
  address: {
    city: "Some where else",
    state: "Another one of them",
  },
};

// the properties from the personOne with same key names are stored in the varaibles
let { name, favoriteFood } = personOne;
console.log(name, favoriteFood);

// we can give aliases to the variables from the object and please remember to use the same later in the code
// we can pass default values as well if there none defined for that object
let { name: _firstName = "John", favoriteFood: food = "Rice" } = personTwo;
console.log(_firstName, food);

// here the age goes to `myAge` and all the rest of the arguments are saved into `rest` variable
let { age: myAge, ...rest } = personOne;
console.log(myAge, rest);

// we can destructure the nested object as shown
const {
  name: firstName,
  address: { city },
} = personOne;
console.log(firstName, city);
```

_Ouptut:_

```javascript
Kyle Pasta
John Rice
24 {
  name: 'Kyle',
  favoriteFood: 'Pasta',
  address: { city: 'Some where', state: 'One of them' }
}
Kyle Some where
```

**Example for merging two objects**

```javascript
// if the properties are same then they will be overwritten or else they will be merged
const personThree = { ...personOne, ...personTwo };
console.log(personThree);
```

_Ouptut:_

```javascript
{
  name: 'Kyle',
  age: 32,
  favoriteFood: 'Pasta',
  address: { city: 'Some where else', state: 'Another one of them' }
}
```

**Example for destructuring object as paramters to a function**

```javascript
const turtle = {
  name: "Bob 🐢",
  legs: 4,
  shell: true,
  type: "amphibious",
  meal: 10,
  diet: "berries",
};

// normal way to pass object as a parameter and use required properties 💩
function feed(animal) {
  console.log(`Feed ${animal.name} ${animal.meal} kilos of ${animal.diet}`);
}
feed(turtle);

// the required properties can be destructured as parameters itself like shown ✅
function _feed({ name, meal, diet }) {
  console.log(`Feed ${name} ${meal} kilos of ${diet}`);
}
_feed(turtle);

// The required properties can be destructured later inside the function
//  Better way to go if we have multiple objects to destucture in the same function ✅
function __feed(animal) {
  const { name, meal, diet } = animal;
  console.log(`Feed ${name} ${meal} kilos of ${diet}`);
}
__feed(turtle);
```

_Ouptut:_

```javascript
Feed Bob 🐢 10 kilos of berries
Feed Bob 🐢 10 kilos of berries
Feed Bob 🐢 10 kilos of berries
```
