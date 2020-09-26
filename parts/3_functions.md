### It's all about `fun` !

In Kotlin function are define by the keyword `fun`.

You can declare a function like this:

```kotlin runnable
fun myFirstFunction() {
  println("My first function")
}
// { autofold
fun main(args: Array<String>) {
  myFirstFunction()
}
// }
```

#### Function with parameters

Here is a function that accept one `String` parameter and return an `Int`:

``` kotlin runnable
fun lenght(s: String): Int {
    return s.lenght
}
// { autofold
fun main(args: Array<String>) {
    print(lenght("Kotlin"))
}
// }
```

#### Function with expression body:

For simple and concise functions that returns values, we can replace the block body (between curly braces) by an 
expression body, with a single `=`:

``` kotlin runnable
fun hello(s: String) : String = "Hello, $s !"
// { autofold
fun main(args: Array<String>) {
    println(hello("My name is Bond, James Bond"))
}
// }
```

You also can omit the return type by writing:
 
``` kotlin
fun hello(s: String) = "Hello, $s !"
```

#### Function with no return value (Equivalent to Java's `void`):

``` kotlin runnable
fun printHello(s: String): Unit {
    println("Hello, $s !")
}
// { autofold
fun main(args: Array<String>) {
    printHello("Tech.IO")
}
// }
```

As any return type, `Unit` can be omitted:

``` kotlin
fun printHello(s: String) {
    println("Hello, $s !")
}
```

#### Default and Named Arguments

In Java, it happens that you need to overload functions to handle multiple signature. To avoid breaking APIs you also
 end by calling a unique function with default arguments, like the following snippet:
 
```java
public void Constructor(String arg1) {
 Constructor(arg1, null, null); 
}
public void Constructor(String arg1, String arg2) {
 Constructor(arg1, arg2, null); 
}
public void Constructor(String arg1, String arg2, String arg3) {
  // Computation Here
}
```

Kotlin allow you to write the same code more concisely:

```kotlin
fun Constructor(arg1 : String, arg2 : String? = null, arg3 : String? = null) {
// Computation Here
}
``` 

So, you'll be able to call the `Constructor` function with:

```kotlin
Constructor("abc")
Constructor("abc", "def")
Constructor("abc", "def", "hij")
```

As you may notice, this can be confusing, as the parameters all are strings, named `arg..`. Kotlin provide a syntax 
helper that give you the ability to name arguments in the function call:

```kotlin
Constructor(arg1 = "abc")
Constructor(arg1 = "abc", arg2 = "def")
Constructor(arg1 = "abc", arg2 = "def", arg3 = "hij")
```

> If you name one argument, you need to name all the others

#### Variable number of arguments

If you don't how much arguments will be passed to a function, you can use the `vararg` keyword. That allows you to 
define a variable number of parameters, with the same type.  

You can also pass an array to a `vararg` argument, with the `*` notation.

```kotlin runnable
fun sum(vararg values: Int) = values.sum()

fun main(args: Array<String>) {
  print("sum(1, 2, 3) = ")
  println(sum(1, 2, 3))
  print("sum(11, 22, 33, 44, 55) = ")
  println(sum(11, 22, 33, 44, 55))
  val array = intArrayOf(33, 44)
  print("sum(1, 2, *array, 5)= ")
  println(sum(1, 2, *array, 5))
}
```

> **Tips from documentation**: 
  Only one parameter may be marked as vararg.
  A function's parameter marked as `vararg` should be the last parameter
  
#### Infix notation

Infix notation allow you to simplify your code by calling function without `.` or `()`, like:

```kotlin
1 add 2
```

```kotlin runnable
infix fun Int.add(value: Int) = this + value

fun main(args: Array<String>) {
  print("1 add 1 = ")
  println(1 add 1)
  println("is the same as: ")
  print("1.add(1) = ")
  println(1.add(1))
}
```

This was the basics about functions in Kotlin. Now we'll some really nice features.
