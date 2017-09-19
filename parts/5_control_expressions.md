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
//]
```

In Kotlin, IF becomes an expression, that means that it cans return values
``` kotlin runnable
fun max(a: Int, b: Int): = if (a > b) a else b
// { autofold
fun main(args: Array<String>) {
    println("max of 0 and 42 is ${max(0, 42)}")
}
//]
```

### WHEN expression