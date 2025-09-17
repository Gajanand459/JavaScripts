# Complete JavaScript Guide 📚

[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)]()
[![ES6+](https://img.shields.io/badge/ES6+-4CAF50?style=for-the-badge&logo=javascript&logoColor=white)]()
[![Node.js](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)]()
[![Browser](https://img.shields.io/badge/Browser-FF5722?style=for-the-badge&logo=google-chrome&logoColor=white)]()

## 📋 Table of Contents

1. [JavaScript Fundamentals](#-javascript-fundamentals)
2. [Variables and Data Types](#-variables-and-data-types)
3. [Operators](#-operators)
4. [Control Structures](#-control-structures)
5. [Functions](#-functions)
6. [Objects and Classes](#-objects-and-classes)
7. [Arrays and Array Methods](#-arrays-and-array-methods)
8. [Strings and String Methods](#-strings-and-string-methods)
9. [Scope and Closures](#-scope-and-closures)
10. [Asynchronous JavaScript](#-asynchronous-javascript)
11. [DOM Manipulation](#-dom-manipulation)
12. [Event Handling](#-event-handling)
13. [Error Handling](#-error-handling)
14. [Modules and Imports](#-modules-and-imports)
15. [Advanced Concepts](#-advanced-concepts)
16. [Browser APIs](#-browser-apis)
17. [JavaScript Patterns](#-javascript-patterns)
18. [Performance Optimization](#-performance-optimization)
19. [Testing in JavaScript](#-testing-in-javascript)
20. [Modern JavaScript Features](#-modern-javascript-features)

---

## 🚀 JavaScript Fundamentals

### What is JavaScript?
JavaScript is a high-level, interpreted programming language that enables interactive web pages and server-side development.

### Key Characteristics
- **Dynamic Typing**: Variables can hold different types of values
- **Interpreted Language**: No compilation step required
- **First-class Functions**: Functions are treated as values
- **Prototype-based OOP**: Object-oriented programming through prototypes
- **Event-driven**: Responds to user interactions and system events

### JavaScript Execution Context
```javascript
// Global Execution Context
var globalVar = 'I am global';

function createExecutionContext() {
  // Function Execution Context
  var localVar = 'I am local';
  
  function nestedFunction() {
    // Another Function Execution Context
    var nestedVar = 'I am nested';
    console.log(globalVar, localVar, nestedVar);
  }
  
  nestedFunction();
}

createExecutionContext();
```

### The JavaScript Engine
```javascript
// Hoisting Example
console.log(hoistedVar); // undefined (not ReferenceError)
var hoistedVar = 'This is hoisted';

console.log(hoistedFunction()); // "I'm hoisted!"
function hoistedFunction() {
  return "I'm hoisted!";
}

// Let and const are not hoisted in the same way
console.log(letVar); // ReferenceError: Cannot access before initialization
let letVar = 'Let variable';
```

---

## 📊 Variables and Data Types

### Variable Declarations

#### var (Function Scoped)
```javascript
var varVariable = 'I am var';
var varVariable = 'I can be redeclared'; // No error

function varExample() {
  if (true) {
    var functionScoped = 'Available throughout function';
  }
  console.log(functionScoped); // Accessible here
}
```

#### let (Block Scoped)
```javascript
let letVariable = 'I am let';
// let letVariable = 'Error'; // SyntaxError: Identifier already declared

function letExample() {
  if (true) {
    let blockScoped = 'Only available in this block';
    console.log(blockScoped); // Accessible here
  }
  // console.log(blockScoped); // ReferenceError
}
```

#### const (Block Scoped, Immutable)
```javascript
const constVariable = 'I am const';
// constVariable = 'Error'; // TypeError: Assignment to constant variable

// Objects and arrays can be mutated
const constObject = { name: 'JavaScript' };
constObject.name = 'JS'; // This is allowed
constObject.version = 'ES6+'; // This is allowed

const constArray = [1, 2, 3];
constArray.push(4); // This is allowed
// constArray = [1, 2, 3, 4]; // This is not allowed
```

### Data Types

#### Primitive Data Types
```javascript
// Number
let integer = 42;
let float = 3.14159;
let scientific = 2.998e8;
let infinity = Infinity;
let notANumber = NaN;

console.log(typeof integer); // "number"
console.log(Number.isInteger(integer)); // true
console.log(Number.isNaN(notANumber)); // true

// String
let singleQuotes = 'Hello';
let doubleQuotes = "World";
let templateLiteral = `Hello ${doubleQuotes}!`;
let multiLine = `This is
a multi-line
string`;

// Boolean
let isTrue = true;
let isFalse = false;
let truthyValue = Boolean(1); // true
let falsyValue = Boolean(0); // false

// Undefined
let undefinedVar;
console.log(undefinedVar); // undefined

// Null
let nullVar = null;
console.log(nullVar); // null

// Symbol (ES6+)
let symbol1 = Symbol('description');
let symbol2 = Symbol('description');
console.log(symbol1 === symbol2); // false - symbols are unique

// BigInt (ES2020)
let bigNumber = BigInt(9007199254740991);
let bigNumberLiteral = 9007199254740991n;
```

#### Non-Primitive Data Types
```javascript
// Object
let person = {
  name: 'John',
  age: 30,
  city: 'New York',
  greet: function() {
    return `Hello, I'm ${this.name}`;
  }
};

// Array
let numbers = [1, 2, 3, 4, 5];
let mixedArray = [1, 'string', true, null, undefined, {}];

// Function
function regularFunction() {
  return 'I am a function';
}

let arrowFunction = () => 'I am an arrow function';

// Date
let currentDate = new Date();
let specificDate = new Date('2024-01-01');

// RegExp
let regex = /[a-z]+/gi;
let regexConstructor = new RegExp('[a-z]+', 'gi');
```

#### Type Checking and Conversion
```javascript
// Type checking
console.log(typeof 42); // "number"
console.log(typeof 'hello'); // "string"
console.log(typeof true); // "boolean"
console.log(typeof undefined); // "undefined"
console.log(typeof null); // "object" (this is a known quirk)
console.log(typeof {}); // "object"
console.log(typeof []); // "object"
console.log(typeof function() {}); // "function"

// Better type checking for objects
console.log(Object.prototype.toString.call([])); // "[object Array]"
console.log(Array.isArray([])); // true

// Type conversion
let numStr = '123';
let num = Number(numStr); // 123
let num2 = parseInt(numStr); // 123
let num3 = parseFloat('123.45'); // 123.45
let num4 = +numStr; // 123 (unary plus operator)

let str = String(123); // "123"
let str2 = (123).toString(); // "123"

let bool = Boolean(1); // true
let bool2 = !!1; // true (double negation)
```

---

## 🔢 Operators

### Arithmetic Operators
```javascript
let a = 10;
let b = 3;

console.log(a + b); // 13 (Addition)
console.log(a - b); // 7 (Subtraction)
console.log(a * b); // 30 (Multiplication)
console.log(a / b); // 3.333... (Division)
console.log(a % b); // 1 (Modulus/Remainder)
console.log(a ** b); // 1000 (Exponentiation - ES2016)

// Increment and Decrement
let x = 5;
console.log(x++); // 5 (post-increment)
console.log(++x); // 7 (pre-increment)
console.log(x--); // 7 (post-decrement)
console.log(--x); // 5 (pre-decrement)
```

### Assignment Operators
```javascript
let value = 10;

value += 5; // value = value + 5; (15)
value -= 3; // value = value - 3; (12)
value *= 2; // value = value * 2; (24)
value /= 4; // value = value / 4; (6)
value %= 3; // value = value % 3; (0)
value **= 2; // value = value ** 2; (0)

// Logical assignment (ES2021)
let obj = { a: 1 };
obj.b ??= 2; // obj.b = obj.b ?? 2 (assign if nullish)
obj.a &&= 5; // obj.a = obj.a && 5 (assign if truthy)
obj.c ||= 3; // obj.c = obj.c || 3 (assign if falsy)
```

### Comparison Operators
```javascript
let x = 5;
let y = '5';

console.log(x == y); // true (loose equality)
console.log(x === y); // false (strict equality)
console.log(x != y); // false (loose inequality)
console.log(x !== y); // true (strict inequality)

console.log(x > 3); // true
console.log(x < 10); // true
console.log(x >= 5); // true
console.log(x <= 5); // true

// Special cases
console.log(null == undefined); // true
console.log(null === undefined); // false
console.log(NaN === NaN); // false
console.log(Object.is(NaN, NaN)); // true
```

### Logical Operators
```javascript
let a = true;
let b = false;

console.log(a && b); // false (AND)
console.log(a || b); // true (OR)
console.log(!a); // false (NOT)

// Short-circuit evaluation
function expensiveOperation() {
  console.log('This is expensive!');
  return true;
}

false && expensiveOperation(); // expensiveOperation is not called
true || expensiveOperation(); // expensiveOperation is not called

// Nullish coalescing operator (ES2020)
let user = null;
let defaultUser = 'Anonymous';
console.log(user ?? defaultUser); // 'Anonymous'

let config = { theme: '', timeout: 0 };
console.log(config.theme || 'dark'); // 'dark' (empty string is falsy)
console.log(config.theme ?? 'dark'); // '' (empty string is not nullish)
console.log(config.timeout || 5000); // 5000 (0 is falsy)
console.log(config.timeout ?? 5000); // 0 (0 is not nullish)
```

### Bitwise Operators
```javascript
let a = 5; // 101 in binary
let b = 3; // 011 in binary

console.log(a & b); // 1 (AND: 001)
console.log(a | b); // 7 (OR: 111)
console.log(a ^ b); // 6 (XOR: 110)
console.log(~a); // -6 (NOT)
console.log(a << 1); // 10 (Left shift: 1010)
console.log(a >> 1); // 2 (Right shift: 010)
console.log(a >>> 1); // 2 (Unsigned right shift)
```

### Ternary Operator
```javascript
let age = 20;
let status = age >= 18 ? 'adult' : 'minor';
console.log(status); // 'adult'

// Nested ternary (use with caution)
let score = 85;
let grade = score >= 90 ? 'A' : score >= 80 ? 'B' : score >= 70 ? 'C' : 'F';
console.log(grade); // 'B'

// Better approach with functions
function calculateGrade(score) {
  if (score >= 90) return 'A';
  if (score >= 80) return 'B';
  if (score >= 70) return 'C';
  return 'F';
}
```

---

## 🔀 Control Structures

### Conditional Statements

#### if...else
```javascript
let weather = 'sunny';

if (weather === 'sunny') {
  console.log('Wear sunglasses!');
} else if (weather === 'rainy') {
  console.log('Take an umbrella!');
} else if (weather === 'snowy') {
  console.log('Wear a coat!');
} else {
  console.log('Check the weather forecast!');
}

// Truthy and falsy values
let value = 0;
if (value) {
  console.log('Truthy');
} else {
  console.log('Falsy'); // This will execute
}

// Falsy values: false, 0, -0, 0n, "", null, undefined, NaN
// Everything else is truthy
```

#### switch
```javascript
let day = 'Monday';

switch (day) {
  case 'Monday':
  case 'Tuesday':
  case 'Wednesday':
  case 'Thursday':
  case 'Friday':
    console.log('Weekday');
    break;
  case 'Saturday':
  case 'Sunday':
    console.log('Weekend');
    break;
  default:
    console.log('Invalid day');
}

// Switch with expressions (proposal)
function getDayType(day) {
  return switch (day) {
    case 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday' -> 'Weekday';
    case 'Saturday', 'Sunday' -> 'Weekend';
    default -> 'Invalid day';
  };
}
```

### Loops

#### for Loop
```javascript
// Traditional for loop
for (let i = 0; i < 5; i++) {
  console.log(i); // 0, 1, 2, 3, 4
}

// Nested loops
for (let i = 1; i <= 3; i++) {
  for (let j = 1; j <= 3; j++) {
    console.log(`${i}-${j}`);
  }
}

// Loop with break and continue
for (let i = 0; i < 10; i++) {
  if (i === 3) continue; // Skip 3
  if (i === 7) break; // Stop at 7
  console.log(i); // 0, 1, 2, 4, 5, 6
}
```

#### for...in Loop (for object properties)
```javascript
let person = {
  name: 'John',
  age: 30,
  city: 'New York'
};

for (let property in person) {
  console.log(`${property}: ${person[property]}`);
}

// Be careful with arrays
let numbers = [10, 20, 30];
numbers.customProperty = 'custom';

for (let index in numbers) {
  console.log(index); // '0', '1', '2', 'customProperty'
}
```

#### for...of Loop (for iterable objects)
```javascript
let numbers = [10, 20, 30];

for (let number of numbers) {
  console.log(number); // 10, 20, 30
}

// Works with strings
let word = 'JavaScript';
for (let char of word) {
  console.log(char); // J, a, v, a, S, c, r, i, p, t
}

// Works with Maps and Sets
let map = new Map([['a', 1], ['b', 2]]);
for (let [key, value] of map) {
  console.log(`${key}: ${value}`);
}

let set = new Set([1, 2, 3]);
for (let value of set) {
  console.log(value);
}

// Get both index and value
for (let [index, value] of numbers.entries()) {
  console.log(`${index}: ${value}`);
}
```

#### while Loop
```javascript
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}

// Be careful with infinite loops
let condition = true;
while (condition) {
  console.log('This would run forever');
  condition = false; // Make sure to update the condition
}
```

#### do...while Loop
```javascript
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);

// The loop body executes at least once
let j = 10;
do {
  console.log(j); // This will print 10 once
  j++;
} while (j < 5);
```

### Loop Control

#### break and continue
```javascript
// break - exits the loop entirely
for (let i = 0; i < 10; i++) {
  if (i === 5) break;
  console.log(i); // 0, 1, 2, 3, 4
}

// continue - skips current iteration
for (let i = 0; i < 10; i++) {
  if (i % 2 === 0) continue;
  console.log(i); // 1, 3, 5, 7, 9 (odd numbers only)
}

// Labeled statements (rarely used)
outer: for (let i = 0; i < 3; i++) {
  inner: for (let j = 0; j < 3; j++) {
    if (i === 1 && j === 1) break outer;
    console.log(`${i}-${j}`);
  }
}
```

---

## 🔧 Functions

### Function Declarations
```javascript
// Function declaration (hoisted)
function greet(name) {
  return `Hello, ${name}!`;
}

console.log(greet('Alice')); // Works even before declaration due to hoisting

// Function with default parameters
function greetWithDefault(name = 'World') {
  return `Hello, ${name}!`;
}

console.log(greetWithDefault()); // "Hello, World!"
console.log(greetWithDefault('Bob')); // "Hello, Bob!"

// Function with rest parameters
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3, 4, 5)); // 15
```

### Function Expressions
```javascript
// Function expression (not hoisted)
const multiply = function(a, b) {
  return a * b;
};

// Named function expression
const factorial = function fact(n) {
  return n <= 1 ? 1 : n * fact(n - 1);
};

// Immediately Invoked Function Expression (IIFE)
(function() {
  console.log('This function runs immediately!');
})();

// IIFE with parameters
(function(name) {
  console.log(`Hello, ${name}!`);
})('JavaScript');
```

### Arrow Functions
```javascript
// Basic arrow function
const add = (a, b) => a + b;

// With single parameter (parentheses optional)
const square = x => x * x;

// With no parameters
const sayHello = () => 'Hello!';

// With block body
const complexFunction = (a, b) => {
  const result = a * b;
  console.log(`Result: ${result}`);
  return result;
};

// Arrow functions and 'this'
const obj = {
  name: 'Object',
  regularMethod: function() {
    console.log(this.name); // 'Object'
    
    const arrowInside = () => {
      console.log(this.name); // 'Object' (inherits from outer scope)
    };
    arrowInside();
  },
  arrowMethod: () => {
    console.log(this.name); // undefined (no own 'this')
  }
};
```

### Higher-Order Functions
```javascript
// Function that takes another function as parameter
function operate(a, b, operation) {
  return operation(a, b);
}

const add = (x, y) => x + y;
const multiply = (x, y) => x * y;

console.log(operate(5, 3, add)); // 8
console.log(operate(5, 3, multiply)); // 15

// Function that returns another function
function createMultiplier(multiplier) {
  return function(number) {
    return number * multiplier;
  };
}

const double = createMultiplier(2);
const triple = createMultiplier(3);

console.log(double(5)); // 10
console.log(triple(4)); // 12

// Function composition
const compose = (f, g) => (x) => f(g(x));

const addOne = x => x + 1;
const multiplyByTwo = x => x * 2;

const addOneAndDouble = compose(multiplyByTwo, addOne);
console.log(addOneAndDouble(3)); // 8 ((3 + 1) * 2)
```

### Function Methods (call, apply, bind)
```javascript
const person = {
  name: 'John',
  greet: function(greeting, punctuation) {
    return `${greeting}, ${this.name}${punctuation}`;
  }
};

const anotherPerson = { name: 'Jane' };

// call - invoke function with specific 'this' and individual arguments
console.log(person.greet.call(anotherPerson, 'Hello', '!')); // "Hello, Jane!"

// apply - invoke function with specific 'this' and array of arguments
console.log(person.greet.apply(anotherPerson, ['Hi', '.'])); // "Hi, Jane."

// bind - create new function with specific 'this'
const boundGreet = person.greet.bind(anotherPerson);
console.log(boundGreet('Hey', '?')); // "Hey, Jane?"

// Partial application with bind
const sayHello = person.greet.bind(anotherPerson, 'Hello');
console.log(sayHello('!')); // "Hello, Jane!"
```

### Recursive Functions
```javascript
// Factorial
function factorial(n) {
  if (n <= 1) return 1;
  return n * factorial(n - 1);
}

// Fibonacci
function fibonacci(n) {
  if (n <= 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}

// Fibonacci with memoization
function fibonacciMemo() {
  const cache = {};
  
  return function fib(n) {
    if (n in cache) return cache[n];
    if (n <= 1) return n;
    
    cache[n] = fib(n - 1) + fib(n - 2);
    return cache[n];
  };
}

const memoizedFib = fibonacciMemo();
console.log(memoizedFib(40)); // Much faster than regular fibonacci
```

---

## 🏗️ Objects and Classes

### Object Creation and Manipulation
```javascript
// Object literal
const person = {
  name: 'John',
  age: 30,
  city: 'New York',
  
  // Method
  greet() {
    return `Hello, I'm ${this.name}`;
  },
  
  // Computed property name
  ['prop_' + 'computed']: 'computed value'
};

// Property access
console.log(person.name); // Dot notation
console.log(person['age']); // Bracket notation
console.log(person['prop_computed']); // 'computed value'

// Adding properties
person.email = 'john@example.com';
person['phone'] = '123-456-7890';

// Object destructuring
const { name, age, city } = person;
const { name: personName, age: personAge } = person; // Renaming

// Nested destructuring
const company = {
  name: 'TechCorp',
  address: {
    street: '123 Main St',
    city: 'San Francisco'
  }
};

const { address: { street, city: companyCity } } = company;
```

### Object Methods and Properties
```javascript
const user = {
  firstName: 'John',
  lastName: 'Doe',
  
  // Getter
  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  },
  
  // Setter
  set fullName(value) {
    [this.firstName, this.lastName] = value.split(' ');
  }
};

console.log(user.fullName); // "John Doe"
user.fullName = 'Jane Smith';
console.log(user.firstName); // "Jane"

// Object methods
const obj = { a: 1, b: 2, c: 3 };

console.log(Object.keys(obj)); // ['a', 'b', 'c']
console.log(Object.values(obj)); // [1, 2, 3]
console.log(Object.entries(obj)); // [['a', 1], ['b', 2], ['c', 3]]

// Object.assign (shallow copy)
const target = { a: 1 };
const source = { b: 2, c: 3 };
Object.assign(target, source); // target is now { a: 1, b: 2, c: 3 }

// Spread operator (shallow copy)
const copy = { ...obj, d: 4 }; // { a: 1, b: 2, c: 3, d: 4 }

// Object.freeze, Object.seal
const frozen = Object.freeze({ name: 'Frozen' });
// frozen.name = 'New Name'; // This won't work

const sealed = Object.seal({ name: 'Sealed' });
sealed.name = 'New Name'; // This works
// sealed.age = 25; // This won't work
```

### Prototypes and Inheritance
```javascript
// Constructor function
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Adding method to prototype
Person.prototype.greet = function() {
  return `Hello, I'm ${this.name}`;
};

Person.prototype.getAge = function() {
  return this.age;
};

// Creating instances
const person1 = new Person('Alice', 25);
const person2 = new Person('Bob', 30);

console.log(person1.greet()); // "Hello, I'm Alice"
console.log(person2.getAge()); // 30

// Prototype chain
console.log(person1.__proto__ === Person.prototype); // true
console.log(Person.prototype.__proto__ === Object.prototype); // true

// Inheritance with constructor functions
function Developer(name, age, language) {
  Person.call(this, name, age); // Call parent constructor
  this.language = language;
}

// Set up inheritance
Developer.prototype = Object.create(Person.prototype);
Developer.prototype.constructor = Developer;

// Add method specific to Developer
Developer.prototype.code = function() {
  return `${this.name} is coding in ${this.language}`;
};

const dev = new Developer('Charlie', 28, 'JavaScript');
console.log(dev.greet()); // "Hello, I'm Charlie"
console.log(dev.code()); // "Charlie is coding in JavaScript"
```

### ES6 Classes
```javascript
// Class declaration
class Animal {
  constructor(name, species) {
    this.name = name;
    this.species = species;
  }
  
  // Method
  speak() {
    return `${this.name} makes a sound`;
  }
  
  // Static method
  static getKingdom() {
    return 'Animalia';
  }
  
  // Getter
  get info() {
    return `${this.name} is a ${this.species}`;
  }
  
  // Setter
  set nickname(value) {
    this._nickname = value;
  }
  
  get nickname() {
    return this._nickname || this.name;
  }
}

// Inheritance with extends
class Dog extends Animal {
  constructor(name, breed) {
    super(name, 'Dog'); // Call parent constructor
    this.breed = breed;
  }
  
  // Override parent method
  speak() {
    return `${this.name} barks`;
  }
  
  // Additional method
  wagTail() {
    return `${this.name} wags tail happily`;
  }
}

const dog = new Dog('Buddy', 'Golden Retriever');
console.log(dog.speak()); // "Buddy barks"
console.log(dog.info); // "Buddy is a Dog"
console.log(Animal.getKingdom()); // "Animalia"

// Class expressions
const Cat = class {
  constructor(name) {
    this.name = name;
  }
  
  meow() {
    return `${this.name} says meow`;
  }
};

// Private fields and methods (ES2022)
class BankAccount {
  #balance = 0; // Private field
  
  constructor(initialBalance) {
    this.#balance = initialBalance;
  }
  
  // Private method
  #validateAmount(amount) {
    return amount > 0;
  }
  
  deposit(amount) {
    if (this.#validateAmount(amount)) {
      this.#balance += amount;
    }
  }
  
  getBalance() {
    return this.#balance;
  }
}

const account = new BankAccount(1000);
account.deposit(500);
console.log(account.getBalance()); // 1500
// console.log(account.#balance); // SyntaxError: Private field '#balance' must be declared in an enclosing class
```

---

## 📚 Arrays and Array Methods

### Array Creation and Basic Operations
```javascript
// Array creation
const fruits = ['apple', 'banana', 'orange'];
const numbers = new Array(1, 2, 3, 4, 5);
const emptyArray = [];
const arrayWithLength = new Array(5); // Creates array with 5 empty slots

// Array properties
console.log(fruits.length); // 3
console.log(Array.isArray(fruits)); // true

// Accessing elements
console.log(fruits[0]); // 'apple'
console.log(fruits[fruits.length - 1]); // 'orange'

// Modifying arrays
fruits[1] = 'grape'; // ['apple', 'grape', 'orange']
fruits[fruits.length] = 'kiwi'; // Add to end
```

### Mutating Array Methods
```javascript
let numbers = [1, 2, 3];

// push() - add to end
numbers.push(4, 5); // [1, 2, 3, 4, 5]

// pop() - remove from end
let last = numbers.pop(); // 5, numbers = [1, 2, 3, 4]

// unshift() - add to beginning
numbers.unshift(0); // [0, 1, 2, 3, 4]

// shift() - remove from beginning
let first = numbers.shift(); // 0, numbers = [1, 2, 3, 4]

// splice() - add/remove elements at any position
let removed = numbers.splice(1, 2, 'a', 'b'); // [2, 3], numbers = [1, 'a', 'b', 4]

// reverse() - reverse array in place
numbers.reverse(); // [4, 'b', 'a', 1]

// sort() - sort array in place
let words = ['banana', 'apple', 'cherry'];
words.sort(); // ['apple', 'banana', 'cherry']

// Custom sort
let nums = [10, 5, 40, 25, 1000, 1];
nums.sort((a, b) => a - b); // [1, 5, 10, 25, 40, 1000]
nums.sort((a, b) => b - a); // [1000, 40, 25, 10, 5, 1] (descending)
```

### Non-Mutating Array Methods
```javascript
let original = [1, 2, 3, 4, 5];

// concat() - combine arrays
let combined = original.concat([6, 7], [8, 9]); // [1, 2, 3, 4, 5, 6, 7, 8, 9]

// slice() - extract portion
let portion = original.slice(1, 4); // [2, 3, 4]
let fromIndex = original.slice(2); // [3, 4, 5]
let lastTwo = original.slice(-2); // [4, 5]

// join() - create string from array
let joined = original.join(' - '); // "1 - 2 - 3 - 4 - 5"

// indexOf() and lastIndexOf()
let fruits = ['apple', 'banana', 'apple', 'orange'];
console.log(fruits.indexOf('apple')); // 0
console.log(fruits.lastIndexOf('apple')); // 2
console.log(fruits.indexOf('grape')); // -1 (not found)

// includes() - check if element exists
console.log(fruits.includes('banana')); // true
console.log(fruits.includes('grape')); // false
```

### Functional Array Methods
```javascript
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// forEach() - execute function for each element
numbers.forEach((num, index) => {
  console.log(`Index ${index}: ${num}`);
});

// map() - transform each element
let doubled = numbers.map(num => num * 2); // [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
let squares = numbers.map(num => num ** 2); // [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

// filter() - select elements based on condition
let evens = numbers.filter(num => num % 2 === 0); // [2, 4, 6, 8, 10]
let greaterThanFive = numbers.filter(num => num > 5); // [6, 7, 8, 9, 10]

// find() - find first matching element
let firstEven = numbers.find(num => num % 2 === 0); // 2
let firstGreaterThanFive = numbers.find(num => num > 5); // 6

// findIndex() - find index of first matching element
let firstEvenIndex = numbers.findIndex(num => num % 2 === 0); // 1

// some() - check if at least one element matches
let hasEven = numbers.some(num => num % 2 === 0); // true
let hasNegative = numbers.some(num => num < 0); // false

// every() - check if all elements match
let allPositive = numbers.every(num => num > 0); // true
let allEven = numbers.every(num => num % 2 === 0); // false

// reduce() - reduce array to single value
let sum = numbers.reduce((acc, num) => acc + num, 0); // 55
let product = numbers.reduce((acc, num) => acc * num, 1); // 3628800

// reduceRight() - reduce from right to left
let concatenated = ['a', 'b', 'c'].reduceRight((acc, char) => acc + char, ''); // "cba"

// Complex reduce examples
let people = [
  { name: 'John', age: 30 },
  { name: 'Jane', age: 25 },
  { name: 'Bob', age: 35 }
];

let totalAge = people.reduce((sum, person) => sum + person.age, 0); // 90
let nameMap = people.reduce((map, person) => {
  map[person.name] = person.age;
  return map;
}, {}); // { John: 30, Jane: 25, Bob: 35 }

// Chaining array methods
let processedNumbers = numbers
  .filter(num => num % 2 === 0)  // Get even numbers
  .map(num => num * 3)           // Multiply by 3
  .filter(num => num > 10)       // Keep only > 10
  .sort((a, b) => b - a);        // Sort descending
// Result: [30, 24, 18, 12]
```

### Advanced Array Operations
```javascript
// Array destructuring
let [first, second, ...rest] = [1, 2, 3, 4, 5];
console.log(first); // 1
console.log(second); // 2
console.log(rest); // [3, 4, 5]

// Skipping elements
let [a, , c] = [1, 2, 3];
console.log(a, c); // 1, 3

// Default values
let [x, y, z = 0] = [1, 2];
console.log(z); // 0

// Swapping variables
let var1 = 'hello';
let var2 = 'world';
[var1, var2] = [var2, var1];
console.log(var1, var2); // 'world', 'hello'

// Spread operator with arrays
let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];
let combined = [...arr1, ...arr2]; // [1, 2, 3, 4, 5, 6]
let copy = [...arr1]; // [1, 2, 3]

// Array.from() - create array from iterable
let arrayFromString = Array.from('hello'); // ['h', 'e', 'l', 'l', 'o']
let arrayFromSet = Array.from(new Set([1, 2, 2, 3])); // [1, 2, 3]

// Array.from() with mapping function
let doubled = Array.from([1, 2, 3], x => x * 2); // [2, 4, 6]

// Array.of() - create array from arguments
let created = Array.of(1, 2, 3); // [1, 2, 3]

// flat() - flatten nested arrays
let nested = [1, [2, 3], [4, [5, 6]]];
console.log(nested.flat()); // [1, 2, 3, 4, [5, 6]]
console.log(nested.flat(2)); // [1, 2, 3, 4, 5, 6] (depth 2)

// flatMap() - map then flat
let sentences = ['Hello world', 'How are you'];
let words = sentences.flatMap(sentence => sentence.split(' '));
// ['Hello', 'world', 'How', 'are', 'you']
```

---

## 🔤 Strings and String Methods

### String Creation and Properties
```javascript
// String creation
let singleQuotes = 'Hello';
let doubleQuotes = "World";
let templateLiteral = `Hello ${doubleQuotes}!`;
let stringObject = new String('Hello'); // Avoid this

// String properties
console.log('Hello'.length); // 5

// String immutability
let str = 'Hello';
str[0] = 'h'; // This doesn't work
console.log(str); // Still "Hello"
```

### String Methods

#### Character and Position Methods
```javascript
let text = 'JavaScript';

// charAt() - character at index
console.log(text.charAt(0)); // 'J'
console.log(text.charAt(4)); // 'S'

// charCodeAt() - character code at index
console.log(text.charCodeAt(0)); // 74 (ASCII code for 'J')

// indexOf() - find first occurrence
console.log(text.indexOf('S')); // 4
console.log(text.indexOf('Script')); // 4
console.log(text.indexOf('Python')); // -1 (not found)

// lastIndexOf() - find last occurrence
console.log('JavaScript JavaScript'.lastIndexOf('Script')); // 15

// includes() - check if substring exists
console.log(text.includes('Script')); // true
console.log(text.includes('Python')); // false

// startsWith() and endsWith()
console.log(text.startsWith('Java')); // true
console.log(text.endsWith('Script')); // true
```

#### Extraction Methods
```javascript
let phrase = 'The quick brown fox';

// substring() - extract between two indices
console.log(phrase.substring(4, 9)); // 'quick'
console.log(phrase.substring(4)); // 'quick brown fox'

// substr() - extract from index with length (deprecated)
console.log(phrase.substr(4, 5)); // 'quick'

// slice() - extract portion (supports negative indices)
console.log(phrase.slice(4, 9)); // 'quick'
console.log(phrase.slice(-3)); // 'fox'
console.log(phrase.slice(-7, -4)); // 'own'
```

#### Transformation Methods
```javascript
let text = '  Hello World  ';

// Case transformation
console.log(text.toLowerCase()); // '  hello world  '
console.log(text.toUpperCase()); // '  HELLO WORLD  '

// Trimming
console.log(text.trim()); // 'Hello World'
console.log(text.trimStart()); // 'Hello World  '
console.log(text.trimEnd()); // '  Hello World'

// Replacement
let sentence = 'The quick brown fox jumps over the lazy dog';
console.log(sentence.replace('quick', 'slow')); // 'The slow brown fox...'
console.log(sentence.replaceAll('the', 'a')); // 'The quick brown fox jumps over a lazy dog'

// Using regex with replace
console.log(sentence.replace(/the/gi, 'a')); // 'a quick brown fox jumps over a lazy dog'

// Padding
let num = '5';
console.log(num.padStart(3, '0')); // '005'
console.log(num.padEnd(3, '0')); // '500'

// Repeat
console.log('Ha'.repeat(3)); // 'HaHaHa'
```

#### Split and Join
```javascript
let csv = 'apple,banana,orange,grape';
let fruits = csv.split(','); // ['apple', 'banana', 'orange', 'grape']

let sentence = 'The quick brown fox';
let words = sentence.split(' '); // ['The', 'quick', 'brown', 'fox']
let chars = sentence.split(''); // ['T', 'h', 'e', ' ', 'q', ...]

// Join arrays back to strings
console.log(fruits.join(' | ')); // 'apple | banana | orange | grape'
console.log(words.join('')); // 'Thequickbrownfox'
```

### Template Literals
```javascript
let name = 'Alice';
let age = 25;

// Basic interpolation
let greeting = `Hello, my name is ${name} and I am ${age} years old.`;

// Multi-line strings
let multiLine = `
  This is a
  multi-line
  string.
`;

// Expression evaluation
let calculation = `The result is: ${10 + 5}`;
let comparison = `Is adult: ${age >= 18}`;

// Nested template literals
let nested = `Hello ${name}, you are ${age >= 18 ? 'an adult' : 'a minor'}.`;

// Tagged template literals
function highlight(strings, ...values) {
  return strings.reduce((result, string, i) => {
    const value = values[i] ? `<mark>${values[i]}</mark>` : '';
    return result + string + value;
  }, '');
}

let highlighted = highlight`Hello ${name}, you are ${age} years old.`;
// "Hello <mark>Alice</mark>, you are <mark>25</mark> years old."
```

### Regular Expressions with Strings
```javascript
let text = 'The price is $25.99 and tax is $3.25';

// test() - check if pattern exists
let hasPrice = /\$\d+\.\d+/.test(text); // true

// match() - find matches
let prices = text.match(/\$\d+\.\d+/g); // ['$25.99', '$3.25']

// search() - find index of first match
let priceIndex = text.search(/\$\d+\.\d+/); // 13

// replace() with regex
let withoutPrices = text.replace(/\$\d+\.\d+/g, '[PRICE]');
// 'The price is [PRICE] and tax is [PRICE]'

// split() with regex
let splitByNumbers = 'abc123def456ghi'.split(/\d+/); // ['abc', 'def', 'ghi']

// matchAll() - get all matches with details
let emailText = 'Contact: john@email.com or jane@email.com';
let emailRegex = /([a-zA-Z]+)@([a-zA-Z]+\.[a-zA-Z]+)/g;

for (let match of emailText.matchAll(emailRegex)) {
  console.log(`Full: ${match[0]}, Name: ${match[1]}, Domain: ${match[2]}`);
}
```

### String Comparison and Localization
```javascript
// Basic comparison
console.log('a' < 'b'); // true
console.log('apple' < 'banana'); // true

// Locale-aware comparison
let fruits = ['ä', 'a', 'z'];
fruits.sort(); // ['a', 'z', 'ä'] - not ideal for German

fruits.sort((a, b) => a.localeCompare(b, 'de')); // ['a', 'ä', 'z'] - correct German order

// Case-insensitive comparison
function caseInsensitiveCompare(a, b) {
  return a.toLowerCase().localeCompare(b.toLowerCase());
}

// String normalization
let str1 = '\u00e9'; // é (single character)
let str2 = 'e\u0301'; // é (e + combining accent)
console.log(str1 === str2); // false
console.log(str1.normalize() === str2.normalize()); // true
```

---

## 🔍 Scope and Closures

### Understanding Scope
```javascript
// Global scope
var globalVar = 'I am global';
let globalLet = 'I am also global';
const globalConst = 'I am global too';

function demonstrateScope() {
  // Function scope
  var functionScoped = 'I am function scoped';
  
  if (true) {
    // Block scope
    var varInBlock = 'I am still function scoped'; // var ignores block scope
    let letInBlock = 'I am block scoped';
    const constInBlock = 'I am also block scoped';
    
    console.log(letInBlock); // Accessible here
  }
  
  console.log(varInBlock); // Accessible here
  // console.log(letInBlock); // ReferenceError: not accessible here
  // console.log(constInBlock); // ReferenceError: not accessible here
}

// Lexical scoping
function outerFunction(x) {
  // Outer function scope
  
  function innerFunction(y) {
    // Inner function has access to outer function's variables
    return x + y; // x is from outer scope
  }
  
  return innerFunction;
}

const addToFive = outerFunction(5);
console.log(addToFive(3)); // 8
```

### Closures
```javascript
// Basic closure
function createCounter() {
  let count = 0;
  
  return function() {
    count++;
    return count;
  };
}

const counter1 = createCounter();
const counter2 = createCounter();

console.log(counter1()); // 1
console.log(counter1()); // 2
console.log(counter2()); // 1 (separate closure)
console.log(counter1()); // 3

// Closure with parameters
function createMultiplier(multiplier) {
  return function(number) {
    return number * multiplier;
  };
}

const double = createMultiplier(2);
const triple = createMultiplier(3);

console.log(double(5)); // 10
console.log(triple(4)); // 12

// Module pattern using closures
const calculator = (function() {
  let result = 0;
  
  return {
    add: function(x) {
      result += x;
      return this;
    },
    subtract: function(x) {
      result -= x;
      return this;
    },
    multiply: function(x) {
      result *= x;
      return this;
    },
    divide: function(x) {
      result /= x;
      return this;
    },
    getResult: function() {
      return result;
    },
    reset: function() {
      result = 0;
      return this;
    }
  };
})();

// Method chaining
const finalResult = calculator
  .add(10)
  .multiply(2)
  .subtract(5)
  .getResult(); // 15

// Private variables with closures
function Person(name, age) {
  // Private variables
  let _name = name;
  let _age = age;
  
  // Public interface
  return {
    getName: function() {
      return _name;
    },
    setName: function(newName) {
      if (typeof newName === 'string' && newName.length > 0) {
        _name = newName;
      }
    },
    getAge: function() {
      return _age;
    },
    setAge: function(newAge) {
      if (typeof newAge === 'number' && newAge >= 0) {
        _age = newAge;
      }
    },
    greet: function() {
      return `Hello, I'm ${_name} and I'm ${_age} years old.`;
    }
  };
}

const person = Person('John', 30);
console.log(person.getName()); // 'John'
person.setName('Jane');
console.log(person.greet()); // "Hello, I'm Jane and I'm 30 years old."
// console.log(person._name); // undefined - private variable not accessible
```

### Practical Closure Examples
```javascript
// Debouncing with closures
function debounce(func, delay) {
  let timeoutId;
  
  return function(...args) {
    clearTimeout(timeoutId);
    timeoutId = setTimeout(() => func.apply(this, args), delay);
  };
}

const debouncedSearch = debounce(function(query) {
  console.log(`Searching for: ${query}`);
}, 300);

// Throttling with closures
function throttle(func, limit) {
  let inThrottle;
  
  return function(...args) {
    if (!inThrottle) {
      func.apply(this, args);
      inThrottle = true;
      setTimeout(() => inThrottle = false, limit);
    }
  };
}

const throttledScroll = throttle(function() {
  console.log('Scrolling...');
}, 100);

// Memoization with closures
function memoize(fn) {
  const cache = {};
  
  return function(...args) {
    const key = JSON.stringify(args);
    
    if (key in cache) {
      return cache[key];
    }
    
    const result = fn.apply(this, args);
    cache[key] = result;
    return result;
  };
}

const memoizedFactorial = memoize(function factorial(n) {
  if (n <= 1) return 1;
  return n * factorial(n - 1);
});

// Function factory with closures
function createValidator(rules) {
  return function(value) {
    for (let rule of rules) {
      if (!rule.test(value)) {
        return { valid: false, message: rule.message };
      }
    }
    return { valid: true };
  };
}

const emailValidator = createValidator([
  {
    test: (value) => value.length > 0,
    message: 'Email is required'
  },
  {
    test: (value) => value.includes('@'),
    message: 'Email must contain @'
  },
  {
    test: (value) => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value),
    message: 'Email format is invalid'
  }
]);

console.log(emailValidator('test@example.com')); // { valid: true }
console.log(emailValidator('invalid-email')); // { valid: false, message: '...' }
```

---

## ⏰ Asynchronous JavaScript

### Callbacks
```javascript
// Basic callback
function fetchData(callback) {
  setTimeout(() => {
    const data = { id: 1, name: 'John' };
    callback(data);
  }, 1000);
}

fetchData((data) => {
  console.log('Received data:', data);
});

// Callback with error handling
function fetchDataWithError(callback) {
  setTimeout(() => {
    const success = Math.random() > 0.5;
    
    if (success) {
      callback(null, { id: 1, name: 'John' });
    } else {
      callback(new Error('Failed to fetch data'), null);
    }
  }, 1000);
}

fetchDataWithError((error, data) => {
  if (error) {
    console.error('Error:', error.message);
  } else {
    console.log('Data:', data);
  }
});

// Callback hell example
function step1(callback) {
  setTimeout(() => callback(null, 'Step 1 complete'), 1000);
}

function step2(callback) {
  setTimeout(() => callback(null, 'Step 2 complete'), 1000);
}

function step3(callback) {
  setTimeout(() => callback(null, 'Step 3 complete'), 1000);
}

// This becomes hard to read and maintain
step1((err, result1) => {
  if (err) return console.error(err);
  console.log(result1);
  
  step2((err, result2) => {
    if (err) return console.error(err);
    console.log(result2);
    
    step3((err, result3) => {
      if (err) return console.error(err);
      console.log(result3);
      console.log('All steps completed!');
    });
  });
});
```

### Promises
```javascript
// Creating a Promise
function fetchUser(id) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (id > 0) {
        resolve({ id: id, name: `User ${id}` });
      } else {
        reject(new Error('Invalid user ID'));
      }
    }, 1000);
  });
}

// Using Promises
fetchUser(1)
  .then(user => {
    console.log('User:', user);
    return fetchUser(2); // Return another promise
  })
  .then(user => {
    console.log('Another user:', user);
  })
  .catch(error => {
    console.error('Error:', error.message);
  })
  .finally(() => {
    console.log('Promise chain completed');
  });

// Promise.all() - wait for all promises
const promise1 = fetchUser(1);
const promise2 = fetchUser(2);
const promise3 = fetchUser(3);

Promise.all([promise1, promise2, promise3])
  .then(users => {
    console.log('All users:', users);
  })
  .catch(error => {
    console.error('At least one promise failed:', error);
  });

// Promise.allSettled() - wait for all promises (success or failure)
Promise.allSettled([promise1, promise2, fetchUser(-1)])
  .then(results => {
    results.forEach((result, index) => {
      if (result.status === 'fulfilled') {
        console.log(`Promise ${index} succeeded:`, result.value);
      } else {
        console.log(`Promise ${index} failed:`, result.reason);
      }
    });
  });

// Promise.race() - first promise to resolve/reject
Promise.race([
  new Promise(resolve => setTimeout(() => resolve('Fast'), 100)),
  new Promise(resolve => setTimeout(() => resolve('Slow'), 1000))
])
.then(result => {
  console.log('Winner:', result); // "Fast"
});

// Promise.any() - first promise to fulfill
Promise.any([
  Promise.reject('Error 1'),
  new Promise(resolve => setTimeout(() => resolve('Success'), 100)),
  Promise.reject('Error 2')
])
.then(result => {
  console.log('First success:', result); // "Success"
})
.catch(error => {
  console.error('All promises rejected:', error);
});

// Promise utility functions
Promise.resolve('Immediate value').then(console.log);
Promise.reject(new Error('Immediate error')).catch(console.error);
```

### Async/Await
```javascript
// Basic async/await
async function fetchUserAsync(id) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (id > 0) {
        resolve({ id: id, name: `User ${id}` });
      } else {
        reject(new Error('Invalid user ID'));
      }
    }, 1000);
  });
}

async function getUserData() {
  try {
    const user1 = await fetchUserAsync(1);
    console.log('User 1:', user1);
    
    const user2 = await fetchUserAsync(2);
    console.log('User 2:', user2);
    
    return [user1, user2];
  } catch (error) {
    console.error('Error:', error.message);
    throw error; // Re-throw if needed
  }
}

// Using async function
getUserData()
  .then(users => console.log('All users retrieved:', users))
  .catch(error => console.error('Failed to get users'));

// Parallel execution with async/await
async function fetchUsersParallel() {
  try {
    // Start all requests simultaneously
    const userPromises = [
      fetchUserAsync(1),
      fetchUserAsync(2),
      fetchUserAsync(3)
    ];
    
    // Wait for all to complete
    const users = await Promise.all(userPromises);
    console.log('All users (parallel):', users);
    
    return users;
  } catch (error) {
    console.error('One or more requests failed:', error);
  }
}

// Sequential vs Parallel execution
async function sequentialExecution() {
  const start = Date.now();
  
  const user1 = await fetchUserAsync(1); // Wait 1 second
  const user2 = await fetchUserAsync(2); // Wait another 1 second
  const user3 = await fetchUserAsync(3); // Wait another 1 second
  
  console.log(`Sequential took: ${Date.now() - start}ms`); // ~3000ms
  return [user1, user2, user3];
}

async function parallelExecution() {
  const start = Date.now();
  
  const [user1, user2, user3] = await Promise.all([
    fetchUserAsync(1), // All start simultaneously
    fetchUserAsync(2),
    fetchUserAsync(3)
  ]);
  
  console.log(`Parallel took: ${Date.now() - start}ms`); // ~1000ms
  return [user1, user2, user3];
}
```

### Advanced Async Patterns
```javascript
// Async generators
async function* numberGenerator() {
  for (let i = 1; i <= 5; i++) {
    await new Promise(resolve => setTimeout(resolve, 1000));
    yield i;
  }
}

async function consumeNumbers() {
  for await (const number of numberGenerator()) {
    console.log('Generated number:', number);
  }
}

// Promise-based timeout
function timeout(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function withTimeout(promise, ms) {
  const timeoutPromise = timeout(ms).then(() => {
    throw new Error(`Operation timed out after ${ms}ms`);
  });
  
  return Promise.race([promise, timeoutPromise]);
}

// Usage
withTimeout(fetchUserAsync(1), 500)
  .then(user => console.log('User fetched in time:', user))
  .catch(error => console.error('Error:', error.message));

// Retry mechanism
async function withRetry(operation, maxRetries = 3, delay = 1000) {
  let lastError;
  
  for (let attempt = 1; attempt <= maxRetries; attempt++) {
    try {
      return await operation();
    } catch (error) {
      lastError = error;
      
      if (attempt === maxRetries) {
        throw new Error(`Operation failed after ${maxRetries} attempts: ${error.message}`);
      }
      
      console.log(`Attempt ${attempt} failed, retrying in ${delay}ms...`);
      await timeout(delay);
    }
  }
}

// Usage
const unreliableOperation = () => {
  return new Promise((resolve, reject) => {
    if (Math.random() > 0.7) {
      resolve('Success!');
    } else {
      reject(new Error('Random failure'));
    }
  });
};

withRetry(unreliableOperation, 5, 1000)
  .then(result => console.log('Eventually succeeded:', result))
  .catch(error => console.error('Gave up:', error.message));

// Queue with concurrency limit
class AsyncQueue {
  constructor(concurrency = 1) {
    this.concurrency = concurrency;
    this.running = 0;
    this.queue = [];
  }
  
  async add(task) {
    return new Promise((resolve, reject) => {
      this.queue.push({
        task,
        resolve,
        reject
      });
      
      this.process();
    });
  }
