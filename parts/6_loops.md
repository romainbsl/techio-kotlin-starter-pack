###  `for`

Classic `for` loop
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

`for` loop with indexes
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

### `while`

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
//}
val aniamls = listOf("dog", "cat", "snake")
var index = 0
while (index < aniamls.size) {
    println("animal at $index is ${aniamls[index]}")
    index++
} 
// { autofold
}
//}
```