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
 number = 3 // Reassignment of the value 3 to the variable "number"
 ```
 **NOTE: When using '=' in the context of a vriable assignment, it is called an assignment operator**
 
 ##Variable Scope##
 - A variable's scope determines where it is available in a program
 - Depends on the scope in which the variable is declared
 **let and const**
 - Have block scopes
 - A block is a set of JS statements between a pair of curly braces
 ```javascript
 if (iLovePie) {
   eatPie();
 ```
