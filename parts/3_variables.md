Immutable (read-only) variable:

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
// }
    val a: Int = 1  // immediate assignment
    val b = 2   // `Int` type is inferred
    val c: Int  // Type required when no initializer is provided
    c = 3       // deferred assignment

// { autofold
    println("a = $a, b = $b, c = $c")
}
// }
```

Mutable (read/write) variable:

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
//}
    var x = 5 // `Int` type is inferred
    x += 1
// { autofold
    println("x = $x")
}
//}
```