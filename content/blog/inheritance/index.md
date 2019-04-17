---
title: Inheritance
date: "2019-04-17T21:33:32.169Z"
description: Animals are awesome.
---

# Inheritance

Classes can inherit fields and methods from another, `super`, class. In the case of `Animal` there can be many animals so `Animal` is a superclass. The subclasses for `Animal` could be `Dog`, `Cat` and `Rabbit`. As these might all have similar features that other animals may not have, they can be further divided into `Pet`s, which would be a subclass of `Animal`.

In order to show that one class is a subclass of another, you should use the following syntax after `public`/`private class`: "sub class name" + extends + "super class name".

The following sub class `Pet` inherits the methods for getting and setting `age` and `limbsCount` from its superclass `Animal`, and also has a field called name. Note that the `Pet` class cannot see the `age` or `limbsCount` fields directly, as they are private - i.e. restricted only to the `Animal` class.

``` java
public class Pet extends Animal {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

The following class `Rabbit` is a subclass of `Pet`. It inherits the getters and setters for `name` from `Pet`, and for `age` and `limbsCount` from `Pet`'s superclass `Animal`.

`Rabbit` also has a field of `fluffDegree`, which `Pet` and `Animal` do not have.

``` java
public class Rabbit extends Pet {
    private String fluffDegree;

    public String getFluffDegree() {
        return fluffDegree;
    }

    public void setFluffDegree(String fluffDegree) {
        this.fluffDegree = fluffDegree;
    }
}
```

# Using Setters and Getters

The following code will make a new cat and a new rabbit with defined `name`, `age`, `limbsCount` and `fluffDegree` for the `Rabbit` only (The `Cat` class doesn't include or inherit this field).

We could use the `Animal` class to get the `age` and `limbsCount` of the `Cat` and `Rabbit`, but to get the `name` for both as well we need to use the `Pet` class.

``` java
public class Application {

    void run() {
        Pet tom = makeCat();
        Pet bugs = makeRabbit();

        Pet[] pets = {tom, bugs};

        for (Pet pet : pets) {
            System.out.println(pet.getAge());
            System.out.println(pet.getLimbsCount());
            System.out.println(pet.getName());
        }
    }

    private Rabbit makeRabbit() {
        Rabbit rabbit = new Rabbit();
        rabbit.setName("Bugs");
        rabbit.setAge(6);
        rabbit.setLimbsCount(3);
        rabbit.setFluffDegree("quite fluffy");
        return rabbit;
    }


    private Cat makeCat() {
        Cat cat = new Cat();
        cat.setName("Tom");
        cat.setAge(5);
        cat.setLimbsCount(4);
        return cat;
    }
}
```