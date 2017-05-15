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
 
 # Running Haskell Programs
 
 + You can invoke the interative mode by running `ghci`
 + If you have a file myFunctions.hs that contains your defined functions, they can be invoked from ghci by typing `:l myFunctions`
 + If you change the script, run `:l myFunctions` again or do `:r` which reloads the current script
