---
layout: post
title: "Design Patterns"
---

* [Basics](#basics)
* [The Observer Pattern](#the-observer-pattern)
* [The Decorator Pattern](#the-decorator-pattern)
* [The Factory Pattern](#the-factory-pattern)
* [The Singleton Pattern](#the-singleton-pattern)
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

6. UML:
   * ![Observer]({{https://tillchen.com}}/images/observer.png)
   * Example: ![Observer example]({{https://tillchen.com}}/images/observer_example.png)

## The Decorator Pattern

1. **The open-closed principle**: classes should be open for extension, but closed for modification.

2. Decorators have the same supertype as the object they decorate.

3. You can use one or more decorators to wrap (HAS-A) an object.

4. The decorator adds its own behavior either before and/or after delegating to the object it decorates to do the rest of the job.

5. The decorator pattern attaches additional responsibilities to an object dynamically.

6. UML:
   * ![Decorator]({{https://tillchen.com}}/images/decorator.png)
   * Example: ![Decorator example]({{https://tillchen.com}}/images/decorator_example.png)

7. `java.io` is mainly using the decorator pattern.

## The Factory Pattern

1. The factory method pattern defines an interface for creating an object, but lets subclasses decide which class to instantiate. Factory Method lets a class defer instantiation to subclasses.

2. UML:
   * ![Factory]({{https://tillchen.com}}/images/factory.png)
   * Example: ![Factory example]({{https://tillchen.com}}/images/factory_example.png)

3. **The dependency inversion principle**: Depend upon abstractions. Do not depend upon concrete classes. High-level components should not depend on low-level components; rather, they should both depend on abstractions.
    * No variables should hold a reference to a concrete class.
    * No class should derive from a concrete class.

4. The abstract factory pattern provides an interface for creating families of related or dependent objects without specifying their concrete classes.

## The Singleton Pattern

1. The singleton pattern restricts the instantiation of a class to one single instance, and provides a global point of access to it:

    ```java
    public class Singleton {
        private static Singleton uniqueInstance;
        private Singleton() {} // PRIVATE constructor
        public static synchronized Singleton getInstance() { // remove synchronized if there's no multithreading
            if (uniqueInstance == null) {
                uniqueInstance = new Singleton();
            }
            return uniqueInstance;
        }
    }
    ```

## References

* [Head First Design Patterns: A Brain-Friendly Guide 1st Edition](https://www.amazon.com/Head-First-Design-Patterns-Brain-Friendly-dp-0596007124/dp/0596007124/ref=mt_paperback?_encoding=UTF8&me=&qid=1585509064)
