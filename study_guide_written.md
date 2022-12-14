# Study Guide: JS109 #

## General Guidance ##
- What does the code output
  - **Side Effects?**
  - **Return value? (Always a return value for functions/methods)**
- What **concept** does the code demonstrate?

**Variable vocab check**
- Declaration
- Initalization
- Initializer (value that variable is initalized with)
- Assignment
- Reassiment


- When talking about methods called on primitives stored in variables, say:
  - "The method (method name) is called by the primitive (insert value) stored in (insert variable name)
- When talking about methods called on objects stored in variables, say:
  - "The method (method name) is called on the object referenced by (insert variable name)

**Function vocab check**
- Definition (using either declaration or expression or arrow expression)
- Declaration
- Argument (values/references passed to function wyhen called)
- Parameters(local variables defined in function definition)
- Function body (instead of code block)
- Function scope (instead of block scope)
- Variables are not passed to or returned by functions: values or references are passed.
- Invocation or call\

**Key Word vocab check**
- Conditional statements are **defined**
- Loops are **defined**
- Statements in general, which are denoted by key words, are **DEFINED**

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
- The scope within a code block or function body
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

## Primitive values, objects, and type coercions ##

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
- If using non-strict or relational operators, operands of different types will always be converted to numbers before being compared
```javascript
10 + 'peanutbutter'; // Coerces number 10 to string '10' and then concatenates with peanutbutter --> '10peanutbutter'
true * 5; // true is coerced to number 1 and then multiplied by 5 --> 5
true > null;    // true -- becomes 1 > 0
undefined >= 1; // false -- becomes NaN >= 1
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
**Mutable** --> Able to add, remove, or change various component values of an object (only objects)

**Immutable** --> Unable to add, remove, or change components of data type (primitive OR object)
  - Primitives are always immutable
    - Can only be reassigned or given an entirely new value
    - All operations performed on primitive values evaluate as new values, even if the resulting value is the same (0 + 0)

```javascript
let x = 5;
let y = x + 1;
console.log(x); // 5

let obj = { a: 1, b: 2 };
obj.c = 3;
console.log(obj); // { a: 1, b: 2, c: 3 }
```
**const** --> const variables are NOT allowed to be reassigned, they ARE allowed to be mutated
```javascript
const x = 5;
x = 3; // TypeError: reassignment to constant variable

const arr = [ 1, 2, 3 ];
arr[0]; = `ba${0/0}na`.toLowerCase();

console.log(arr); // [ 'banana', 2, 3 ];

arr = 'brandon'; // TypeError: reassignment to a constant variable
```

## Loose and Strict equality ##
**Strict Equality Operator**: === *Returns true when two operands have the same type *and* value*
```javascript
1 === 1; // true
1 === '1'; //false
'abc' == 'aBc'; // false
1 === true; // false
```

**Loose Equality Operator**: == *When operands have differnt types, will coerce one or both operands to the same type before comparing*
 - Booleans and strings are always coerced to numbers if compared to a number using loose equality
```javascript
1 == '1'; // true ('1' is coerced to 1, then strictly compared)
1 == true; // true (true is coerced to 1, then strictly compared)
'1' == true; // true ('1' is coerced to 1, true is coerced to 1, then strictly compared)
'1' == 'true'; //false (Neither value is coerced as they are same type. So '1' and 'true' are stictly compared)
```

## Passing arguments into and return values out of functions ##
**Arguments** - Values that are passed into a function when the function is called
**Parameters** - The names defined within the parenthesis of the function definition
  - Parameters are _local variables_
  - The arguments passed into the function become the values of the parameters when the function is called

```javascript
function add(a, b) { // This part is the definition with the parameters
  return a + b;
}

