# Functional Programming

Functional Programming (FP) and Object-Oriented Programming (OOP) are two approaches in programming. While they both aim to solve problems in programming, they have distinct methodologies and philosophies. 
This document outlines the Data Surge team's standards regarding Functional Programming.

As the name suggests, functional programming revolves around the concept of functions. In contrast to object-oriented programming, which organizes code around objects and their interactions, functional programming treats functions as the main constructs for data manipulation and analysis.

## Data Surge Team Standards

Our team embraces functional programming principles for the following reasons:

- Predictability: FP's emphasis on immutable data and pure functions leads to more predictable code behavior, making debugging and reasoning about code easier.

- Concurrency: Immutable data structures in FP make concurrent programming safer by avoiding shared mutable state.

- Testability: Pure functions facilitate easier testing as they produce the same output given the same input, simplifying unit testing.

- Debugging: The declarative style of FP often leads to shorter and more concise code, making it easier to debug and maintain.

Given these advantages, our team predominantly utilizes functional programming techniques in projects where these benefits are deemed crucial. 

While our team primarily leans towards functional programming, there are scenarios where object-oriented programming is preferred:

- Complex Systems: In complex systems, particularly in automated data pipelines, our team prefers OOP for its ability to create objects containing information and pass it through the pipeline efficiently. 

- Legacy Systems: Inheritances from legacy codebases or integration with libraries/frameworks that heavily rely on OOP may necessitate adopting object-oriented approaches.


## Core Principles of Functional Programming

Here are sojme of the Functional Programming principles that you can adopt and start using to make your code better:

### Pure Functions

In functional programming, functions are pure, meaning they consistently produce the same output for the same input, without any side effects. This predictability makes code more reliable and easier to test.

A function is pure if it satisfies two properties:

* The output only depends on the inputs, i.e. if you call it again with the same inputs, you get the same outputs. This excludes functions like `runif()` or `read.csv()` that can return different values.
* The function has no side-effects, like changing the value of a global variable, writing to disk, or displaying to the screen. This excludes functions like `print()` or `write.csv()`.

Here is an example of pure and impure functions in R:

```r
# Pure Function Example
add <- function(a, b) {
  return(a + b)
}

result <- add(3, 5)  # Calling the pure function
print(result)       # Output: 8

# Impure Function Example (with side effect)
total <- 0

impure_add <- function(a, b) {
  total <<- total + a + b  # Modifying external state (side effect)
  return(total)
}

result <- impure_add(3, 5)  # Calling the impure function
print(result)              # Output: 8

result <- impure_add(2, 5)  # Calling the impure function
print(result)              # Output: 15 ( Incorrect result )
```

Pure functions are simpler to understand and predict since they consistently produce the same output for a given input. However, they come with limitations. For example, consider performing data analysis tasks without the ability to generate random numbers or read files from disk.

Strictly speaking, R isn’t a purely functional programming language **because** it doesn’t require that you write pure functions. However, you can certainly adopt a functional style in parts of your code: you don’t have to write pure functions, but you often should.

### Concurrency and Parallelism

FP encourages stateless computations, making it easier to reason about concurrency and parallelism. Stateless computations refer to computations that do not rely on or modify shared mutable state. In other words, these computations are independent of any external variables or data that may be modified concurrently by other threads or processes. This can lead to more efficient and scalable programs, especially in modern multi-core and distributed computing environments.

### Higher-order Functions and Function Composition

FP languages typically support higher-order functions and function composition, enabling developers to write concise and expressive code by combining smaller functions into larger ones. This allows functions to be passed as arguments to other functions or returned as results. This concept enables the creation of powerful abstractions and facilitates more modular & reusable code.

Here's an example of a higher-order function in R:

```r
# Define a higher-order function named 'apply_operation'
apply_operation <- function(operation, x, y) {
  return(operation(x, y))
}

# Define two simple arithmetic functions
add <- function(a, b) {
  return(a + b)
}

multiply <- function(a, b) {
  return(a * b)
}

# Call 'apply_operation' with 'add' function as the operation
result_add <- apply_operation(add, 3, 5)
print(result_add)  # Output: 8

# Call 'apply_operation' with 'multiply' function as the operation
result_multiply <- apply_operation(multiply, 3, 5)
print(result_multiply)  # Output: 15
```

