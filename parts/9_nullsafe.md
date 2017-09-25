### Null safety

A feature that makes Kotlin more valuable is the management of null.

Kotlin help you to avoid the in-famous NPE (`NullPointerException`). You have to understand that 
you may have NPE, even with Kotlin, but this will happen if you don't make enough effort.
Kotlin will help you think about how you code in a good way.

In Kotlin a non-nullable string will be written `String` and a nullable will be `String?`.

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
//}
// Variable that cannot be `null` 
var str: String = "K." 
// Variable that can be null
var str2: String?
// { autofold
println(str)
println(str2)
}
//}
```

Also, Kotlin provides a way to avoid NPE, when calling multiple level of nullable values.

``` kotlin runnable
// { autofold
data class Address(val city: String, val street: String = "")
data class Person(val firstname: String, val lastname: String, val address: Address?)

fun main(args: Array<String>) {
//}
val me = Person("Romain", "Bsl", Address(city = "Nivelles"))
// Nothing will be printed for me.address?.street
println("${me.firstname} lives in ${me.address?.city} ${me.address?.street}")
// { autofold
}
//}
```

