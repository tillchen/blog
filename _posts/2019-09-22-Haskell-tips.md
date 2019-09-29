---
layout: post
title: "Haskell tips"
---

* [Basics](#basics)
* [Lists](#lists)
* [Tuples](#tuples)
* [Types](#types)
* [Functions](#functions)
* [References](#references)

## Basics

1. How to run in ghci?

    ```shell
    ghci
    :l file
    :quit
    ```

2. How to compile?

    ```shell
    ghc -o file file.hs
    ```

## Lists

1. `:` prepends the element to a list.

    ```haskell
    1 : [2..4]
    ```

2. `++` concatenates two lists.

3. `!!` is the index operator.

    ```haskell
    [1..] !! 9 -- 10
    ```

## Tuples

1. `fst` and `snd` gives the first and second element of a tuple.

    ```haskell
    fst ("one", 1) -- "one"
    ```

## Types

1. `::` indicates the type of the left side.

    ```haskell
    42 :: Double -- 42.0
    ```

2. `:type foo` gives the type of foo.

3. `Num` is for all number types.

## Functions

1. Lambda functions;

    ```haskell
    (\x -> x^2) 2 -- 4
    ```

## References

* [Learn You a Haskell for Great Good!: A Beginner's Guide](https://www.amazon.com/Learn-You-Haskell-Great-Good/dp/1593272839/ref=sr_1_1?keywords=learn+you+a+haskell&qid=1569186473&sr=8-1)
