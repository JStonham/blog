---
title: Abstract Classes and Interfaces
date: "2019-04-17T21:37:03.284Z"
---

# Abstract Classes

Classes can be defined as `abstract` classes. This means that the class is can fill in some, often most, of the blanks, but does not necessarily make sense to exist as a thing on its own.

Of the following classes:

- `Animal`
- `Pet`
- `Dog`
- `Cat`
- `Rabbit`

`Animal` and `Pet` should be considered abstract as there are many animals and many animals can be pets.

In order to define a class as abstract simply use the `abstract` keyword before defining the class.

``` java
public abstract class Animal {
}
```

``` java
public abstract class Pet extends Animal {
}
```

# Interfaces

To change an abstract class to an interface remove 'abstract' from class and methods and change 'class' to 'interface'. Public can be removed from methods as all interface methods are implicitly public.

### `Shape` Interface

``` java
public interface Shape {
    double circumference();
}
```

### `Rectangle` implementation of `Shape` Interface

Subclasses become implementations so change 'extends' to 'implements'.

``` java
public class Rectangle implements Shape {
    // (...)
}
```

# Differences between Abstract Classes and Interfaces in Java

- Both Abstract Classes and Interfaces are used for varying degrees of abstraction (defining relevant/irrelevant details and showing/hiding them from users).
- Abstract Classes are used for partial abstraction whereas Interfaces are used for full abstraction.
- As Abstract Classes are used for partial abstraction, they can have both abstract and concrete methods. Since Interfaces are used for full abstraction, they can only have abstract methods.
- In an Abstract Class, the 'abstract' keyword is mandatory to declare a method as abstract. In an Interface, the 'abstract' keyword is optional (redundant) as all Interface methods are abstract anyway.

Perhaps the biggest differences are:
1. An Abstract Class can extend only one class at a time whereas an Interface can extend multiple interfaces at the same time.
2. An Abstract Class can extend a concrete (regular) class or an abstract class, and it can also implement an interface. An interface can only extend another interface.

When we talk about abstract classes we are defining characteristics of an object type; specifying what an object is.

When we talk about an interface and define capabilities that we promise to provide, we are talking about establishing a contract about what the object can do.

For example, the following can all be animals: cat, dog, hippo, meerkat. However, only a cat or dog would lick people. In this case we could make `Animal` an abstract class where the animals can inherit certain characteristics, and `PeopleLicker` as an interface, which the cat and the dog would implement.