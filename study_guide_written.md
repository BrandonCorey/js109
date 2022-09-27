## Declarations, initialization, assingment, and re-assignment ##
**What is a variable?**
- *A named area of a program's memory where data can be stored*

**Declarations**
- *A variable declaration is a statement that asks the JavaScript egnine to reserve space for a variable (that has a particular name)*
  - Declarations are made with the let and const keywords
  - "let" is used for variables, "const" for constants

  ```javascript
  let variable;
  const constant = 1;
  ```
  - Notice that an initalizer must be specified for constant declarations, but not for variable declarations

**Initialization**
 - *The assignment of a value to a variable declaration. If an initalizer is not specified at time of declaration, variable is initalized to value of undefined*
  - As mentioned above, constants must be initalized with a value at declaration
  - Variables can be initalized with a value or without

 ```javascript
  let variable; // This is a variable declaration initalized to a value of undefined
  const constant = 1; // This is a constant declaration initalized to a value of 1
  ```
