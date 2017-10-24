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