In this section you'll find some basics syntax to start coding with Kotlin.

#### Variables
Kotlin provides two way to declare variable.

- Immutable (read-only) variable:

Using the keyword `val`means that your variable could be assign just once.

>immediate assignment
``` kotlin
val a: Int = 1  
```
>variable's type can be inferred
``` kotlin
val b = 2 // `Int`
```
>deferred assignment
``` kotlin
val c: Int  // type is required when there is no initializer
c = 3
```

- Mutable (read/write) variable:

``` kotlin
var x = 5 // `Int` type is inferred
x += 1 // x now is equals to 6
```

#### String templates

String are made easier with Kotlin, more readable, at least.

- Simple templates

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
// }
var name = "Kotlin"
// simple name in template:
val str = "Hello, $name !"
// { autofold
    println(str)
}
// }
```

More interesting part, you may be able to invoke piece of code inside a template.

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
// }
val name = "Kotlin"
// simple template
val str = "Hello, $name !"

// using expression in template:
val str2 = "${str.replace("Hello", "Welcome on this playground")}"
// { autofold
    println(str)
    println(str2)
}
// }
```

#### Control expressions



#### Loops

