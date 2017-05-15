# Introduction

In purely functional programming you don't tell the computer what to do, but rather you tell it *what stuff is*.
Example:
+ The factorial of a number is the product of all the numbers from 1 to that number
+ The sum of a list of numbers is the first number plus the sum of all the other numbers

That is expressed (defined) in the form of functions.

 You also can't set a variable to something and then set it to something else later. Hence, a function has no side-effects.
 
 A Function just takes an input and returns an output.
 Consequences
 + `Referential Transparency` - if a function is called twice with the same parameters, it's guaranteed to return the same result
 
 This allows building of more complex functions using simpler ones.
 
 Haskell is *Lazy*, won't compute until it's forced to show a result. Allows you to think of programs as a series of *transformations
 on data*.
 
 Haskell is *statically typed*. However, it's pretty neat and contains *type inference*, so you don't have to explicitly label every
 piece of code. For instance, in `a = 5+ 4`, haskell will figure out that a is an int. So
 `If a function you make takes two parameters and adds them together and you don't explicitly state their type, the function 
 will work on any two parameters that act like numbers. `
 
 ## Running Haskell Programs
 
 + You can invoke the interative mode by running `ghci`
 + If you have a file myFunctions.hs that contains your defined functions, they can be invoked from ghci by typing `:l myFunctions`
 + If you change the script, run `:l myFunctions` again or do `:r` which reloads the current script


# Getting Started 

+ Operator precedence applies just as in Java,  can be modified using parenthesis
+ Logical Operators - &&, ||, not
+ Relational Operators - ==, \= `Not equal to`, >=, <= and so forth

### Types of functions

#### Infix
```haskell
ghci> 2 + 3
5
```
In the above example, `+` is a function that is an `infix` function because its sandwiched between its parameters.

#### Prefix

Functions that arent used with numbers are usually `prefix` functions. In imperitive languages, functions are called using the function name 
followed by the parameters in parenthesis, however `prefix` **functions are called by writing the function name followed by the parameters seperated by a space**.

Examples
```haskell
ghci> succ 8
9
ghci> max 2 3
3
ghci> min 3.4 3.3
3.3
```
+ Function application has the highest precedence.

```haskell
ghci> succ 9 + max 5 4 + 1
16
```

**Note** - Prefix functions can be converted to infix by surrounding the function name with backticks

```haskell
ghci> 10 `div` 2
5
```
`div` - Integral division

#### Defining custom functions
