# Study Guide: JS109 #

## Declarations, initialization, assingment, and re-assignment ##
**What is a variable?**
- A named area of a program's memory where data can be stored

**Declarations**
- A variable declaration is a statement that asks the JavaScript egnine to reserve space for a variable (that has a particular name)
  - Declarations are made with the let and const keywords
  - "let" is used for variables, "const" for constants
  - Notice that an initalizer must be specified for constant declarations, but not for variable declarations

  ```javascript
  let variable;
  const constant = 1;
  ```
**NOTE: Variables for 109 exam**: 
- variables declared with let or const
- function parameters
- function names

**NOTE: Object Properties are NOT variables**                                 
                                
**Initialization**
- Initalization is the storing of a value inside of a variable at declaration. If an initalizer is not specified at time of declaration, variable is initalized to value of undefined
  - As mentioned above, constants must be initalized with a value at declaration
  - Variables can be initalized with a value or without

 ```javascript
  let num; // This is a variable declaration initalized to a value of undefined
  let number = 1; // This is a variable declaration initalized with a value of 1;
  const constant = 1; // This is a constant declaration initalized to a value of 1
  ```
  
  **NOTE: INITALIZATIONS AND DECLARATIONS**
   - Variable declarations always return a value of undefined, regardless of whether or not they are provided an initial value (initializer)
  ```javascript
  let num; // Returns undefined
  let number = 5; // Returns UNdefined
 ```
**Assignment**
- A value that is supplied to a variable after the initialilzation

**Reassignment**
- A variable assignment that takes place on a variable that has been initalized with or assigned a value previously.
 ```javascript
 let num; // variable declaration
 let number = 5; // variable delcaration with an initializer of 5
 number = 5; // Assignment of the value 5 to variable "number" 
 number = 3; // Reassignment of the value 3 to the variable "number"
 ```
 **NOTE: When using '=' in the context of a vriable assignment, it is called an assignment operator**
 
 ## Variable Scope ##
 - A variable's scope determines where it is available in a program
 - Depends on the scope in which the variable is declared
 **Block scope**
 - Variables declared with let and const have block scope
 - A block is a set of JS statements between a pair of curly braces
 - Generally seen in if...else, while, do...while, for, switch, and try...catch statements
 ```javascript
 if (iLovePie) {
   eatPie(); // This space between the braces is the block. eatPie function lives here currently
}
 ```
**NOTE: Not all statements between curly braces are technically blocks i.e function body, object literal etc.**
```javascript
function foo() {
  console.log('foo'); // This is a function body. It technically has function scope, not block scope. They act very similar however.
}

let bar = {
  foo: 'bar'; // This is not a block  
}
```
- Variables with block scope cannot be accessed outside of their scope
```javascript
if (something === true) {
  let answer = 'this is true';
}
console.log(answer) // This will throw a reference error as answer is not visible to the outer scope that console.log(answer) is in
```
- An example where answer would be accessible
```javascript
let a = 0;
if (1 === 1) {
  a = 5;
}
console.log(a); 
// This print 5 as 'a' is declared within the same scope as the log statment. 
// 'a' is accessible within the block of the if statement as it was declared in an outer scope. 
// 'a' is then reassigned since the condition evaluates to true, then printed.
```
**Global Scope**
- The outermost scope of a program
- Variable declared here are called *Global Variables*
- Global Variables are accessible throughout the entire program (below where they are declared)

**Local Scope**
- The scope of a function or block
- Variables declared here are called *Local Variables*
- Local variables are not accessible to the outer scope
```javascript
let globalVar = 5
function changeVar() {
  console.log(globalVar); // Doesn't need to take argument since global var is accessible within the local scope of the function
}
changeVar(); // Prints 5

function changeVarLocal() {
  let num = 5;
  console.log(num);
}
changeVarLocal(); // Prints 5 as well, but doesn't use any global variables 
```
## Primitive alues, objects, and type coercions ##

**Primitive Data Types**
- String --> list of characters in sequence (typically used to represent text)
- Number --> represents all types of numbers in javaScript (int, float, fixed)
- Bool --> represents an "on" or "off" state, can also be used for evaluation of logical "true" or "false"
- Undefined --> represents the absence of a value. Can be implicit or used in a literal.
- Null --> same as undefined, but MUST be used as a literal. Cannot be implicitly returned.
- BigInt --> represents larger numbers than Number
- Symbol --> Don't know what this does

**Object Data Types**
- Simple Object --> A collection of key value pairs
- Array --> an ordered list of data types (do not have to be same data type)
- Functions --> A named, extracted unit of code that can be executed repeatedly throughout a program
- Dates

*These data types can be represented as literals*
- A literal is any notation that lets you represent a fixed value in source code
```javascript
'I am the man'             // string literal
12345                      // numeric literal
{name: 'Brandon', age: 23} // object literal
true                       // boolean literal
[1, 2, 3]                  // array literal
undefined                  // undefined literal
```

**Explicit Coercion**
- When the programmer intentionally changes one data type to another
- This can be done using functions
```javascript
Number('69'); // Coerces the string '69' to the number 69
Number('peanutbutter'); // Coerces string 'peanutbutter' to number NaN
String(20); // Coerces number 20 to string '20'
```
**Implicit Coercion**
- When the JavaScript engine coerces one data type to another
```javascript
10 + 'peanutbutter'; // Coerces number 10 to string '10' and then concatenates with peanutbutter --> '10peanutbutter'
true * 5; // true is coerced to number 1 and then multiplied by 5 --> 5
'123' == 123; // '123' is coerced to 123 number due to loose equality operator
if ('randomtruthy') console.log('hello'); // All values are coerced to boolean within conditional statements based on truthiness of the value
```

## Object Properties ##
- An object property is a named key that can be used to access an associated value
- An onjects properties are always strings or symbols, but the values can be any type
- Despite the fact that keys are strings, they do not need quotations, the JS engine knows what you mean.
*Accessing Properties*
- Can be done two ways
```javascript
person.name;
person['age'];
```
- If using a variable as the key name, it MUST be done with a bracket opposed to a dot
```javascript
let name = 'Brandon';
person[name];
```

## Mutability vs Immutability vs const. ##
**Mutable** --> Able to add, remove, or change various component values of an object (only objects, primitives are NOT mutable)

**Immutable** --> Unable to add, remove, or change components of data type (primitive OR object)
  - Primitives always immutable
  - Can only be reassigned or given an entirely new value
  - All operations on primitive values evaluate as new values, even if the resulting value is the same (0 + 0)

```javascript
let x = 5;
let y = x + 1;
console.log(x); // 5

let obj = {a: 1, b: 2}
obj.c = 3;
console.log(obj) // {a: 1, b: 2, c: 3}
```
**const** --> const variables are NOT allowed to be reassigned, they ARE allowed to be mutates
```javascript
const x = 5;
x = 3; // TypeError: reassignment to constant variable

const arr = [ 1, 2, 3 ];
arr[0] = `ba${0/0}na`.toLowerCase();

console.log(arr) // [ 'banana', 2, 3 ];

arr = 'brandon'; // TypeError: reassignment to a constant variable
```
