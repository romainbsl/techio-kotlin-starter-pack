### Type inference

Kotlin is a statically type language. Regarding to that specification, that means that the compiler will know what is 
the type of a variable or the return type of a function. That's why you can write `val str = "hello"` instead of 
`val str : String = "hello"`, or even `fun sum(ints: Lst<Int>) = ints.sum()` instead of `fun sum(ints : List<Int>) : 
Int = ints.sum()`. In a lot of cases you will be allowed to omit the declaration type, so your code should be more 
concise. 

### Type checks

If you do Java, you may know the keyword `instanceof` that help you defined what is the type of the object you're 
working on. In Kotlin, we use the keyword `is`, or `!is` for the negation. 

```kotlin runnable
fun isString(obj: Any) {
  println("Object $obj is ${if (obj !is String) "not" else ""} a String")
}

fun main(args: Array<String>) {
  isString("ABC")
  isString("10")
  isString(10)
}
```

### Smart casts

The `is` and `!is` operators help us to avoid type checks along code block. If a variable is checked as a `String`, 
the code block that follow that check will consider the variable as a `String` without casting it. This allow you to 
call function on variable without be worried of any casting action. It works as well with nullable variable. 

```kotlin
if (x is String) print(x.length) // x is automatically cast to String
```

```kotlin
val x : String? // nullable String
// Computation... 
print(x?.length) // x might be null, so we use the `?.` operator 
if (x != null) print(x.length) // in that case x is automatically cast to non-null String
```

```kotlin
when (x) {
    is Int -> print(x + 1)
    is String -> print(x.length + 1)
    is IntArray -> print(x.sum())
}
```