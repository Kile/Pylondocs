## JavaScript/TypeScript introduction
JavaScript/TypeScript (JS/TS) is a **object oriented programing** (OOP) language, but does this in a different way then most programming languages. Using classes (objects) is kinda optional.
In traditional OOP languages, like C++/C# and Java, you have **classes**, were you have your **variables** and **methodes/functions**.
```cs
// C# (not JavsScript/TypeScript)
class MyClass { // a class
  int x; // a variable
  
  void MyFunction () { // a function
    // code
  }
}
```
You have here a class named `MyClass`.
`MyClass` itself has to be instanziated to work. You can think of it like the hardware of a computer. You can buy many computers and they all will have the same parts: a CPU, a GPU, RAM, some drives... but these computers will probably have different CPUs, different amount of memory... But they all have the same functionality and use the same parts (just with different values).
Back to programing, all instances of `MyClass` will have a value for `x`, but the value itself may differ from one instance to another. All instances of `MyClass` have a function called `MyFunction`. You can execute this part of the code (the function `MyFunction`) whenever you want, but if you use `x` inside the function, it will only use the local value of `x` (the value of `x` setted in **this instance** of `MyClass`).
In some OOP Languages, you have some kind of `Main` class, which has only one instance. So you start from it, and create new instances of other classes in it, and use the variables and functions from these instances.
To say it simple: a class describes an **object** with it's properties in form of **variables** and **functions**.


(Here is one important thing to know if you use Java/C++/C#: there is no global value for `MyClass.x` here, because you don't have a "main instance" of `MyClass`. If you want that all instances of `MyClass` have the same value for `MyClass.x` at all time, you have to make the variable `static`.)


JavaScript/TypeScript is there a bit different. You can have functions **outside** of classes!
Additionaly you can easily say, do function 1 `f1()` but don't wait until it's finish, but do in parallele function 2 `f2()`. 
This is archived with the keyword `async`.
If you have an asynchronous function, but you need it's return value, you have use the keyword `await` to signify that the function should be executed first and after it's completly finished, continue.


// further explanation of TypeScript


// importance of clean code and doing the conventions


## Variables and TypeScripts primitiv types
A variable in programing is pretty much the same thing like in mathematics. You have e.g. an variable named `x` and you can use `x` to perform different actions with it. Unlike mathematics, you know the value of `x` at all points in time.


Variables have different possible types. If you want to store a number, you use an other type when you want to store a word. In JavaScript you don't have to manage the type of variables! But you still have errors if you want to multiply two words with each other so be carefull! TypeScript on the other hand, has types which you can manage but this is completly **optional**.


To create a variable you first need to **declare it's name**:
```js
let x; // declaring a new variable with the name x
```
If you are using TypeScript, I would **heavily** encourage you, to **declare it's type** too:
```ts
let x: number; // declaring a new variable with the name x and type number
```
After the declaration, you can **initialize it with it's first value** (after the initzialization of the first value, it isn't called initzialization anymore):
```js
x = 5; // initzialzing x with the value 5
```
If you want to read it's value, just write the name of the variable:
```js
console.log(x); // expected output: 5
```
If you want to change it's value just change it!
```js
x = 6; // changing the value of x to 6
```


If you want to do this a bit shorter and write cleaner code, declare and initzialize your variables at the same time:
```js
// JavaScript
let x = 5;
```
```ts
// TypeScript
let x: number = 5;
```


TypeScript has 13 primitiv types of variables. Your code will run either way but it is **way** better do declare the type of variables for things like readability. The types are:

**Boolean**: True/False

**Number**: Any number, including negativs and point numbers (in other programing languages often called: floating point number)

**String**: Character**s** including emojis. Strings are written in ""!

**Array**: An array is a list of values. You can have e.g. the array `{0, 5, 1, 7}` which has values from type `Number` in it.

**Tuple**: 

**Enum**:

**Any**:

**Null**:

**Undefined**:

**Void**:

**Object**:

and Unknown and Never

