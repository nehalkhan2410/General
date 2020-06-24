_[General](../README.md) > [JavaScript](./main.md) > [Template Literals](./TemplateLiterals.md)_

# **JavaScript**

## **Template Literals**

Template literals are enclosed by the backtick (``) character instead of double or single quotes. Template literals can contain placeholders/variables. These are indicated by the dollar sign and curly braces (\${expression}).

These are a new way to create strings which brings new features like:

- String Interpolation
- Embedded Expressions
- Multi-line Strings
- Nesting Templates
- Tagged Templates

**String Interpolation:**

Generally, when we talk about interpolation, we concatenate the strings with variables to form a complete sentence.

```javascript
let a = 5;
let b = 10;

// Normal way of String interpolation 💩
console.log("Fifteen is " + (a + b) + " and\nnot " + (2 * a + b) + ".");

// Interpolation using string literals ✅
console.log(`Fifteen is ${a + b} and not ${2 * a + b}.`);
```

_Output:_

```javascript
Fifteen is 15 and
not 20.
Fifteen is 15 and not 20.
```

**Embedded Expressions:**

We embed expressions in a string by concatenating them with static string content.

```javascript
const horse = {
  name: "Topher 🐴",
  size: "large",
  skills: ["jousting", "racing"],
  age: 7,
};

// Normal way of String interpolation 💩
let bio =
  horse.name +
  " is a " +
  horse.size +
  " horse skilled in " +
  horse.skills.join(" & ");
console.log(bio);

// Interpolation using string literals ✅
bio = `${horse.name} is a ${horse.size} horse skilled in ${horse.skills.join(
  " & "
)}`;
console.log(bio);
```

_Output:_

```javascript
Topher 🐴 is a large horse skilled in jousting & racing
Topher 🐴 is a large horse skilled in jousting & racing
```

**Multi-line Strings:**

Normally, you would have to use the following syntax with newline characters in order to get multi-line strings:

```javascript
// Normal way of getting multi-line string 💩
console.log("string text line 1\n" + "string text line 2");

// Using string literals ✅
console.log(`string text line 1
string text line 2`);
```

_Output:_

```javascript
string text line 1
string text line 2
string text line 1
string text line 2
```

**Nesting Templates:**

In certain cases, nesting a template is the easiest (and perhaps more readable) way to have configurable strings. For instance, if condition a is true, then return this templated literal.

```javascript
function isLargeScreen() {
  return false;
}

let item = {
  isCollapsed: false,
};

// Normal way of check a condition and form a template 💩
let classes = "header";
classes += isLargeScreen()
  ? ""
  : item.isCollapsed
  ? " icon-expander"
  : " icon-collapser";

// Template literals and without nesting ✅
const classes = `header ${
  isLargeScreen() ? "" : item.isCollapsed ? "icon-expander" : "icon-collapser"
}`;

// Nested Template literals ✅
const classes = `header ${
  isLargeScreen() ? "" : `icon-${item.isCollapsed ? "expander" : "collapser"}`
}`;
```

_Output:_

```javascript
header icon-collapser
```

**Tagged Templates:**

Tags allow you to parse template literals with a function. The first argument of a tag function contains an array of string values. The remaining arguments are related to the expressions.

```javascript
const horse = {
  name: "Topher 🐴 ",
  size: "large",
  skills: ["jousting", "racing"],
  age: 7,
  🌐
};

// The string passed to function is considered as first paramter, and provided expressions are the following parameters
function horseAge(str, age, skill) {
  const ageStr = age > 5 ? "old" : "young";
  console.log(`${str[0]}${ageStr} at ${age} years${str[1]}${skill}`);
}

horseAge`This horse is ${horse.age} skilled at ${horse.skills}`;
```

_Output:_

```javascript
This horse is old at 7 years skilled at jousting,racing
```