add(5, 4); // 9 is the value returned, 5 and 4 are the arugments
```

**Return values**
- Returns a result to the call location of the function
- Functions have implicit or explicit return values. Implicit value is undefined by default
- The `return` key word creates a return statement that can be used to explicity return a value from a function
  - Functions that always return a boolean value are called _Predicates_

## Method types ##
- Prototype method
  - Can be called directly on corresponding data type
- Static method
  - Can ony be called on the constuctor for the data type
```javascript
// Prototype Method
'abc'.charCodeAt(0); // 97
// Static method
String.fromCharCode(97); // 'a'
```

## Working with strings ##
_Strings are zero-indexed ordered collections_

**Rerfernece string elements**
 - Can do this using bracket notation
 - Can also use a method like String.prototype.slice or substring
```javascript
let str = 'brandon';
str[0]; // 'b'
str.slice(2, 4); // 'an'
str.substring(2, 4); //'an'
str.substring(-2); // 'brandon'
str.slice(-2); // 'on'
```

### String Methods ###

_NOTE: Because strings are primitive values, any operation on them will return a new string_

**String.prototype.concat**
- The ```concat``` method concatenates the string arguments to the calling string and ```returns``` a new string.
```javascript 
'hello '.concat('world'); // 'hello world'
```

**String.prototype.includes**
- Takes a string as an argument and ```returns``` a boolean signifying whether that string exists within the string that ```includes``` was called on.
- Has optional second argument for index to start searching at
```javascript
let sentence = `qwerty`
sentence.includes('w'); // true
sentence.includes('w', 2); // false
sentence.includes('z'); // false
```

**String.prototype.split**
- Seperates a given string into multiple strings and ```returns``` them in the form of an array
- Has optional argument that determines the seperator character for the split
  - No argument specification returns the entire string as an array. Empty string argument returns split on each character.
```javascript
let string = 'I went to the store';
string.split(); // [ 'I went to the store' ];
string.split(''); // [ 'I', ' ', 'w', 'e', 'n', 't', ' ', 't', 'o', ' ', 't', 'h', 'e', ' ', 's', 't', 'o', 'r', 'e' ]
string.split(' '); // [ 'I', 'went', 'to', 'the', 'store' ]
```

**String.prototype.trim**
- Removes whitespace from both ends of the string that it is called on and ```returns``` new string.
- Useful when getting input from the user
```javascript
'    brandon corey    '.trim(); // brandon corey
'\tbrandon corey\n'.trim(); // brandon corey (NOTE: These are both whitespace characets. Tab and new line respectively
```
-There are variations of the ```trim``` method. ```trimStart``` removes whitespace from start of string, ```trimEnd``` removes white space from end of string
```javascript
'   once upon a time'.trimStart(); // 'once upon a time'
'once upon a time'.trimEnd(); // 'once upon a time'
```

**String.prototype.toUpperCase and String.prototype.toLowerCase**
- Convert the strings to uppercase or lowercase characters respectively and ```returns``` new string.
```javascript
'Brandon'.toUpperCase(); // 'BRANDON'
'Brandon'.toLowerCase(); // 'brandon'
```

**String.prototype.charAt**
- Takes an index as an argument and ```returns``` the character at that index for a given string. Nearly identical to using bracket notation
```javascript
'brandon'.charAt(2); // 'a'
'brandon'[2]; // 'a'

// NOTE THE DIFFERENCE BELOW HOWEVER: When passing in indices for characters that don't exist
'brandon'.charAt(10); // ''
'brandon'[10]; // undefined
```

**String.prototype.charCodeAt**
- Takes an index as an argument and ```returns``` the character code (UTF-16) of the character at the index
```javascript
'abc'.charCodeAt(1); // 98
'abc'.charcodeAt(); // 97 --> NOTE: By default, returns char code of first character
```

**String.fromCharCode**
- Takes a character code (UTF-16) and ```returns``` the character represented by that code
```javascript
String.fromCharCode(97); // 'a'
```

**String.prototype.startsWith and String.prototype.endsWith**
- Takes a string argument and ```returns``` true or false if the starting or ending characters match the characters passed in as the argument
```javascript
let name = 'brandon';
name.endsWith('don'); // true
name.endsWith('and'); // false

name.startsWith('br'); // true
name.startsWith('and'); // false
```

**String.prototype.repeat**
- Constructs and ```returns``` a new string which contains a specified number of copies of the string on which it was called, concatenated together.
```javascript
let phrase = 'black and yellow ';
phrase.repeat(4); // 'black and yellow black and yellow black and yellow black and yellow
```

## Working with arrays ##
_Arrays are zero-indexed ordered collections_

**Array Element Reference**
- Can do this the same as a string, using bracket notation
- Can use Array.prototype.slice
```javascript
let arr = [ 'these', 'are', 'are', 'different', 'words', 'within', 'a', 'sentence' ];
arr[0] // 'these'
arr.slice() // [ 'these', 'are', 'are', 'different', 'words', 'within', 'a', 'sentence' ] (NOTE: THIS IS A COPY)
arr.slice(-4, -1) // [ 'words', 'within', 'a' ]
```

### Array Methods ###

**Array.prototype.forEach**
-  A method that executes a provided callback function once for each array element. 
-  ```forEach``` passes two arguments to the callback function: (Value of current element, index of current element)
-  The callback function determines what happens to each element on each iteration
-  ```Returns``` undefined
```javascript
['a', 'b', 'c'].forEach((element, idx) => {
  console.log(`The index of ${element} is ${idx}`);
});
// 'The index of a is 0'
// 'The index of b is 1'
// 'The index of c is 2'
// undefined
```
**Array.prototype.filter**
- Filter passes the current element value and index to a callback function
- For each element, the callback function returns a value
- If the value ```returned``` by the callback is truthy, ```filer``` will select the current element and put it into an array
- The filter method ```returns``` an array of all the filtered elements when all iterations have completed

```javascript
let array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

