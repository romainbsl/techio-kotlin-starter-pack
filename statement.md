## Welcome !

In this playground, you'll find some basics examples that make Kotlin a friendly companion to play with.

## Defining functions



<table>
  <tr>
    <th>Function having two `Int` parameters with `Int` return type:</th>
    <th>Function with an expression body and inferred return type:</th>
  </tr>
  <tr>
    <th>
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
    </th>
    <th>
``` kotlin runnable
fun sum(a: Int, b: Int) = a + b

// { autofold
fun main(args: Array<String>) {
    println("sum of 19 and 23 is ${sum(19, 23)}")
}
// }
```
</th>
  </tr>
</table>




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

## Defining local variables

Assign-once (read-only) local variable:

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

Mutable variable:

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

## Comments
## Using string templates
## Using conditional expressions
## Using nullable values and checking for `null`
## Using type checks and automatic casts
## Using a `for` loop
## Using a `while` loop
## Using `when` expression
## Using ranges
## Using collections

## Basics

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

- Variables
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
