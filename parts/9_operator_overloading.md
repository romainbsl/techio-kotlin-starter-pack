### Operator Overloading

Kotlin allows us to overload some operators on any object we have created, or that we know of (through [extensions][]). 
The concept of [operator overloading][op_overloading] provides a way to invoke functions to perform arithmetic 
operation, equality checks or comparison on whatever object we want, through symbols like `+`, `-`, `/`, `*`, `%`,
 `<`, `>`. But, obviously, those overloading should be defined when it make sense to use them.
 
For the following parts, let's assume we have the `data class`:  

```kotlin
data class Point(val x: Double, val y: Double)
```

### Arithmetic operators

To overload the `+` operator we need to implement the function `plus`, with the keyword `operator`. This function 
takes one parameter of any kind, even it make sense in most cases to use the same type.

```kotlin
// Here how to provide `+` operator on our object Point
operator fun plus(p: Point) = Point(this.x + p.x, this.y + p.x)
// return type is inferred to Point
```

To go further we can apply all the following operator overloading on the object `Point`.

|expression|function called|
|------------|----------|
| p1 `+` p2 | p1.`plus`(p2) |
| p1 `-` p2 | p1.`minus`(p2) |
| p1 `*` p2 | p1.`times`(p2) |
| p1 `/` p2 | p1.`div`(p2) |
| p1 `%` p2 | p1.`rem`(p2) |
| p1`++` | p1.`inc`() |
| p1`--` | p1.`dec`() |

Here the implementation on our previous `data class`:

```kotlin runnable
data class Point(val x: Double, val y: Double) {
  operator fun plus(p: Point) = Point(x + p.x, y + p.y)
  operator fun minus(p: Point) = Point(x - p.x, y - p.y)
  operator fun times(p: Point) = Point(x * p.x, y * p.y)
  operator fun div(p: Point) = Point(x / p.x, y / p.y)
  operator fun inc() = Point(x + 1, y + 1)
  operator fun dec() = Point(x - 1, y - 1)
}

// { autofold
val running: (String, String, String) -> String = {first, op, second -> "Running $first $op $second = "}
fun main(args: Array<String>) {
  var one = Point(2.0, 3.0)
  var two = Point(3.0, 2.0)
  println(running(one.toString(), "+", two.toString()) + (one + two))
  println(running(one.toString(), "-", two.toString()) + (one - two))
  println(running(one.toString(), "*", two.toString()) + (one * two))
  println(running(one.toString(), "/", two.toString()) + (one * two))
  println(running(one.toString(), "++", "") + (++one))
  println(running(two.toString(), "--", "") + (--two))
}
// }
```

Note that those examples are quiet simple, you may be able to implement more complex operator, depending on your own 
object's definition.


### Equality and inequality

As a Java developer, I always felt confused about equality, sometimes you have to use `==` / `!=` (on primitives), 
sometimes you have to use `equals()`. (reminder, the usage of `==`/ `!=` on non-primitive checks the reference of the
 object not its value).
 
Kotlin makes it more simple by reserving the symbols `==`and `!=` to check the objects' values (to check 
references you may use `===`/ `!==`).

To overload the equality (and inequality) checks, you may override the well known `equals()` function.

```kotlin
override fun equals(other: Any?): Boolean {
  if (other == null || 
      other !is Point ||
      x != other.x || y != other.y) return false
    
  return true
}
```   

> **Exception**: As you may know, in Kotlin objects can be non-null. In that case, `x == null` will always be `false`, 
and `equals` will never be called. 

> **Tips**: As you may know, in Kotlin, data class already implements `eqauls()`, as other useful functions (`getters/setters`, `hashCode()`, `copy()` and `toString()`)

If you want to know more about operator overloading, please check at my [full article](https://tech.io/playgrounds/6847/kotlin-operator-overloading) on this subject.