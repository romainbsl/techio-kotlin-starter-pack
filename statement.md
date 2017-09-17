# Welcome !

In this playground, you'll find some basics examples that make Kotlin a friendly companion to play with.

# Basics

- Very known `println`
```kotlin runnable
fun main(args: Array<String>) {
    println("Tech.IO is awesome !")
}
```

- Variables
```kotlin runnable
// { autofold
fun main(args: Array<String>) {
// }
val name = "Kotlin"  // can't be changed
var age = 5          // can be changed
println(name)
println(age++)
//{ autofold
}
//}
```

- String
```kotlin runnable
// { autofold
fun main(args: Array<String>) {
// }
    val name = "Kotlin"
    println("Hello, $name")
//{ autofold
}
//}
```

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
// }
    val a: Int = 1  // immediate assignment
    val b = 2   // `Int` type is inferred
    val c: Int  // Type required when no initializer is provided
    c = 3       // deferred assignment

//{ autofold
    println("a = $a, b = $b, c = $c")

}
//}
```
