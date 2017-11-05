### Ranges 

Kotlin provide a way to deal with value ranges, so you might be able to simply create and manipulate ranges 
effortlessly.


Control if a value belong or not to a range of elements.

``` kotlin runnable
// { autofold
fun checkRange(i: Int) {
//}
if (i in 1..10) { // equivalent of 1 <= i && i <= 10
    println("$i belongs to the range 1..10")
}
// { autofold
}
fun main(args: Array<String>) {
  checkRange(1)
  checkRange(5)
  checkRange(7)
  checkRange(11)
}
//}
```

Iteration over ranges

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
//}
for (i in 1..5) println("square($i) gives ${i * i}")
// { autofold
}
//}
```

Reverse iteration over ranges

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
//}
for (i in 5 downTo 1) print(i)
// { autofold
}
//}
```

Iterating over ranges ... step by step

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
//}  
for (i in 1..10 step 2) print(i)
// { autofold 
println() 
// }
for (i in 10 downTo 1 step 2) print(i)
// { autofold
}
//}
```

Range with exclusion

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
//}  
for (i in 1 until 5) print(i)
// { autofold
}
//}
```
