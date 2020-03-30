---
layout: post
title: "Design Patterns"
---

* [Basics](#basics)
* [The Observer Pattern](#the-observer-pattern)
* [References](#references)

## Basics

1. Identify the varying parts and separate them from the invariant.

2. Program to an interface (supertype), not an implementation.

    ```java
    Animal animal = new Dog();
    animal.makeSound();
    List<Integer> list = new ArrayList<Integer>();
    ```

3. Favor composition over inheritance. HAS-A can be better than IS-A.

4. The strategy pattern enables selecting an algorithm at runtime. Instead of implementing a single algorithm directly, code receives run-time instructions as to which in a family of algorithms to use.

## The Observer Pattern

1. Publishers (Subject) + Subscribers (Observers) = Observer Pattern.

2. It defines a one-to-many dependency. When the subject changes, all dependents are notified.

3. This enables loose coupling, which minimizes the interdependency between objects.

4. In Java, we can use the built-in Observable - Observer superclasses.

    ```java
    // extends Observable
    setChanged();
    notifyObservers();
    // extends Observer
    // in the constructor
    observable.addObserver(this);
    ```

5. In Java, Observable is a class, which means we have to subclass it.

## References

* [Head First Design Patterns: A Brain-Friendly Guide 1st Edition](https://www.amazon.com/Head-First-Design-Patterns-Brain-Friendly-dp-0596007124/dp/0596007124/ref=mt_paperback?_encoding=UTF8&me=&qid=1585509064)
