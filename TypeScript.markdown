## JavaScript/TypeScript introduction
JavaScript/TypeScript (JS/TS) are **object oriented programing** (OOP) languages, but does this in a different way then most programming languages. In traditional OOP languages, like C++/C# and Java, you have **classes**, were you have your **variables** and **methodes/functions**.
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
`Dog` itself has to be initialized to work. You can think of it as the hardware of a computer. You can buy many computers and they all will have the same parts: a CPU, a GPU, RAM, some drives... but these computers will probably have different CPUs, different amounts of memory... But they all have the same functionality and use the same parts (just with different values).
Back to programming, all instances of `Dog` will have values for `name` and `age`, but the values themselves may differ from one instance to another. All instances of `Dog` have a function called `Bark()` too. You can execute this part of the code (the function `Bark()`) whenever you want, but if you use `age` or `name` inside the function, it will only use the local values of `age` and `name` (the values of `age` and `name` set in **this instance** of `Dog`).
In some OOP languages, you have some kind of `Main` class, which has only one instance. So you start from it, and create new instances of other classes in it, and use the variables and functions from these instances to complete your goal.
To say it simple: a class describes an **object** with it's properties in form of **variables** and **methods/functions**.


(An important thing for Java/C++/C# users: there is no global value for `Dog.name` here because you don't have a "main instance" of `Dog`. If you want that all instances of `Dog` have the same value for `Dog.age` at all times, you have to make the variable `age` `static`.)


JavaScript/TypeScript is there a bit different. You can have functions **outside** of classes! In fact, you don't have classes, you have **objects**.
Additionally, you can easily say, do function 1 `f1()` but don't wait until it's finished, but do in parallel function 2 `f2()`. 
This is archived with the keyword `async`.
If you have an asynchronous function (an `async` function), but you need the value it will return, you have to use the keyword `await` to signify that the function should be executed first and after it's completely finished, continue.

## Variables
Variables are used to store information to be referenced and manipulated in a computer program. They also provide a way of labeling data with a descriptive name, so our programs can be understood more clearly by the reader and ourselves. It is helpful to think of variables as containers that hold information. Their sole purpose is to label and store data in memory. This data can then be used throughout your program.


The first step is the **declaration** of the name. There are three ways in JavaScript/TypeScript
```ts
//JavaScript
let x; // variable with name x declared
var x; // this is the same as let but has some specialty on the scope (don't use that!)
const x; // this signifies, that you won't change its value
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
Variables have types. If you want to store a number you use another type when you want to store a word. In JavaScript, you don't have to manage the type of your variables, but you will still have errors if you want to multiply two words with each other or appending "Hello world" to the number 5. You still have to be careful about the types. TypeScript, on the other hand, has types which you can manage; but this is completely **optional** and you can use the JavaScript way at all time.


TypeScript has 13 primitive types of variables. Your code will run either way but it is **way** better to declare the type of variables for things like readability and bug fixing. The types are ([here a more detailed overview over the types](https://www.typescriptlang.org/docs/handbook/basic-types.html)): (* means it is actually an object)

- **Number**: Any number, including negatives and point numbers (in other programming languages often called: floating-point number, takes 2 bytes)

- **String**: Character(s) including emojis. At the beginning and end of a String, you need to write *"*! (Takes 2 Bytes per character + some bytes at the start)

- **Boolean**: True/False (this needs a whole byte despite that one bit would be enough)

- **Array***: An array is a list of values from the same type. Every primitive type can be stored in an array (yes even arrays). E.g. the array `{0, 5, 1, 7}`, has values from type `Number` stored. (Bytes depending on the type but you can say: bytes the type normally needs * length of the array (number of values stored))

- **Tuple***: Tuple types allow you to express an array with a fixed number of elements whose types are known, but need not be the same. (bytes have to be calculated like an array but for each different type)

- **Enum***: Enums helps you, to make your code more human-readable. You can use any type (byte depending on the type used)

- **Null***: This means, the variable hasn't stored anything in it (that means: yes every type can have `null` as a value). The value is not "" (an empty string) or 0 (the number 0), the value is `null`. (0 bytes)

- **Undefined**: It's pretty much the same as `null`, but not an object. Still `undefined === null` is a false statement. (0 bytes)

- **Void***: This means *no type at all*. Commonly used for functions, which don't return anything.

- **Never***: This represents the type of values that never occur

- **Any***: Can be any type.

- **Unknown***: The type is unknown so like `any`. It is used if you don't know what the type of the variable is.

- **Object***: Objects will be discussed later on.

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
A function is a block of organized, reusable code that is used to perform a single, related action. Functions provide better modularity for your application and a high degree of code reusing. You have already seen various functions like console.log(). Normally you get some **arguments/parameters** from the caller, then the function does things and you get finally its **return value**.

Example 1:

```ts
function f(x: number): number {
  return x * 2;
}
let y: number = f(5);
console.log(y); // expected output: 10
```

In this example, we have declared a function called `f` which takes one `number` as an argument and returns one `number`. As we say: `y = f(5)`, the function `f()` is executed and it calculated `x` (in this case 5) multiplied with two and returned this value. Y took we **return value** and used it as its value.

Example 2:

```js
function sayHello(): void {
  console.log("Hello world");
}
```

This function doesn't need any arguments and doesn't return something either. It is still a valid function.


An important thing in JavaScript is the possibility to do things asynchronously. Consider the following example: (example 3)

```js
async function f1() {
  console.log(1);
}
function f2() {
  console.log(2);
}
f1();
f2();
// This code will starting executing f1() while starting f2() too.
// That means you don't know if the output is: 1 2 or 2 1
```

If you have an `async` function, but you want it to run in order, that this time it is called 100% sure first, you can do:

```js
await f1();
f2();
// expected output: 1 2
```

## If-Statements
A `if`-statement checks if the expression is `true` or `false`. In case the expression is `true`, it executes it's code, else it don't.
```js
if (5 > 3) {
  console.log("1");
}
// expected output: 1
if (false) {
  console.log("2");
}
// no output
```
If you want that something happens if an other condition is true or just execute the other thing, you use `else if` or `else`:
```js
let x = 5;
if (5 > x) {
  // 5 is more than x
  console.log("1");
} else if (5 < x) {
  // 5 is not more than x AND 5 is less then x
  console.log("2");
} else {
  // neither expression was right
  console.log("3");
}
// expected output: 3
```
A similar thing is a switch. It looks if a variable has the value of an case. If so he executes the code until a `break;` or the `}` is arrived. That means even if the input is 2, if you forget the `break;` it will also execute the case 3 and if you forgot there...:
```js
let x = 2;
switch (x) {
  case 0:
    console.log("0");
    break;
  ccase 1:
    console.log("1");
    break;
  case 2:
    console.log("2");
    break;
  case 3:
    console.log("3");
    break;
  default:
    console.log("nothing");
    break;
}
// expeted output: 2
```

If you have more then one argument, you can archive it with multiple `if`s ore with `&&` and `||`:
```js
let x = 5;
if (x > 1 && x != 2) {
  // x is more than one and not euqal to 2
  console.log("1");
}
// expected output: 1
if (x > 1 || x != 5) {
  // x is more than one, not equal to 5 or both
  console.log("2");
}
// expected output: 2
```

## Loops
A loop is a structure that repeats a sequence of instructions until a specific condition is met.

The `while`-Loop, takes a boolean expression as input (e.g. `true` or `5 === 5`) and repeats the code, until this expression turns into `false`. The `do-while`-loop, does the code before checking the expression.
```js
let myBool = true;
let n = 0;
while (myBool) {
  console.log(n);
  
  n = n + 1;
    
  if (n === 5) {
    myBool = false;
  }
}
// expected output: 0 1 2 3 4
myBool = true;
n = 0;
do {
  console.log(n);
  
  n = n + 1;
    
  if (n === 5) {
    myBool = false;
  }
} while (myBool);
// expected output: 0 1 2 3 4
```


The `for`-Loop uses a new variable (which is only in the [scope](https://github.com/FlorianStrobl/Pylondocs/blob/main/TypeScript.markdown#javascripttypescript-introduction) of the loop itself), checks a boolean expression (often with the declared variable of the beginning), and does an operation at the end (often with the declared variable of the beginning).
```js
for (let i = 0; i < 5; i++) {
  // code block/main body
  console.log(i);
}
// expected output: 0 1 2 3 4
```
Statement 1 is executed (one time) before the execution of the code block. Here we declare and initialize the variable `i` with 0.

Statement 2 defines the condition for executing the code block. It is executed every time before attempting to do the code block. If it is a `true` expression, the code block will be executed, otherwise, it is skipped.

Statement 3 is executed (every time) after the code block has been executed. In this example, we add 1 to the variable `i`


The `foreach`-loop is in JavaScript a `for`-loop with the keyword `in` or `of` in it. 
- `in` loops through the properties of an [**object**](https://github.com/FlorianStrobl/Pylondocs/blob/main/TypeScript.markdown#javascripttypescript-introduction).
- `of` loops through the values of an iterable object (like an array).
```js
let person = {name: "John", name: "Doe", age: 32};
let text = "";
for (let x in person) {
  text += person[x];
} 
console.log(text); // expected output: JohnDoe25
let names = ["Peter", "Jack", "Alice"];
text = "";
for (let x of names) {
  text += x;
} 
console.log(text); // expected output: PeterJackAlice
```


## Objects
Pretty much everything is an object. Even arrays and functions. Only `string`, `number`, `boolean` and `undefined` are not objects!

## Shorthands
? :
!null
() => {}
() =>
.then()
