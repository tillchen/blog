---
layout: post
title: "Kotlin tips"
---
## Table of Contents

* [Table of Contents](#table-of-contents)
* [Basics](#basics)
* [OOP](#oop)
* [References](#references)

## Basics

1. Kotlin requires one `main` per app:

    ```kotlin
    fun main(args: Array<String>) { // the args part can be omitted
        println("Hello Kotlin!")
    }
    ```

2. Shorter `if`

    ```kotlin
    println(if (x > y) "x is greater" else "x is not greater")
    ```

3. `var` vs `val`:

    * When using `var`, we can assign another value to the variable.
    * When using `val`, the reference to the object stays forever. However, if the variable is an array, the array itself can be updated. (Similar to `let` in Swift)

4. Primitive types are also objects controlled by references.

5. Similar to Swift, we can define the type:

    ```kotlin
    var z: Int = 6
    var x: Long = z.toLong() // similarly, toFloat(), to Byte(), etc.
    ```

6. Arrays:

    ```kotlin
    var myArray = arrayOf(1, 2, 3)
    var myLength = myArray.size
    var explicitArray: Array<Int> = arrayOf(1, 2, 3)
    ```

7. Strings:

    ```kotlin
    var x = 42
    var myString = "x is $x"
    // When accessing a property or function of a object, use ${}
    var myArray = arrayOf(1, 2, 3)
    var arraySize = "The size if ${myArray.size}"
    var firstItem = "The first item is ${myArray[0]}"
    ```

8. Functions;

    ```kotlin
    fun foo(bar: Int): Int{ // Unit means no return value, or just omit it
        // stuff
        return 1
    }

    var result = foo(1)

    fun max(a: Int, b: Int): Int = if (a > b) a else b // also works
    ```

9. Loops:

    ```kotlin
    for (x in 1..100) println(x) // end inclusive
    for (x in 1 until 100) println(x) // not end inclusive
    for (x in 15 downTo 1) println(x)
    for (x in 1..100 step 2) println(x)
    for (item in items) println(item)
    ```

10. Input:

    ```kotlin
    val userInput = readLine()
    ```

## OOP

1. Example class:

    ```kotlin
    class Dog(val name: String, var weight: int, val breed: String) {
        var temperament: String = ""
        // All properties must be initialized.
        // Or:
        // lateinit var temperament = String
        fun bark() {
            println("Woof!")
        }
    }
    ```

2. Custom getters and setters:

    ```kotlin
    ...
    val weightInKgs: Double
        get() = weight / 2.2
    var weight = weightParam
        set(value) {
            if (value > 0) field = value // field is a keyword
        }
    ...
    ```

3. In fact, the complier adds getters and setters automatically:

    ```kotlin
    var myProperty: String
        get() = field
        set(value) {
            field = value
        }
    ```

## References

* [Head First Kotlin: A Brain-Friendly Guide](https://www.amazon.com/Head-First-Kotlin-Brain-Friendly-Guide/dp/1491996692/ref=sr_1_1?keywords=head+first+kotlin&qid=1567580813&s=gateway&sr=8-1)
