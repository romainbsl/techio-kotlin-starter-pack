Function having two `Int` parameters with `Int` return type:

``` kotlin runnable
fun sum(a: Int, b: Int): Int {
    return a + b
}

// { autofold
fun main(args: Array<String>) {
    print("sum of 3 and 5 is ")
    println(sum(3, 5))
}
// }
```

Function with an expression body and inferred return type:

``` kotlin runnable
fun sum(a: Int, b: Int) = a + b

// { autofold
fun main(args: Array<String>) {
    println("sum of 19 and 23 is ${sum(19, 23)}")
}
// }
```

Function returning no meaningful value:

``` kotlin runnable
fun printSum(a: Int, b: Int): Unit {
    println("sum of $a and $b is ${a + b}")
}

// { autofold
fun main(args: Array<String>) {
    printSum(-1, 8)
}
// }
```

`Unit` return type can be omitted:

``` kotlin runnable
fun printSum(a: Int, b: Int) {
    println("sum of $a and $b is ${a + b}")
}

// { autofold
fun main(args: Array<String>) {
    printSum(-1, 8)
}
// }
```
