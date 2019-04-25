---
title: Polymorphism
date: "2019-04-17T21:35:37.121Z"
---

# Polymorphism

Polymorphism is the capability of a method, defined by a superclass (foreshadowing: or `interface`), to do different things based on the subclass(/implementation) instance that it is acting upon. It decouples a method's contract (method signature) from its implementation. (It stipulates what should be done, but allows for different implementations or calculations).

If we think of the class `Shape`, it would be an `abstract` class as there are many shapes. We want to calculate the circumference of these shapes. The problem is that the circumference for different shapes is calculated in different ways. Rather than putting all of the different methods into the `Shape` class, we put a constructor to say what we want, and force the problem of the method down into the subclasses.

A constructors looks like a method, but it has an implicit return type of the class it is defined in. It is used for setting up the initial state of an object. The name of a constructor is always the same as the name of the class. 

> Convention: When writing a class you tend to write it in the following order: fields, then constructors, then methods.

``` java
public abstract class Shape {
    public abstract double circumference();
}
```

We then create our `Shape` subclasses of `Circle`, `RightAngleTriangle` and `Rectangle`, each with their own methods for calculating their circumference.

### `Circle`

``` java
public class Circle extends Shape {
    private double radius;

    public Circle(double radius) {
        if (radius >= 0) {
            this.radius = radius;
        } else {
            System.out.println("ERROR: Radius needs to be a non-negative value.");
        }
    }

    public double circumference() {
        return 2*radius*Math.PI;
    }
}
```

This method includes a check that the radius entered is a non-negative value i.e. 0 or positive.

### `RightAngleTriangle`

``` java
public class RightAngleTriangle extends Shape {
    private double height;
    private double width;

    public RightAngleTriangle(double height, double width) {
        this.height = height;
        this.width = width;
    }

    public double circumference() {
        return height + width + hypotenuse();
    }

    private double hypotenuse() {
        return Math.sqrt(height * height + width * width);
    }
}
```

### Rectangle

``` java
public class Rectangle extends Shape {
    private double height;
    private double width;

    public Rectangle(double height, double width) {
        this.height = height;
        this.width = width;
    }


    public double circumference() {
        return 2 * height + 2 * width;
    }
}
```

### Calling the method of Circumference

We can then call the method `circumference()` on the abstract class `Shape` and its subclasses in the Main application.

``` java
public class Main {
    public static void main(String[] args) {
        Shape circle = new Circle(5); // A circle is-a shape
        Shape triangle = new RightAngleTriangle(3, 4); // A right-angle triangle is-a shape
        Shape rectangle = new Rectangle(3, 4); // A rectangle is-a shape

        // Only care that these objects are shapes, don't care exactly which Shape they are
        Shape[] shapes = {circle, triangle, rectangle};

        for (Shape shape : shapes) {
            System.out.println(shape.circumference());
        }
    }
}
```

The method `circumference()` is called for all shapes in `shapes`, and returns 3 values based on what height/width/radius has been selected and how the circumference of the individual shapes is calculated.