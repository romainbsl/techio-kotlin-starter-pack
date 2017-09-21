Function having one `String` parameter with `String` return type:

``` kotlin runnable
fun hello(s: String): String {
    return "Hello, $s !"
}
// { autofold
fun main(args: Array<String>) {
    print(hello("Kotlin"))
}
// }
```

Function with expression body:

``` kotlin runnable
fun hello(s: String) : String = "Hello, $s !"
// { autofold
fun main(args: Array<String>) {
    println(hello("My name is Bond, James Bond"))
}
// }
```

Function with expression body and inferred return type:

``` kotlin runnable
fun hello(s: String) = "Hello, $s !"
// { autofold
fun main(args: Array<String>) {
    println(hello("Mr Bond"))
}
// }
```

Function with no return value (Equivalent to Java's `void`):

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

`Unit` return type can be omitted:

``` kotlin runnable
fun printHello(s: String) {
    println("Hello, $s !")
}
// { autofold
fun main(args: Array<String>) {
    printHello("Tech.IO ! you're awesome ")
}
// }
```