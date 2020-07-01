This chapter will talk about how to work with classes in Kotlin, and what's great about them.

### Classes

As in Java or C#, classes are declared with the keyword `class`

```kotlin
class Book {}
```

> You're allowed to omit curly braces if class is empty

```kotlin
class Book
```

#### Constructors

In Kotlin, a class can have a primary constructor and many secondary constructors.

- Primary constructor

A primary constructor is part of the class header declaration.

```kotlin
class Book constructor(author: String) {}
```

Any many cases `constructor` keyword can be omitted. 

```kotlin
class Book(author: String) {}
```

Primary constructor can't contains any logic. To help with that you can declare an `init` block.

```kotlin  runnable
class Book(author: String){
  init {
    println("init block for Book authored by $author")
  }
}
// { autofold
fun main(args: Array<String>) {
  Book("Chuck Palahniuk")
}
// }
```

- Secondary constructor

Sometimes, you may need to initialize your object in multiple ways

```kotlin
class Book(author: String) {
    constructor(author: String, publisher: Publisher): this(author) {
    publisher.books.add(this)
  }
}
```

> class initialization

To initialize you don't need any `new` keyword, just call the constructor

```kotlin
val fightClub = Book("Chuck Palahniuk")
val kotlinInAction = Book("Dmitry Jemerov and Svetlana Isakova", Publisher("Manning"))
```

#### Properties

As in C#, Kotlin have properties to describe classes. You can make them either `val`or `var`.

```kotlin
class Person {
  val name: String
  val birthDate: LocalDate
  var address: Address
}
```

Under the hood, Kotlin handles Getters and Setters. But, you also can override those Getters and Setters.

```kotlin
var name: String
    get() = this.toString()
    set(value) {
      field = value
      println("name updated: $value")
    }
```

### Inheritance

In Kotlin:
- all types are derived from `Any`.
- classes are `final` by default, that means if you need to inherit from a class, it has to be `open`.

```kotlin
open class Animal(val name: String)
class Dog(name: String): Animal(name)
class Cat: Animal {
  constructor(name: String): super(name)
  constructor(name: String, color: String): super(name)
}
```

As in other languages you can override methods super classes' methods.
In opposition to Java, the `override` keyword is mandatory.

```kotlin
open class Animal(val name: String) {
  fun eat() {} // can't be overriden
  open fun walk() {} // can be overriden
}
class Dog(name: String): Animal(name) {
  override fun walk() {}
}
```

### Data Classes

In every languages, when you want to create object that carry data, you always have to write boilerplate code to 
compare, print or even duplicate objects.
To get rid of that, Kotlin introduce the `data class` concept.

According to the following snippet, in one line, the compiler will create extra members as:

- `equals()` / `hashCode()`
- `toString()`
- `copy()`

```kotlin runnable
data class Cat(val name: String, val color: String)
// { autofold
fun main(args: Array<String>) {
  val felix = Cat("Felix", "White")
  val loki = Cat("Loki", "Black/White")
  println("felix prints: $felix")
  println("felix's hashCode: ${felix.hashCode()}")
  println("loki prints: $loki")
  println("felix's hashCode: ${loki.hashCode()}")
  println("Does felix == loki ? ${felix == loki}")
}
// }
```

> **Tips**: Since v1.1, data class can inherit from other classes, but still can't be inherited

### Sealed Classes

Kotlin introduced an other type of class, `sealeed class`. A sealed class, is a class that can be inherit by a 
restricted class set. By definition, a sealed class is `abstract`, that means it can't be directly instantiate.
All derived classes have to be in the same file than the sealed class.

```kotlin
sealed class ArithmeticExpression 
data class Const(val number: Double) : ArithmeticExpression()
data class Sum(val left: ArithmeticExpression, val right: ArithmeticExpression) : ArithmeticExpression()
```

Accordingto the below snippet, you should be able to evaluate an `ArithmeticExpression` without having to implement a 
fallback.

```kotlin runnable
fun evaluate(expr: ArithmeticExpression): Double = when (expr) {
  is ArithmeticExpression.Const -> expr.number
  is ArithmeticExpression.Sum -> evaluate(expr.left) + evaluate(expr.right)
  // else branch is not needed, because all possibilities are covered
}
// { autofold
fun main(args: Array<String>) {
  println("Sum of 1 + 2 is " +
      "${
      evaluate(
          ArithmeticExpression.Sum(
              ArithmeticExpression.Const(1.0),
              ArithmeticExpression.Const(2.0))
      )
      }")
}

sealed class ArithmeticExpression {
    data class Const(val number: Double) : ArithmeticExpression()
    data class Sum(val left: ArithmeticExpression, val right: ArithmeticExpression) : ArithmeticExpression()
}
// }
```

For more details on `sealed class` please check at the [Simon Wirst's playground](https://tech.io/playgrounds/6539/kotlin-sealed-classes-in-action)

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
