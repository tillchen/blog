---
layout: post
title: "Kotlin tips"
---

## Basics

1. Kotlin requires one `main` per app:

    ```kotlin
    fun main(args: Array<String>) { // the args part can be omitted
        println("Hello Kotlin!")
    }
    ```

2. Kotlin shell REPL: Read- Eval- Print- Loop

3. Shorter `if`

    ```kotlin
    println(if (x > y) "x is greater" else "x is not greater")
    ```

4. `var` vs `val`:

    * When using `var`, we can assign another value to the variable.
    * When using `val`, the reference to the object stays forever. However, if the variable is an array, the array itself can be updated.

5. Primitive types are also objects controlled by references.

6. Similar to Swift, we can define the type:

    ```kotlin
    var z: Int = 6
    var x: Long = z.toLong() // similarly, toFloat(), to Byte(), etc.
    ```

7. Arrays:

    ```kotlin
    var myArray = arrayOf(1, 2, 3)
    var myLength = myArray.size
    var explicitArray: Array<Int> = arrayOf(1, 2, 3)
    ```

8. Strings:

    ```kotlin
    var x = 42
    var myString = "x is $x"
    // When accessing a property or function of a object, use ${}
    var myArray = arrayOf(1, 2, 3)
    var arraySize = "The size if ${myArray.size}"
    var firstItem = "The first item is ${myArray[0]}"
    ```

9. Functions;

    ```kotlin
    fun foo(bar: Int): Int{ // Unit means no return value, or just omit it
        // stuff
        return 1
    }

    var result = foo(1)
    ```

## References

* [Head First Kotlin: A Brain-Friendly Guide](https://www.amazon.com/Head-First-Kotlin-Brain-Friendly-Guide/dp/1491996692/ref=sr_1_1?keywords=head+first+kotlin&qid=1567580813&s=gateway&sr=8-1)
