JavaScript/TypeScript is a **object oriented programing** (OOP) language, but does this in a different way then most programming languages. Its kinda optional.
In traditional OOP languages, like C++/c# and Java, you have a class were you have your variables and functions.
```cs
class MyClass {
  int x;
  
  void MyFunction () {
    // code
  }
}
```
You have e.g. here a class named `MyClass`.
`Main` itself has to have a instance to work. You can think of it like a box for a Lego car. You can buy many of theses boxes and they all will have the same properties.
So all instances will have a value for `x`, but the value may differ from one instance to another. All instances of `MyClass` have here not just the variable `x`, but also a function called `MyFunction`. You can execut this part of the code when every you want, but if you use `x` in it, it will only use the local value of `x` (the value of `x` setted in this instance of `MyClass`).
In most OOP Languages, you have some kind of `Main` class, which has only one instance. So you start from it, and create instances of class in it, and use the variables and functions from these instances.
In other words a class describes an **object** with it's properties in form of variables and functions.

But there is one thing you have to mind all the time, there is no global value for `MyClass.x` here, because you don't have a "main instance" of `MyClass`. If you want that all instances of `MyClass` have the same value for `MyClass.x`, and when you change `MyClass.x` in e.g. the fifth instance, that it's updates the value for all instances, you have to make the variable `static`.

JavaScript/TypeScript is there a bit different. You can have functions **outside** of classes!
Additionaly you can easily say, do function 1 `f1()` but don't wait until it's finish, but do in parallele function 2. 
This is archived with the keyword `async`.
But if you have an asynchronous function, but you need it's return value for something later, 
you have use the keyword `await` to signify that the function should be executed first and after it's completly finished, do all the later code.
