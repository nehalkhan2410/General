*[General](../README.md) > [JavaScript](./main.md) > [Arrow Functions](./ArrowFunctions.md)*

# **JavaScript**

## **Arrow Functions**

**Function with a single parameter:**

```javascript
// Function with one parameter
function isPositive(number) {
  return number >= 0;
}

// Arrow function with one parameter
let isPositive2 = (number) => {
  return number >= 0;
}

// If it has a single parameter then we can omit the paranthesis completely and since it just has a return statement inside the block we can skip that and everything after => is considered as a return statement.
let isPositive3 = number => number >= 0;
```
**Function with two parameters:**

```javascript
// Function with two parameters
function sum(a, b) {
  return a + b;
}

// Two parameters are surrounded by paranthesis.
let sum2 = (a, b) => {
  return a + b;
}

// Since it just has a return statement inside the block we can skip that retunr and everything after => is considered as a return statement.
let sum3 = (a, b) => a + b;
```
**Function with no parameters:**

```javascript
// Function with no parameter
function randonNumber() {
  return Math.random();
}

// We provide empty paranthesis if there no parameters.
let randomNumber2 = () => {
  return Math.random();
}

// Since it just has a return statement inside the block we can skip that return and everything after => is considered as a return statement here.
let randomNumber3 = () => Math.random();
```

**Anonymous function:**

```javascript
// Anonymous function
document.addEventListener("click", function () {
  console.log("Click");
});

// We provide empty paranthesis as there no parameters passed to anonymous function.
document.addEventListener("click", () => {
  console.log("Click")
});

// Since it just has a single statement inside the block we can skip the curly braces.
document.addEventListener("click", () => console.log("Click"));
```
**Here is an example that shows how a normal function and an arrow function make use of `this` keyword within their scopes**

The arrow function shares the scope of its parent in this case setTImeout and printNameArrow function so the value of `this` is not redefined but is same as that of its parent function.

The normal function creates a new scope for itself once it is declared so the value of `this` would also be redefined within the function. So it can't access the elements from its parent function.

```javascript
class Person {
  constructor(name) {
    this.name = name;
  }

  printNameArrow() {
    setTimeout(() => {
      // An arrow function doesn't redefine this keyword
      console.log(`Arrow: ${this.name}`);
    }, 100);
  }

  printNameFuncion() {
    setTimeout(function () {
      // A normal function redefines this keyword
      console.log(`Function: ${this.name}`);
    }, 100);
  }
}

let person = new Person("Kyle");
person.printNameArrow();
person.printNameFuncion();
```

**Output:**
```javascript
Arrow: Kyle
Function: undefined
```