As you've already seen in earlier section, String are made easier with Kotlin.
Instead of concatenate, you can use templates.

Simple templates

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
// }
    var name = "Kotlin"
    // simple name in template:
    val strTemplate = "Hello, $name !"
// { autofold
    println(strTemplate)
}
// }
```

You may be able to invoke piece of code inside a template:

``` kotlin runnable
// { autofold
fun main(args: Array<String>) {
// }
    val name = "Kotlin"
    // simple template
    val strTemplate = "Hello, $name !"

    // using expression in template:
    val strTemplate2 = "${strTemplate.replace("Hello", "Welcome on this playground")}"
// { autofold
    println(strTemplate)
    println(strTemplate2)
}
// }
```