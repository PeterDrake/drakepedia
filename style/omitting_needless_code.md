# Omitting Needless Code
## Overview
> Omit needless words.
>
> Vigorous writing is concise. A sentence should contain no unnecessary words, a paragraph no unnecessary sentences, for the same
> reason that a drawing should have no unnecessary lines and a machine no unnecessary parts. This requires not that the writer make
> all sentences short, or avoid all detail and treat subjects only in outline, but that every word tell.
>
> -Strunk and White, *The Elements of Style*

Programs should be clear. To that end, they should be concise. An overly long program is tedious to write and difficult to read and maintain. A program that solves a problem with a small amount of clear code is considered *elegant*.

Crafting elegant solutions is part of the art of programming. Several techniques will steer you in the right direction.

### Don't check for conditions that must be true

Consider this method to determine whether a number is even:

```java
static boolean isEven(int n) {
    boolean result = false;
    if (n % 2 == 0) {
        result = true;
    } else if (n % 2 == 1) {
        result = false;
    }
    return result;
}
```

This is correct, but it can be more concise.

`n % 2` must either be 0 or 1. You therefore don't need the second `if` check:

```java
static boolean isEven(int n) {
    boolean result = false;
    if (n % 2 == 0) {
        result = true;
    } else {
        result = false;
    }
    return result;
}
```

### Do not store values that will never be read

Continuing the example, the initial value of `result` will never be read (it is *always* going to be set in the `if` statement) so there's no need to initialize it:

```java
static boolean isEven(int n) {
    boolean result;
    if (n % 2 == 0) {
        result = true;
    } else {
        result = false;
    }
    return result;
}
```

This is correct and shorter than the original, but you can do even better.

### Stop as soon as you know the answer

In this example, once the value of `result` has been set, it will never change. You can therefore return as soon as you know the answer:

```java
static boolean isEven(int n) {
    boolean result;
    if (n % 2 == 0) {
        return true;
    } else {
        return false;
    }
    return result;
}
```

Now the local variable `result` can be eliminated completely:

```java
static boolean isEven(int n) {
    if (n % 2 == 0) {
        return true;
    } else {
        return false;
    }
}
```

### Use shorter expressions

In the example, the method returns `true` if `n % 2 == 0` is true and `false` if `n % 2 == 0` is false. In other words, the value of `n % 2 == 0` is the value you want to return:

```java
static boolean isEven(int n) {
    return n % 2 == 0;
}
```

### Avoid redundant code

If you find the identical code in several places in your program, strongly consider defining one method and calling it in each place. [Don't repeat yourself.](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)

If you find several *similar* patches of code, see if you can figure out what's similar and what's different between them. Write a method whose parameters specify the different part.

If the identical or similar sections of code appear one right after another, a loop may be the easiest solution.

### Minimize special cases

Sometimes exactly the same code can handle more than one case. Consider the standard recursive method to compute the nth Fibonacci number:

```java
static int fibo(int n) {
    if (n == 0) {
        return 1;
    }
    if (n == 1) {
        return 1;
    }
    return fibo(n - 1) + fibo(n - 2);
}
```

Since the returned value for the two base cases is the same, they can be combined:

```java
static int fibo(int n) {
    if (n <= 1) {
        return 1;
    }
    return fibo(n - 1) + fibo(n - 2);
}
```

### Separate control from data

This method finds the sum of the four elements adjacent to element `r`, `c` in a two-dimensional array:

```java
static int neighborSum(int[][] grid, int r, int c) {
    int sum = 0;
    if (r > 0) {
        sum += grid[r - 1][c];
    }
    if (r < grid.length - 1) {
        sum += grid[r + 1][c];
    }
    if (c > 0) {
        sum += grid[r][c - 1];
    }
    if (c < grid[r].length - 1) {
        sum += grid[r][c + 1];
    }
    return sum;
}
```

The four if statements differ only in their tests and in the array indices. By storing the four directions in a separate array `offsets`, you can accomplish all of these in one loop:

```java
static int neighborSum(int[][] grid, int r, int c) {
    int[][] offsets = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}};
    int sum = 0;
    for (int[] offset : offsets) {
        int rr = r + offset[0];
        int cc = c + offset[1];
        if (rr >= 0 && rr < grid.length && cc >= 0 && cc < grid[r].length) {
            sum += grid[rr][cc];
        }
    }
    return sum;
}
```

This improvement was made by separating the control (what to do with each neighbor) from the data (the list of offsets to find neighbors).

Modifying the method to also look at the diagonal neighbors now becomes trivial; only the data has to be modified.

```java
static int neighborSum(int[][] grid, int r, int c) {
    int[][] offsets = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}, {-1, -1}, {-1, 1}, {1, -1}, {1, 1}};
    int sum = 0;
    for (int[] offset : offsets) {
        int rr = r + offset[0];
        int cc = c + offset[1];
        if (rr >= 0 && rr < grid.length && cc >= 0 && cc < grid[r].length) {
            sum += grid[rr][cc];
        }
    }
    return sum;
}
```

## Resources

-Martin, *Clean Code*


## Questions
1. :star::star: Is a shorter program always preferable?
1. :star::star: Using an array, refactor the method below to avoid the long if/else chain.
    ```java
    static String toString(int n) {
        if (n == 0) {
            return "red";
        } else if (n == 1) {
            return "orange";
        } else if (n == 2) {
            return "yellow";
        } else if (n == 3) {
            return "green";
        } else if (n == 4) {
            return "blue";
        } else if (n == 5) {
            return "indigo";
        } else {
            return "violet";
        }
    }
    ```
## Answers
1. No. The goal is clarity, and to that end we omit only *needless* code. Programmers sometimes play ["code golf"](https://en.wikipedia.org/wiki/Code_golf), solving a problem in as few characters as possible, but a program so short that it becomes cryptic serves nothing but the ego of the programmer.
1.
    ```java
    static String toString(int n) {
        String[] colors = {"red", "orange", "yellow", "green", "blue", "indigo", "violet"};
        return colors[n];
    }
    ```
    It would be even better to declare `COLORS` as a constant so that it doesn't have to be created each time `toString` is called.
    
    Strictly speaking, this code is not *precisely* equivalent to the original code, as it doesn't behave the same way if `n` not a valid index
    into `colors`. This could be remedied by adding the following between the two lines in the method above:
    ```java
    if (n < 0 || n >= colors.length) {
        n = colors.length - 1;
    }
    ```
