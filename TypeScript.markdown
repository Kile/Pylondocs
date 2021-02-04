## Table of contents
[**Introduction**](https://github.com/FlorianStrobl/Pylondocs/blob/main/TypeScript.markdown#javascripttypescript-introduction)

[**Variables**](https://github.com/FlorianStrobl/Pylondocs/blob/main/TypeScript.markdown#variables)

[**Types**](https://github.com/FlorianStrobl/Pylondocs/blob/main/TypeScript.markdown#typescript-types)

[**Functions**](https://github.com/FlorianStrobl/Pylondocs/blob/main/TypeScript.markdown#functions)


## JavaScript/TypeScript introduction
JavaScript/TypeScript (JS/TS) are **object oriented programing** (OOP) languages, but does this in a different way then most programming languages. Using classes (objects) is here kinda optional.
In traditional OOP languages, like C++/C# and Java, you have **classes**, were you have your **variables** and **methodes/functions**.
```cs
// C# (not JavsScript/TypeScript)
class Dog { // a class
  string name; // a varibale
  int age; // a variable
  
  void Bark () { // a function
    // code
  }
}
```
You have here a class named `Dog`.
`Dog` itself has to be instanziated to work. You can think of it like the hardware of a computer. You can buy many computers and they all will have the same parts: a CPU, a GPU, RAM, some drives... but these computers will probably have different CPUs, different amount of memory... But they all have the same functionality and use the same parts (just with different values).
Back to programing, all instances of `Dog` will have values for `name` and `age`, but the values itself may differ from one instance to another. All instances of `Dog` have a function called `Bark()` too. You can execute this part of the code (the function `Bark()`) whenever you want, but if you use `age` or `name` inside the function, it will only use the local values of `age` and `name` (the values of `age` and `name` setted in **this instance** of `Dog`).
In some OOP Languages, you have some kind of `Main` class, which has only one instance. So you start from it, and create new instances of other classes in it, and use the variables and functions from these instances to complete your goal.
To say it simple: a class describes an **object** with it's properties in form of **variables** and **methodes/functions**.


(An important thing for Java/C++/C# users: there is no global value for `Dog.name` here, because you don't have a "main instance" of `Dog`. If you want that all instances of `Dog` have the same value for `Dog.age` at all time, you have to make the variable `age` `static`.)


JavaScript/TypeScript is there a bit different. You can have functions **outside** of classes!
Additionaly you can easily say, do function 1 `f1()` but don't wait until it's finish, but do in parallele function 2 `f2()`. 
This is archived with the keyword `async`.
If you have an asynchronous function (an `async` function), but you need the value it will return, you have use the keyword `await` to signify that the function should be executed first and after it's completly finished, continue.


// further explanation of TypeScript


// importance of clean code and doing the conventions


## Variables
A variable in programing is pretty much the same thing like in mathematics. You have e.g. a variable named `x` and you can use `x` to perform different actions with it. Unlike mathematics, you know the value of `x` at all points in time.


Variables have different possible types. If you want to store a number, you use an other type when you want to store a word. In JavaScript you don't have to manage the type of variables! But you still have errors if you want to multiply two words with each other or appending to the number 5 the string "hi!" so be carefull! TypeScript on the other hand, has types which you can manage; but this is completly **optional**.


First step is the **declaration** of the name. There are three ways in JavaScript/TypeScript
```ts
//JavaScript
let x; // variable with name x declared
var x; // this is the same as let but has some specialty on the scope (don't use that!)
const x; // this signifis, that you won't change it's value

// TS
let x: number; // variable with name x declared with type number
// var and const are the same as in JS and you can too declare it's type
```

After the declaration, you can **initialize it with it's first value** (*initzialization* = setting the first value):
```js
x = 5; // initzialzing x with the value 5
```

You work with variables this way:
```js
// Reading the value is just typing the name
console.log(x); // expected output: 5

// Want to change the value? Just change it!
x = 6; // changing the value of x to 6
```

If you want to do this a bit shorter and write cleaner code, declare and initzialize your variables at the same time:
```ts
// JavaScript
let x = 5;

// TypeScript
let x: number = 5;
```

## TypeScript types

TypeScript has 13 primitiv types of variables. Your code will run either way but it is **way** better to declare the type of variables for things like readability and bug fixing. The types are ([here a more detailed overview over the types](https://www.typescriptlang.org/docs/handbook/basic-types.html)):

**Number**: Any number, including negativs and point numbers (in other programing languages often called: floating point number, takes 2 bytes)

**String**: Character**s** including emojis. At the beginning and ending of a String, you need to write *"*! (Takes 2 Bytes per character + some bytes at the start)

**Boolean**: True/False (this needs a whole byte despites that one bit would be enough)

**Array**: An array is a list of values from the same type. Every primitiv type can be stored in an array (yes even arrays). E.g. the array `{0, 5, 1, 7}`, has values from type `Number` stored. (Bytes depending on the type but you can say: bytes the type normaly needs * lenght of the array (number of values stored))

**Tuple**: Tuple types allow you to express an array with a fixed number of elements whose types are known, but need not be the same. (bytes have to be calculated like an array, but for each different type)

**Enum**: Enums helps you, to make your code more human readable. You can use any type (byte depening on the type used)

**Null**: This means, the variable hasn't stored anything in it (that means: yes every type can have `null` as value). The value is not "" (an empty string) or 0 (the number 0), the value is `null`. (0 bytes)

**Undefined**: It's pretty much the same as `null`. Still `undefined === null` is a false statement (in an if statement (will come later)). (0 bytes)

**Void**: This means *no type at all*. Commonly used for functions, which don't return anything.

**Never**: I don't even know what this is exactly lmao. It is used, when you have a function which will never return something and this isn't even `any`. You'll probably don't need that.

**Any**: Can be any type.

**Unknown**: The type is unknown so like `any`. It is used if you don't know what the type of the variable is.

**Object**: Objects will be discusst later on.

```ts
let myNumber: number = 5;

let myString: string = "Hello world!";

let myBool: boolean = true;

let myArray: Array<number> = {0, 5, 1, 7};
// the same thing:
let myArray2: number[] = {0, 5, 1, 7};

let myTuple: [string, number] = {"a string", 5}; // the order is important
// you can't swap the position of the number and the string!

enum Color {
  Red,
  Green,
  Blue
}
let aValueFromEnum: Color = Color.Green;

let x: number = null; // valid code

let x: number;
console.log(x); // expected output: undefined
x = undefined; // still valid

function myFunction(): void {} // this function returns nothing, so not even null or undefined (but if you console.log() this, it will say undefined)

let anything: any = 5;
anything = "Hello!";
anything = false;
```

## Functions

A function is a block of organized, reusable code that is used to perform a single, related action. Functions provide better modularity for your application and a high degree of code reusing. You have already seen various functions like console.log(). Normaly you get some **arguments/parameters** from the caller, then the function does things and you get finaly it's **return value**.

Example 1:

```ts
function f(x: number): number {
  return x * 2;
}

let y: number = f(5);

console.log(y); // expected output: 10
```

In this example, we have declared a function called `f` which takes one `number` as argument and returns one `number`. As we say: `y = f(5)`, the function `f()` is executed and it calculated `x` (in this case 5) multiplied with two and returned this value. Y took we **return value** and used it as it's value.

Example 2:

```ts
function sayHello(): void {
  console.log("Hello world");
}
```

This function don't need any arguments and don't return something either. It is still a valid function.


A important thing in JavaScript is the possibility to do things asynchronous. Consider the following example: (example 3)

```ts
async function f1() {
  console.log(1);
}

function f2() {
  console.log(2);
}

f1();
f2();

// This code will starting executing f1() while starting f2() too. That means you don't know if the ouput is: 1 2 or 2 1
```

If you have an `async` function, but you want, that this time it is called 100% sure first you can do:

```ts
await f1();
f2();

// expected output: 1 2
```
