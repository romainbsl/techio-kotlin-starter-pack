### IF ... as an expression

Classic IF statement
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

In Kotlin, IF becomes an expression, that means that it cans return values
``` kotlin runnable
fun max(a: Int, b: Int) = if (a > b) a else b

// { autofold
fun main(args: Array<String>) {
    println("max of 0 and 42 is ${max(0, 42)}")
}
//}
```

### WHEN expression

You can use `when` to evaluate objects.

``` kotlin runnable
fun describe(obj: Any): String =
    when (obj) {
      is Dog -> "This is a dog: $obj, ${obj.weight}"
      is Cat -> "This is a cat: $obj, ${obj.color}"
      is Animal -> "This is an aniaml: $obj"
      else -> "Unknown"
}

// { autofold
open class Animal(val name: String) {
  override fun toString(): String {
    return "${this.javaClass}(name='$name')"
  }
}
class Dog(name: String, val weight: Double) : Animal(name)
class Cat(name: String, val color: String) : Animal(name)
class Snake(name: String) : Animal(name)

fun main(args: Array<String>) {
  println(describe(Dog("Rex", 9.2)))
  println(describe(Cat("Felix", "White")))
  println(describe(Snake("Dr Snake")))
  println(describe(1))
  println(describe("Hello"))
  println(describe(1000L))
  println(describe(2))
  println(describe("other"))
}
//}
```