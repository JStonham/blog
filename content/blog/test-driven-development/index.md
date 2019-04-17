---
title: Test Driven Development
date: "2019-04-17T21:43:03.284Z"
---

## Test Driven Development (TDD)

TDD rules:
1. RED. Write as little test code as possible to make your production code fail.
1. GREEN. Write as little production code as possible to make your test pass.
1. REFACTOR. Optimise your code for readability without changing its behaviour.

### TDD with Fibonacci

First, create a test class that calls the intended target class:

``` java
public class FibonacciTest {
    
    Fibonacci target = new Fibonacci();

}
```

Then create that target class.

``` java
public class Fibonacci {
}
```

Second, add a simple method to the test class.

``` java
public class FibonacciTest {

    Fibonacci target = new Fibonacci();

    public int shouldBe(int i) {
        target.get(i);
    }

}
```

Then create the method `get` in the target class.

``` java
public class Fibonacci {

    public int get() {
        return 0;
    }
    
}
```

Third, create a simple test in the test class.

``` java
import static org.junit.Assert.assertEquals;

public class FibonacciTest {

    Fibonacci target = new Fibonacci();

    @Test
    public int shouldBe(int i) {
        assertEquals(1,target.get(i));
    }

}
```

Then modify the method in the target class.

``` java
public class Fibonacci {

    public int get() {
        return 1;
    }
    
}
```

Fourth, add more tests/assertions to the test class.

``` java
import static org.junit.Assert.assertEquals;

public class FibonacciTest {

    Fibonacci target = new Fibonacci();

    @Test
    public int shouldBe(int i) {
        assertEquals(1,target.get(i));
        assertEquals(3,target.get(i));
    }

}
```

Then refactor the test class.

A private method called `shouldBe()` can be created.

``` java
import static org.junit.Assert.assertEquals;

public class FibonacciTest {

    Fibonacci target = new Fibonacci();

    @Test
    public int shouldBe(int i) {
        shouldBe(1, 1);
        shouldBe(3, 2);
    }

    private int shouldBe(int index, int expected) {
        assertEquals(expected, target.get(index));
    }
}
```

Now we can update the target class.

``` java
public class Fibonacci {

    public int get(int n) {
        if (n < 3) {
            return 1;
        }
        return 2;
    }
}
```

Then further tests/assertions can be added to the test class.

``` java
import static org.junit.Assert.assertEquals;

public class FibonacciTest {

    Fibonacci target = new Fibonacci();

    @Test
    public int shouldBe(int i) {
        shouldBe(1, 1);
        shouldBe(2, 1);
        shouldBe(3, 2);
        shouldBe(4, 3);
        shouldBe(5, 5);
    }

    private int shouldBe(int index, int expected) {
        assertEquals(expected, target.get(index));
    }
}
```

Finally, update the target class so that it will work for any number tested.

``` java
public class Fibonacci {

    int get(int n) {
        if (n < 3) {
            return 1;
        }
        return get(n - 2) + get(n - 1);
    }
}
```