array.filter(nums => nums % 2 === 0); // [2, 4, 6, 8, 10]
array.filter(nums => nums + 5) // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]; (All values in callback evaluate to truthy, so each element in array is returned)

array.filter(nums => {
  return nums > 7;
});

// [8, 9, 10]

array.filter(nums=> {
  nums > 7;
}):
// [] (Forgot to return the values in callback, so filter does not select any elements to be returned in resulting array)
```

**Array.prototype.map**
- ```map``` passes the current element value and index to a callback function
- The callback function ```returns``` a value to map on each iteration
- ```map``` uses the ```return``` value of the callback to transform the original array
- ```map``` ```returns``` the transformed array

```javascript
let array = [1, 2, 3, 4, 5];

array.map(num => num + 5);  // [ 6, 7, 8, 9, 10 ]; 
array.map(num % 2 === 1); // [ true, false, true, false, true ]
array.map(num => {
  num * 2;
});
// [ undefined, undefined, undefined ];
```
**Array.prototype.find**
- ```find``` passes the current element value and index to a callback function
- The callback function ```returns``` the truthy and falsey values to ```find```
- Find returns the first truthy value `returned` from the callback function, otherwise, undefined.
```javascript

const customers = [
  { name: "Joe Smith", phone: 5081113456 },
  { name: "Bob Johnson", phone: 5086789112 },
  { name: "Brandon Corey", phone: 5088081106 },
];

customers.find(customer => {
  return (customer.name).toLowerCase() === 'brandon corey'
}); 
// {name: 'brandon corey', phone: 5088081106}
```

**Array.prototype.sort**
- `sort` method sorts elements in place, returning the reference to the original array now sorted
- `sort` by default will convert elements to strings, and then compare based on UTF-16 codes and sort in ascending order
- `sort` takes an optional callbacck function as an argument
- Callback funciton takes two arguments, two elements to be compared
- Callback function logic
  - if a is less than b by some ordering criterion, `return` -1
  - if a is greater than b by some ordering criterion, `return`
  - else return 0

```javascript
let arr = [10 , 15, 12, 11, 7, 5]

arr.sort((a, b) => a - b) // [ 5, 7, 10, 11, 12, 15 ]

arr.sort((a, b) => {
  if (a < b) return -1;
  if (a > b) return 1;
  return 0;
});

[ 5, 7, 10, 11, 12, 15 ]
```

## Object Element Reference ##
_Objects are collections that use key-value pairs, where the key is a string and the value is any JavaScript data type_

**Object Element Reference**
- Can use bracket notation or dot notation
- key/property names in an object must be unique
- Object.keys(obj) method and Object.values(obj) method can be used to reference their respective components (keys, values)
```javascript
let name = { last: ever, first: greatest } // like a sprained ankle boy aint nothing to play with
name.last = 'Corey';
name['first'] = 'Brandon';
name.last[0] // Returns 'C' since last is now 'Corey';
```
### Iterators ###
- Can iterate over an object using a `for in` loop

```javascript
let person = { name: 'brandon', age: 23, eight: "5'9" };

for (let props in person) {
  console.log(`The ${props} of ${person.name} is ${person[props]}`)
}
```

**NOTE: `for in ` will iterate over an object's prototype (an object from which it inherited properties) as well**

```javascript
let obj1 = { a: 5, b: 10 }
let obj2 = Object.create(obj1);
obj2.c = 11;
obj2.d = 15;

console.log(obj1) // { a: 5, b: 10 }
console.log(obj2) // { c: 11, d: 15 }

