It's important to understand that Kotlin's collection are built on top of the Java API.
That means a lot for interoperability. 

But, Kotlin brings consistency and simplicity.

List of ...

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
//}
val numbers = listOf(1, 2, 3)
// { autofold
numbers.forEach { println(it) }
}
//}
```

Set of ...

```kotlin runnable
// { autofold
fun main(args: Array<String>) {
//}
val numbers = setOf(1, 2, 2, 3, 4, 3)
// { autofold
  numbers.forEach { println(it) }
}
//}
```

Map to ...

````kotlin runnable
// { autofold
fun main(args: Array<String>) {
//}
val map = hashMapOf(1 to "first", 2 to "second", 3 to "third")
// { autofold
map.forEach {(key, value) -> println("key: $key ; value: $value")}
}
//}
````

> Note that beyond that simplicity, Kotlin provides some cool features, essentially based on 
extensions of the Java API.

Here a sample of what Kotlin is capable of.
You may find more into the Kotlin documentation.

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
//}
  val numbers = listOf(1, 2, 3)
  // forearch with indexes
  numbers.forEachIndexed { index, it -> println("At index $index there is $it") }
  // first()
  println("numbers' first is: ${numbers.first()}")
  // last
  println("numbers' last is: ${numbers.last()}")
  // sum
  println("numbers' sum is: ${numbers.sum()}")
  // etc.
// { autofold
}
//}
```