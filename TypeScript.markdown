JavaScript/TypeScript is a object oriented programing language (OOP), but does this in a different way then most programming languages. Its kinda optional.
In traditional OOP languages, like C++/c# and Java, you have a class were you have your variables and functions.
```cs
class Main {
  int x = 5;
  
  void Function () {
  
  }
}
```
Your class has some values saved like `Main.x` (a variable from type Integer with the value 5) and some functions like `Main.Function()`.
You describe a obejects with it's values and things, it can do. But be carefull, because you can instaniate many versions of `Main`. They have then on `Main.x` different values and you can choose when you want to use the function `Main.function`.
There is no global value for `Main.x` here, because you don't have a "main instance" of `Main`. If you want to have all the instances of `Main` the same value for `Main.x` and when you change `Main.x` in e.g. the fifth instance that it's updates the value for all instances, you have to make it `static`.
JavaScript/TypeScript is there a bit different. You can have functions OUTSIDE of classes!
Additionaly you can easily say, do function 1 `f1()` but don't wait until it's finish, but do in parallele function 2. 
This is archived with the keyword `async`.
But if you have an asynchronous function, but you need it's return value for something later, 
you have use the keyword `await` to signify that the function should be executed first and after it's completly finished, do all the later code.
