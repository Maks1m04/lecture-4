JavaScript Scope is the area where a variable (or function) exists and is accessible. We can layer the scope in a system which means the child scope can access the parent scope but not vice-versa.

Javascript has three different scopes
Global Scope
Block Scope
Function Scope
Global Scope
Those variables which are declared outside the function or blocks or you can say curly braces({}) are having a global scope.

In a JavaScript program, global variables can be accessed from anywhere.

The scope of var, let, and const are quite equivalent when declared outside the function.


Example: In this example, we will declare all the variables outside the function and now we can access those variables from anywhere in the Javascript program.

   
var global_variable1 = "Geeksforgeeks";
let global_variable2 = "Geeks";
const global_variable3 = "GFG";
 
function check_global_variables(){
    console.log(global_variable1);
    console.log(global_variable2);
    console.log(global_variable3);
}
 
check_global_variables();

Output
Geeksforgeeks
Geeks
GFG



Function Scope
Those variables that are declared inside a function have local or function scope which means variables that are declared inside the function are not accessible outside that function.

When declared inside a function, variables declared with var, let, and const look quite similar.

Note: Functions and Objects are also variables in Javascript.

Variables which are declared within the function have function scope. When var declared in the function have a function scope. Function uses the curly braces to store the function body . Therefore, block scope and function scope is same for the function body.

Example: In this example, we will declare a variable inside the function and try to access it from outside the function.

 
function check_function_scope(){
    var variable1 = "Geeksforgeeks";
    let variable2 = "Geeks";
    const variable3 = "GFG";
    console.log(variable1);
    console.log(variable2);
}
 
check_function_scope();
console.log(variable3);
Output: In the above example, we tried to access the variable outside the function but it gives the reference error because of the function scope.

Geeksforgeeks
Geeks
ReferenceError: variable3 is not defined
Block Scope
Before the ECMA6(2015) we have only global and function scope but when the Let and Const keywords were introduced in ES6 they provide the block scope.

Variables that are declared inside the { } (curly braces) can only access inside that scope not from the outside of it.

Variables declared with var do not have block scope only let and const have block scope.

Example: In this example, we will declare the variable inside the block scope.

   
{   
    var variable_1 = "GFG";
    const variable_2 = "Geeksforgeeks";
    let x=2;
    x*=2;
    console.log(x);
    console.log(variable_2);
}
 
console.log(variable_1);
 Output: In the above example, we have successfully accessed the variable with the var keyword because var does not have a block scope.

4
Geeksforgeeks
GFG
Lexical Scope
The variable is declared inside the function and can only be accessed inside that block or nested block is called lexical scope.

Example: In this example, we will declare the variable inside the function and going to access inside the nested function.

   
function outerFunction() {
    const outerVariable = "Hello";
 
    function innerFunction() {
        const innerVariable = "Geeks";
        console.log(`${outerVariable} ${innerVariable}`);
    }
 
    innerFunction();
}
 
outerFunction();
Output:

Hello Geeks

Hoisting is a concept that enables us to extract values of variables and functions even before initializing/assigning value without getting errors and this happens during the 1st phase (memory creation phase) of the Execution Context.

Features of Hoisting:
In JavaScript, Hoisting is the default behavior of moving all the declarations at the top of the scope before code execution. Basically, it gives us an advantage that no matter where functions and variables are declared, they are moved to the top of their scope regardless of whether their scope is global or local. 
It allows us to call functions before even writing them in our code. 
Note: JavaScript only hoists declarations, not initializations.

JavaScript allocates memory for all variables and functions defined in the program before execution.

Sequence of variable declaration: The following is the sequence in which variable declaration and initialization occur. 

Declaration –> Initialisation/Assignment –> Usage 

Variable lifecycle:
let a;                  // Declaration
a = 100;            // Assignment
console.log(a);  // Usage

However, since JavaScript allows us to both declare and initialize our variables simultaneously, so we can declare and initialize at the same time.  

let a = 100;