for (let props in obj2) {
  console.log(obj2[props]);
}
// 11
// 15
// 5
// 10
```
- Can get around this behavior using `hasOwnProperty` method
  - `hasOwnProperty` takes an argument of a string
  - `hasOwnProperty` returns `true` if the name of the argument is a property of the object that it is called on. **Excludes inhertied properties**
```javascript
let obj1 = { a: 5, b: 10 }
let obj2 = Object.create(obj1);
obj2.c = 11;
obj2.d = 15;

console.log(obj1) // { a: 5, b: 10 }
console.log(obj2) // { c: 11, d: 15 }

for (let props in obj2) {
  console.log(obj2[props]);
}
// 11
// 15
```
 
### Object Methods ### 
 
**Object.keys**
- Static method returns an object's keys as an array
```
let person = { name: 'brandon', age: 23, eight: "5'9" };

let personKeys = Object.keys(person);

console.log(personKeys) // [ 'name', 'age', 'height' ];

personKeys.forEach(prop => console.log(person[prop]);
// 'brandon'
// 23
// "5'9"
```

**Object.values**
- Static method returns an Object's values as an array

```javascript
let person = { name: 'brandon', age: 23, eight: "5'9" };

let personValues = Object.values(person);

console.log(personValues); // [ 'brandon', 23, "5'9"];
```

**Object.entries**
- Static method returns an array of nested arrays, with each nested array corresponding to each key-value pair of the original object
```javascript
let person = { name: 'brandon', age: 23, height: "5'9" };

let personArray = Object.entries(person); // [ [ 'name', 'brandon' ], [ 'age', 23 ], [ 'height', "5'9" ] ]

personArray.forEach(pair => {
  let [ key, value ] = pair;
  console.log(`The value for ${key} is ${value}`)
});
```

**Object.fromEntries**
- Static method returns an object when passed a nested array of key value pairs as an argument

```javascript
let personArr = [ [ 'name', 'brandon' ], [ 'age', 23 ], [ 'height', "5'9" ] ];

let person = Object.fromEntries(personArr);

console.log(person); // { name: 'brandon', age: 23, height: "5'9" };
```

**Object.assign**
- Static method that can merge to objects (mutating) as well as creates a shallow copy of an object (non mutating)
```javascript
let person = { name: 'brandon', age: 23, height: "5'9" };
let personContinued = { major: 'economics', hobbies: 'weight lifting' };

Object.assign(person, personContinued);

console.log(person); // { name: 'brandon', age: 23, height: "5'9", major: 'economics', hobbies: 'weight lifting' } MUTATES person, not personContinued

OR

let newObj = Object.assign({}, person, personContinued); // { name: 'brandon', age: 23, height: "5'9", major: 'economics', hobbies: 'weight lifting' }

// This one creates a copy. Can use empty Object as target, and can copy or merge any additonal object arguments

```
## Arrays are Objects ##
- Arrays are a type of object
- The property of array that is dealth with object is `length`;
   - **NOTE** `length` is not listed as property of array when using `Object.keys` method
- All indices of an array are also property names of the object
  - The indices are translated to strings however in the context of property names
```javascript
let arr = [1, 2, 3];
Object.keys(arr); // [ '0', '1', '2' ]
arr['3'] = 4;
console.log(arr); // [1, 2, 3, 4];
```

**Elements vs Properties**
- Elements are just the values of non-negative interger properties of an array
- All non-interger or negative interger properties of an array are **NOT** considered elements
- Iterative array methods ignore all non-element values.

```javascript
let arr = [1, 2, 3];
arr['banana'] = 'yummy';
console.log(arr)// [1, 2, 3, banana: 'yummy']
arr.length // 3
arr.forEach(element => console.log(element));
// 1
// 2
// 3
```

## Pass by Reference vs Pass by value ##

### Pass by value ###
- When a variable is passed as an argument to a function, the function cannot modify the orignial value, only a copy of it.
- **_JavaScript is pass by value for Primitives_**
- When an primitive value argument is passed to a function, the corresponding parameter is assigned the same value of the argument, but not to the og value in memory. 
```javascript
function changeValue(value) {
  value = 5; // Locally scoped
}

function mainFunction() {
  let value = 10; // Locally scoped
  changeValue(value); // Explanation below
  console.log(value); // logs 10;
}
mainfunction(); // 10
```
- When `value` in `mainFunction` is passed to `changeValue` as an argument, the `value` parameter for `changeValue` is assigned a value of 10, reassigned to 5
- Because the `value` parameter for `changeValue` is locally scoped, mainFunction's `value` is unaffected

### Pass by Reference ### 
- When a variable is passed as an argument to a function, the function can modify the original variable's value(s).
- _**JavaScript**_ is pass by reference for Objects
- With objects, since variables act as pointers to the original object, we are passing a reference as an argument, opposed to a value.
```javascript
let array = [1, 2, 3, 4, 5];

function removeLastElement(arrayArg) {
  arrayArg.pop();
}

removeLastElement(array);
console.log(array); // [1, 2, 3, 4]; // Permnantly altered

function returnsFollowSameRules(array) {
  return array;
}

let newArray = returnsFollowSameRules(array);
newArray = array // true // Returns act the same as the argumenbts. In this case, we are literally returning a reference to the same array;
```

## Variables as Pointers ##

- When a variable is declared, JavaScript allocates a spot somewhere in memory to hold its value

**Primitves**
- With primitive values, the actual value assigned to variable is stored within the allocated memory.
- So, each variable points directly to the memory location where the value lives
- When you reassign a primitive, the value at that specific memory location that is being pointed to is **CHANGED**
```javascript
let x = 5; // x is the name of mem address 0x1234, (x points to mem address 0x1234)
           // which contains value of 5 
           
x = 10; // x is the name of mem address 0x1234, (x points to mem address 0x1234)
        // which contains value of 10 
        
let y = x; // y is the name of mem address 0x4567, (y points to mem address 0x4567)
           // which contains value of 10 
```

**Objects**
- With Objects, the variable points to a memory location that contains a reference to the object, rather than a value
- As a result, any variable that is assigned the value of an object will being pointing to the same reference
- **UNLIKE A PRIMITIVE**, if you reassign an object, rather than mutate it, the object will now live at a new memory location
```javascript
let obj = { a: 1, b: 2 } // obj is the name of mem address 0x1234 (points to 0x1234)
                         // which contains a value of 0x11562 (contains reference to Object)
                         // mem address 0x11562 contains a value of { a: 1, b: 2 }

obj.c = 3 // obj is the name of mem address 0x1234, (points to 0x1234)
          // which contains a value of 0x11562 (contains reference to Object)
          // mem address 0x11562 contains a value of { a: 1, b: 2, c: 3}

obj = { a: 1 } // obj is the name of mem address 0x1234, (points to 0x1234)
               // which contains a value of 0x33456 (contains reference to Object)
               // mem address 33456 contains a value of { a: 1 };
```
## console.log vs return ##

**console.log**
- console.log is a method that prints the specified argument to the console
- console.log returns undefined
- printing something to the console is considered a "side effect" is the context of a function

**return**
- return is a keyword that specifies a value that is to be explicity returned from a function
- this value can be a string, number, object, or even another function 
- a return value from a function can then be used after the function is called

```javascript
function print(argument) {
  console.log(argument);
}
print('hello'); // prints hello, returns undefined

function return(argument) {
  return argument;
}
return('helloo') // prints nothing, returns 'hello';
```

 ## Truthiness vs Boolean ##
 
 **Boolean**
 - JavaScript uses the `true` and `false` primitive values as booleans
 - These help us build conditional logic based on the premise of whether a statement is true or false
 - Typically, these values aren't explicitly used, and insted condtional expressions evaluate to a boolean
 ```javascript
 let name = 'brandon';
 
 if (name.length < 10) console.log(name) // prints brandon as the conditional statement evalued to true
 ```
 
 **Truthiness**
 - Values that evaluate to `true` are considered `truthy`
 - Values that evaluate to `false` are considered `falsey`
 
 **Truthy vs falsy**
 - Values to evaluate to falsy
  - `false`
  - `undefined`
  - `0`
  - `""`
  - `NaN
 - Values that evaluate to truthy
  - Every other value not listed above
  - Remember that type coercion can produce some of the above values implicitly

## Functions ##

## Side effects ##
- Function re-assigns any non-locally scoped variable
- Mutates the value of any object referenced by a non-local variable (an argument, or a globally scoped object)
- It reads from or writes to a file. Includes writing to the console or reading input from the terminal (user input)
- Raises an exception without handling it
- Calls another function that has side effects

### Function definition and invocation ###

**Function definition**
- A function can be defined through either a function _declaration_ or a function _expression_
- A definition includes the function name, as well as the parameters of the function

```javascript

// declaration (these are hoisted to the top of the program and saved for later)
function add(a, b) {
  return a + b;
}
// expression (technically annonymous function stored in a variable)
const add = function (a,b) {return a + b};

// expression (technically annonymous function stored in a variable)
const add = (a, b) => return a + b;
```

**Function invocation**
- Functions are invoked or called by typing their name and providing some optional values as arguments
- When a function is invoked
  - The program then jumps to the definition of the function that is being called
  - The values of the arguments are assigned to the values of the parameters within the function definition, and then the function body executes (from the definition)
  - A value is then returned from the function execution to the caller. This value can be saved as a variable
```javascript
const add = (a, b) => a + b; // definition

add(5,4); // invocation // When invoked, the function above is executed. The values 5 and 4 are passed to the function definition, and the body executes.
```

## Function declarations, expressions, and arrow expressions
- These are the three ways to define a function

**Declarations**
- Use function keyword
- Are hoisted to top of JavaScript program. Allows for calling of function before declaration
```javascript
function add(a, b) {
  return a + b;
}
```
**Expression**
- An annonymous function that may be stored in a variable
- Not hoisted to top of program
```javascript
const add = function (a,b) {return a + b};
```

**Arrow expression**
- An annonymous function that may be stored in a variable
- Syntactically unique, does not require return keyword if single expression is contained within function body
  - Also does not require curly braces in this situation
```javascript
const add = (a, b) => a + b;
```

**NOTE**
- If a function declaration is nested within another function, it is no longer considered a declaration, it is an expression

## Implicit return value of a function ##

**Functions implicitly return `undefined`**
- Remember that JS methods can have implicit return values that are not `undefined`. Must read documentation to determine return values of non-user-defined methods.

**You can specify an explcit return value using the `return` keyword**

## First-Class Functions ##
_Similar to primitive values and objects, first-class functions have the following properties:_
- Can be assigned to a variable or an element of a data structure
- Can be passed as an argument to a function
- Can be returned as the return value of a function
**Functions can effectively be treated like any other type of value**

### Higher Order Functions ###
- Functions that either
  - Take another function as an argument
  - Return other functions

### Callback Functions ###
- Functions that are passed to other functions as arguments

```javascript
let arr = [1, 2, 3];
arr.map(num => num * num); // map is the higher order function here, (num => num * num) is the call back function (annonymous arrow function expression)
```

**Launch School example**
```javascript
array.forEach(element => {
  console.log(element.foo);
});
```

This paragraph talks about the `forEach` method being
called by the object referenced by `array` in the above
code. It invokes the callback function for each element,
passing that element to the callback as an argument.
Within the callback, the element is known by the
parameter name `element`, and the callback uses the
`console.log` method log the value of `element.foo`.


**Note: Helpful launch school notes on breaking down higher order and callback functions**
- What type of action is being performed? Method call? Callback? Conditional? Something else?
- On what value is that action performed?
- What is the side-effect of that action (e.g., output or destructive action)?
- What is the return value of that action?
- Is the return value used by whatever instigated the action?


## Implementation-level vs. user-level ##
```javascript
function reverseSentence(sentence) {
  let result = [];
  let words = sentence.split(' ');
  for (let idx = words.length - 1; idx >= 0; idx--) {
    result.push(words[idx]);
  }
  return result.join(' ');
}
```
**Implementation-level**
_reverseSentence function is declared and takes one string argument. A result variable is declared  in the function body and initalized to an empty array. The split method is then called on the string argument and assigned to the variable `words`. A for loop, with o local variable `idx` declared and initalized to the index of the a element in the words array, iterates through the array backwards, pushing each word in the sentence to the `result` array. The `join` method is called on the resulting array with a space as the join argument and the string is returned.

**User level**
_reverseSentence is a function that takes one argument and returns a new string. The returned string will have a reversed order on each space contained within the original string_
## Legal vs idomatic ##

**legal/non-idiomatic**
- If a name is legal in JavaScript, it is valid, however poor practice with standard library
- External libraries can rely heavily on these non-idiomatic names as to not conflict with vanilla js or other libraries
- `fizz_buzz`
- `fizzBUZZ`
- `MILESPERHOUR`
- `_hello`
- `Sgoodbye`

**idiomatic**
- A type of naming convention that aligns with common practice among programmers for a specific language
- camelCase variables for example
- `employee`
- `fizzbuzz`
- `speedOfLight`
- `m00n`
- `destinationURL` (URL is an acronym so can be capitalized)
- `MILES_PER_HOUR`
