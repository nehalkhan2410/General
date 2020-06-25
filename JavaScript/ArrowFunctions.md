_[General](../README.md) > [JavaScript](./main.md) > [Arrow Functions](./ArrowFunctions.md)_

# **JavaScript**

## **Arrow Functions**

### **Function with a single parameter**

```javascript
// Function with one parameter
function isPositive(number) {
  return number >= 0;
}

// Arrow function with one parameter
let _isPositive = (number) => {
  return number >= 0;
};

// If it has a single parameter then we can omit the paranthesis completely 
// and since it just has a return statement inside the block we can skip that 
// and everything after => is considered as a return statement.
let _isPositive_ = (number) => number >= 0;

console.log(isPositive(5), _isPositive(5), _isPositive_(5));
```

_Output:_

```javascript
true true true
```

### **Function with two parameters**

```javascript
// Function with two parameters
function sum(a, b) {
  return a + b;
}

// Two parameters are surrounded by paranthesis.
let _sum = (a, b) => {
  return a + b;
};

// Since it just has a return statement inside the block we can skip that return 
// and everything after => is considered as a return statement.
let _sum_ = (a, b) => a + b;
console.log(sum(4, 5), _sum(9, 4), _sum_(10, 2));
```

_Output:_

```javascript
9 13 12
```

### **Function with no parameter(s)**

```javascript
// Function with no parameter
function randonNumber() {
  return Math.random();
}

// We provide empty paranthesis if there no parameters.
let _randomNumber = () => {
  return Math.random();
};

// Since it just has a return statement inside the block we can skip that return 
// and everything after => is considered as a return statement here.
let _randomNumber_ = () => Math.random();

console.log(randonNumber(), _randomNumber(), _randomNumber_());
```

_Output:_

```javascript
0.6592502157878466 0.32602803839516525 0.3468706177062806
```

### **Anonymous function**

```javascript
// Anonymous function
document.addEventListener("click", function () {
  console.log("Click");
});

// We provide empty paranthesis as there no parameters passed to anonymous function.
document.addEventListener("click", () => {
  console.log("Click");
});

// Since it just has a single statement inside the block we can skip the curly braces.
document.addEventListener("click", () => console.log("Click"));
```

_Output:_

```javascript
Click
Click
Click
```

**Here is an example that shows how a normal function and an arrow function make use of `this` keyword within their scopes**

The arrow function shares the scope of its parent without its own bindings to `this`, arguments, super, or new.target keywords, so the value of `this` is not redefined but is the same as that of its parent function.

A normal function creates a new scope for itself once it is declared, so the value of `this` would also be redefined within the function. So it can't access the elements from its parent scope.

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
