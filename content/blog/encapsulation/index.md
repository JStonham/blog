---
title: Encapsulation
date: "2019-04-17T21:31:03.284Z"
---

# Encapsulation

Encapsulation is one of the three main concepts in object oriented programming (the other two being 'inheritance' and 'polymorphism'). Encapsulation is about hiding the internal state and implementation details of how a class does what it does from other classes. The simplest (to the extent that it's basically redundant) example of encapsulation in Java is hiding fields behind dedicated methods for accessing and modifying the fields. Instead of just accessing the fields directly you have to call a method to get them. These fields can then only be accessed through defined `set` and `get` methods.

There are four levels of visibility modifiers: `public`, `protected`, package-private (the default) and `private`. For all except package-private the keyword must be used at the start. For package-private there is no keyword. For now just use `public` and `private`.

In the following example, the `public class Animal` has `private` fields of `age` and `limbsCount`, which can only be changed by using the defined `set` methods (`setLimbsCount()` and `setAge()`) and retrieved through the `get` methods (`getLimbsCount()` and `getAge()`).

``` java
public class Animal {
    private int age;
    private int limbsCount;

    public int getLimbsCount() {
        return limbsCount;
    }

    public void setLimbsCount(int limbsCount) {
        this.limbsCount = limbsCount;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        if (age >= 0) {
            this.age = age;
        }
    }
}
```

When writing the `set` method, remember to include `void` after `public` to let Java know you don't want to return any values. Also, to allow you to use the same word multiple times, write 'this.' before the field name to let Java know which word in the method links to the field and which variable refers to the input parameter.

When using the `get` method, remember to list the data type after `public`, and tell Java what to return.

Note - the `get` keyword is fine for get methods involving all data types except `boolean`. For `boolean`s, instead of `getFoo` use `isFoo`.