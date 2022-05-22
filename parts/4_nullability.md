### Nullability

A feature that makes Kotlin more valuable is its type system, and the management of nullability.

Kotlin helps you to avoid the infamous NPE (`NullPointerException`). You have to understand that 
you may have NPE, even with Kotlin, but this will happen if you don't make enough effort.
Kotlin will help you think about how you code in a good way.

In Kotlin, each type is considered `non-null`, but each of those types have a derived type nullable. Nullable types 
are followed by the `?` character. For example, a `non-null` string will be written `String` and a nullable one will be 
`String?`.

``` kotlin
// Variable that cannot be `null` 
var str: String = "K." 
// Variable that can be null
var str2: String?
```

### Dealing with nullable types

Also, Kotlin provides a way to avoid NPE, when calling multiple level of nullable values. In fact, it's not an helper
 but some compile checks that forbid you to write unsafe code. 

As you can have `non-null` types, you cannot assign `non-null` variables / parameters with `null` value.

``` kotlin
var str: String = null
// Compilation error
```

``` kotlin
fun strLength(s: String) = s.length
strLength(null)
// Compilation error
```

#### Accessing nullable values

For the following sections, let's assume the snippet:

```kotlin
data class Address(val city: String)
data class Person(val firstname: String, val lastname: String?, val address: Address?)
```

##### Safe call operator `?.`

Safe-calls allow you to call properties or functions from a nullable value. It combines a `null` check and an 
invocation in a single expression. For example, `s?.length` is equivalent to `if(s != null) s.length else null`.
So if you are trying to invoke a property or a function upon a `null` value, it will use `null` as the value, instead
 of throwing a `NPE`.
 
``` kotlin runnable
// { autofold
data class Address(val city: String)
data class Person(val firstname: String, val lastname: String?, val address: Address?)
fun main(args: Array<String>) {
//}
val me = Person("Romain", "Bsl", Address(city = "Nivelles"))
println("${me.firstname} ${me.lastname} lives in city: ${me.address?.city}; street: ${me.address?.street}")
// { autofold
}
//}
```

##### Elvis operator `?:`

When dealing with `null`s you may have to define default values instead of getting a `null`. So could write the 
following code:

``` kotlin runnable
// { autofold
data class Address(val city: String)
data class Person(val firstname: String, val lastname: String?, val address: Address?)
fun main(args: Array<String>) {
//}
val me = Person("Romain", "Bsl", Address(city = "Nivelles"))
println("${me.firstname} ${me.lastname} lives in city: ${me.address?.city}: street: ${me.address?.street ?: "[no street 
defined]"}")
// { autofold
}
//}
```

Elvis operator also accept throwing exception in the right side of it.

```kotlin
person.address?.street ?: throw IllegalStateException("For shipping purpose, the street is mandatory")
```

##### The `let` function

The `let` function help you deals with not null values. Preceded by the safe-call (`?.`), it can help you manipulate the 
values inside a lambda like:

```kotlin
// If person.address isn't null the let function returns the address.city with uppercase
person.address?.let { it.city.toUpperCase() }
```

So we could write the following extension function to get the shipping address of a Person:

``` kotlin runnable
// { autofold
import java.lang.IllegalStateException
data class Address(val city: String, val street: String? = null)
data class Person(val firstname: String, val lastname: String = "", val address: Address?)
//}
fun Person.getShippingAddress() =
    """$firstname $lastname
    |${address?.let {
      """${it.street ?: throw IllegalStateException("For shipping, street shouldn't be null")}
        |${it.city}""".trimMargin()
    }}""".trimMargin()

// { autofold
fun main(args: Array<String>) {
//}
val me = Person(firstname = "Romain", address = Address(city = "Nivelles", street = "1 rue de Nivelles"))
println(me.getShippingAddress())
val me2 = Person(firstname = "Romain", address = Address(city = "Nivelles"))
println(me2.getShippingAddress())
// { autofold
  }
//}
```