### Declarative Programming

FP promotes a declarative programming style, where the focus is on what needs to be done rather than how it should be done. This can lead to more readable and maintainable code.

Here's an example of an imperative programming s5tyle vs declarative programming style in R:

```r
# Imperative Programming Example: Calculating the sum of squares of even numbers in a list

numbers <- c(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
sum_of_squares <- 0

for (num in numbers) {
  if (num %% 2 == 0) {
    sum_of_squares <- sum_of_squares + num^2
  }
}

print(sum_of_squares)  # Output: 220

# Declarative Programming Example: Calculating the sum of squares of even numbers in a list

numbers <- c(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
sum_of_squares <- sum(numbers[numbers %% 2 == 0]^2)

print(sum_of_squares)  # Output: 220
```

### Recursion

FP allows recursion, which is a technique where a function calls itself to solve smaller instances of the same problem.

Here is an example of recursion in R:

```r
# Factorial function using recursion
factorial <- function(n) {
  if (n == 0 || n == 1) {
    return(1)
  } else {
    return(n * factorial(n - 1))
  }
}

# Calculate the factorial of 5 using recursion
result <- factorial(5)
print(result)  # Output: 120
```
### Referential Transparency

An expression can be replaced with its value without changing the program's behavior.

Here is an example of referential transparency principle in R:

```r
# Add function with referential transparency
add <- function(a, b) {
  return(a + b)
}

# Using referential transparency
x <- 3
y <- 5
result1 <- add(x, y)
result2 <- x + y

print(result1)  # Output: 8
print(result2)  # Output: 8
```

### Immutability

Instead of modifying existing data, FP promotes creating new data structures, which are never changed once created. This approach simplifies reasoning about data and helps prevent bugs caused by unintended alterations.

Here is an axample of applying immutability approach in R:

```r
# Original list
original_list <- list(a = 1, b = 2, c = 3)

# Modifying the original list directly
original_list$b <- 20

# Printing the modified list
print(original_list)  # Output: $a [1] 1, $b [1] 20, $c [1] 3

# Creating a new list based on the original list
new_list <- c(original_list, d = 4)

# Printing the new list
print(new_list)  # Output: $a [1] 1, $b [1] 20, $c [1] 3, $d [1] 4

# Printing the original list again
print(original_list)  # Output: $a [1] 1, $b [1] 20, $c [1] 3
```

## Functional Programming in R

R, at its heart, is a functional language. This means that it has certain technical properties, but more importantly that it lends itself to a style of problem solving centred on functions. However, it's important to note that R is not a pure functional programming language. Therefore, applying pure functional programming principles in R requires self-discipline. Nevertheless, these efforts are worth it, because pure functions are easier to debug, extend and document.

In R, functions (also known as closures) are first-class objects, primarily because in R *everything* is a first class object. This means that functions can be treated much like any other R object (a vector or list or dataframe). Importantly,

* Functions can be passed as arguments to other functions. This is very handy for the various apply functions, like `lapply()` and `sapply()`.
* Functions can be nested, so that you can define a function inside of another function.
* Functions and all other objects can be values of functions as well as components of lists.
* Functions can be assigned to variables.
* Functions can be returned as a result of a function.

If you’re familiar with C, these features might appear a bit strange. However, they are really important in R and can be useful for data analysis.

## Functional Programming in Python 

While object-oriented programming is a cornerstone of Python's design, Python does not force the use of object-oriented features. 
Python is a multi-paradigm language that supports several different approaches: you can write programs or packages that are largely procedural, object-oriented, or functional. 

Similarly to R, functions in Python are first-class objects (also called first-class citizens). In addition, Python leverages anonymous functions with the lambda keyword and decorators. Python also provides built-in support for many functional programming constructs such as map, filter, and reduce, which allow for concise and expressive manipulation of collections. You can learn more about these features here: https://realpython.com/python-functional-programming/

Overall, while Python is known for its versatility in supporting multiple programming paradigms, its support for functional programming enables developers to leverage the benefits of FP techniques to write clean, efficient, and scalable code. 
