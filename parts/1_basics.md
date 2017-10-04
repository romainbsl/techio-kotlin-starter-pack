In this section you'll find some basics syntax to start coding with Kotlin.

### Variables

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

Using the keyword `var` allow you to declare mutable variable.

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
// }
var x = 5 // `Int` type is inferred
x += 1 // x now is equals to 6
// { autofold
    println(x)
}
// }
```

### String templates

String are made easier with Kotlin, more convinient to use, and more readable.

> Simple templates

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
// }
var name = "Kotlin"
// simple name in template:
val str = "Hello, $name !" // prints "Hello, Kotlin !"
// { autofold
    println(str)
}
// }
```

Here is a more interesting part. You may be able to invoke piece of code inside a template, avoiding lots of boilerplate code.

>String manipulation

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

>Math expression

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
// }
val left = 2
val right = 5

val sum = "+ of $left and $right gives: ${left + right}"
val sum2 = "+ of squared $left and $right gives: ${Math.pow(left.toDouble(), 2.0) + Math.pow(right.toDouble(), 2.0)}"
val multiply = "* of $left and $right gives: ${left * right}"
val div = "/ of $left and $right gives: ${left / right}"
// { autofold
println(sum)
println(sum2)
println(multiply)
println(div)
}
// }
```

### Control expressions

#### `if` statement becomes an expression

To compare two values, you would write the following code

``` kotlin runnable
fun max(a: Int, b: Int): Int {
    if (a > b) {
        return a
    } else {
        return b
    }
}
// { autofold
fun main(args: Array<String>) {
    println("max of 0 and 42 is ${max(0, 42)}")
}
//}
```

In Kotlin, `if` can be an expression, that means that you can assign a variable or return the `if` directly. Previous snippet can be write as follow

``` kotlin runnable
fun max(a: Int, b: Int): Int {
    return if (a > b) a else b
}
// { autofold
fun main(args: Array<String>) {
    println("max of 0 and 42 is ${max(0, 42)}")
}
//}
```

> Or, in idiomatic Kotlin (c.f. part 3. on Functions)

``` kotlin
fun max(a: Int, b: Int) = if (a > b) a else b
```

#### `when` expression

If you were familiar to the `switch`statement from other language like Java, you won't find it in Kotlin. It has been replaced by the `when` expression.

You can use `when` to evaluate objects and return a result.

```kotlin runnable
fun sayHello(language: String) {
  println(when (language) {
    "EN" -> "Hello!"
    "FR" -> "Salut!"
    "IT" -> "Ciao!"
    else -> "Sorry, I can't greet you in $language yet"
  })
}
// { autofold
fun main(args: Array<String>) {
  sayHello("EN")
  sayHello("FR")
  sayHello("IT")
  sayHello("NL")
}
// }
```

To go further, `when` allow you to make some condition by mixing values, ranges, Types, etc. The `when` expression will try to match with every branches sequentially and stop at the first satisfied condition.

``` kotlin runnable
fun describe(obj: Any) {
// { autofold
  print("$obj: ")
// }
  println(when (obj) {
    "EN" -> "Hello!"
    0 -> "I'm a Zero !"
    1, 2, 3, 4 -> "I'm a Fantastic !"
    is Dog -> "This is a dog: $obj, his weight is ${obj.weight}"
    is Cat -> "This is a cat: $obj, his color is ${obj.color}"
    is Animal -> "This is an aniaml: $obj"
    else -> "Sorry, I can't match $obj yet"
  })
}
// { autofold
abstract class Animal(val name: String) {
  override fun toString(): String {
    return "${this.javaClass}(name='$name')"
  }
}
class Dog(name: String, val weight: Double) : Animal(name)
class Cat(name: String, val color: String) : Animal(name)
class Snake(name: String) : Animal(name)

fun main(args: Array<String>) {
  describe("EN")
  describe(0)
  describe(2)
  describe(4)
  describe(Dog("Rex", 9.2))
  describe(Cat("Felix", "White"))
  describe(Snake("Dr Snake"))
}
// }
```

### Loops

#### For loops

`for` works on anything that's iterable. You may think of it as a foreach, like in Java's lambda or C#.

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
//}
val animals = listOf("dog", "cat", "snake")
for (aniaml in animals) {
    println(aniaml)
}
// { autofold
}
//}
```

A combination of Kotlin's features, makes `for` even more convinient. By desctructuring we can iterate over a collection with indexes:

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
//}
val animals = listOf("dog", "cat", "snake")
for ((animal, index) in animals.withIndex()) {
  println("animal at $index is $animal")
}
// { autofold
}
//}
```

#### While loops

`while` works as in many languages

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
//}
val animals = listOf("dog", "cat", "snake")
var index = 0
while (index < animals.size) {
    println("animal at $index is ${animals[index]}")
    index++
}
// { autofold
}
//}
```

### Visibility

Finally, there is some differences between Kotlin and Java when it comes to visibility.

#### For the packages (top-level functions/properties)

- By default, the visibility is `public`, which means that your declaration is visible from everywhere.
- In the contrary, a declaration made `private` will be visible inside the file containing it.
- In Kotlin, there is a new visibility modifiers, `internal`, set the declaration as visible everywhere in the same 
module.

> there is no `protected` visibility modifiers for top-level declarations

#### For the classes

- if you mark a class member as `private`, it will be visible inside this class only.
- if you mark a class member as `protected`, it will be visible inside this class and subclasses
- if you mark a class member as `internal`, it will be visible from any code inside this module (IntelliJ IDEA / 
Maven / Gradle...)
- if you mark a class member as `public`, it will be visible everywhere.