Note: Always remember that in the background the Javascript is first declaring the variable and then initializing them. It is also good to know that variable declarations are processed before any code is executed. 

However, in javascript, undeclared variables do not exist until the code assigning them is executed. Therefore, assigning a value to an undeclared variable implicitly creates it as a global variable when the assignment is executed. This means that all undeclared variables are global variables.

Example:
   
// Hoisting
function codeHoist() {
  a = 10;
  let b = 50;
}
codeHoist();
 
console.log(a); // 10
console.log(b); // ReferenceError : b is not defined
Output:
10
ReferenceError: b is not defined

Explanation: In the above code, we created a function called codeHoist() and in there we have a variable that we didn’t declare using let/var/const and a let variable b. The undeclared variable is assigned the global scope by javascript hence we are able to print it outside the function, but in case of the variable b the scope is confined and it is not available outside and we get a ReferenceError.

Note: There’s a difference between ReferenceError and undefined errors. An undefined error occurs when we have a variable that is either not defined or explicitly defined as type undefined. ReferenceError is thrown when trying to access a previously undeclared variable. 

JavaScript var of ES5: When we talk about ES5, the variable that comes into our minds is var. Hoisting with var is somewhat different. When it is compared to let/const. Let’s make use of var and see how hoisting works.

Example:
   
// var code (global)
console.log(name); // undefined
let name = 'Mukul Latiyan';
Output: 
ReferenceError: Cannot access 'name' before initialization

Explanation: In the above code we tried to console the variable name which was declared and assigned later, the compiler gives us undefined which we didn’t expect as we should have gotten ReferenceError as we were trying to use the name variable even before declaring it. 

But the interpreter sees this differently, the above code is seen like this:


   
// how interpreter sees the above code
let name;
console.log(name); // undefined
name = 'Mukul Latiyan'; 
Output:
undefined

Function scoped variable: Let’s look at how function-scoped variables are hoisted.

Example:
   
// Function scoped
function fun() {
  console.log(name);
  let name = 'Mukul Latiyan';
}
fun(); // Undefined
Output: 
undefined

There is no difference here as when compared to the code where we declared the variable globally.

Example:
We get undefined as the code seen by the interpreter.

   
function fun() {
  let name;
  console.log(name);
  name = 'Mukul Latiyan';
}
fun(); // undefined
Output: 
undefined

In order to avoid this pitfall, we can make sure to declare and assign the variable at the same time, before using it.

Example:
   
function fun() {
  let name = 'Mukul Latiyan';
  console.log(name); // Mukul Latiyan
}
fun();
Output: 
Mukul Latiyan

JavaScript Let of ES6: We know that variables declared with let keywords are block scoped not function scoped and hence there is no problem when it comes to hoisting. 

Example:  
 
//let example(global)
console.log(name);
let name = 'Mukul Latiyan'; // ReferenceError: name is not defined
Output: 
ReferenceError: name is not defined

Explanation: Like before, for the var keyword, we expect the output of the log to be undefined. However, since the es6 let doesn’t take kindly on us using undeclared variables, the interpreter explicitly spits out a Reference error. This ensures that we always declare our variable first. 

JavaScript const of ES6: It behaves similarly to let when it comes to hoisting. A function as a whole can also be hoisted and we can call it before the declaration.

Example:
   
fun(); // Calling before declaration
 
function fun() { // Declaring
  console.log("Function is hoisted");
}
Output:
Function is hoisted

Also, if a function is used as an expression and we try to access it before the assignment an error will occur as only declarations are hoisted.

Example:
   
fun() // Calling the expression
 
let fun = () =>{ // Declaring
    let name = 'Mukul Latiyan';
    console.log(name);
}
Output: 
ReferenceError: Cannot access 'fun' before initialization

However, if var is used in the expression instead of let we will get the following Type Error as follows.

Example:
   
fun() // Calling the expression
 
var fun = () =>{ // Declaring
    let name = 'Mukul Latiyan';
    console.log(name);
}
Output:
TypeError: fun is not a function
