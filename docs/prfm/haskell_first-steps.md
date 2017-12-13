# Haskell Introduction
- `Cons`: Constructor
- `[1, 2, 3] !! 1`: Take second element from list
    - Infix, compared to most other list functions!
- Prefix function application has preference
- Convention: Name list arguments with suffix `s`, e.g. `xs`

## Types and Classes
- Every well-formed expression has a type
- `e :: t`: expression `e` produces a value of `t`
- Types are automatically determined by type inference at compile time
    - It will always determine the most general type (complete and total type inference)
- A list is a sequence of values of the *same* type
    - type of a list is e.g. `[Bool]` or `[Char]`
- Function types: `f :: t1 -> tResult`
- *Curried* Functions: Functions which take "multiple" arguments, i.e. one argument at a time, e.g. `add'` or `map`
    - The arrow `->` associates to the right
- Polymorphic functions: Type contains one or more *type variables* (like generics)
- Type constraints
    - e.g. `(+) :: Num a => a -> a -> a`
    - `Num a` is a type constraint and can only occur once in a type

### Basic Types
- `Int`: Fixed-precision integer
- `Integer`: arbitrary-precision integer

### Type Classes
- `Num`: Numeric Types
- `Eq`: Equality types (e.g. for `(==)`)
- `Ord`: Ordered types (for comparison)

## Defining Functions
### Conditional Expression
- `abs n = if n >= 0 then n else -n`
- Can be nested
- Must always have an `else` branch (to be unambiguous)
- Guarded Equations (syntactic sugar):
```haskell
abs n
    | n >= 0 = n
    | otherwise = -n
```

### Pattern Matching
- Define functions with patterns
- `_` is a wildcard
- Conditions are evaluated top-down
- Definition should be exhaustive
``` haskell
True && True = True
_ && _ = False
```

### List Patterns
- `:` is the cons operator to concatenate two elements
- A list is defined as:
```haskell
= [] | (_:_)
```
- `[1, 2, 3]` is syntactic sugar for ´1: (2: (3: []))´

### Lambda expressions

⁻ `\ x -> x + x`
- `\` is \(\lambda\)
- \(\lambda x. (x+1) * 2\) is `(*2).(+1)` in "point-free" form

### Operator Sections
- Infix operators can be written as a curied functions in `()`
    - like `(+) 1 2`
- Selections: `(1+)` = \(\lambda x. 1 + x\) is a "plus one" function

## List Comprehension
- `[x^2 | x <- [1..5]]`
- `x <- [1..5]` is a generator that generates values for `x`
- `[(x, y) | x <- [1, 2, 3], y <- [4, 5]]`
    - `[(1,4),(1,5),(2,4),(2,5),(3,4),(3,5)]`
    - Notice: the `y` generator is used up first
- Think of later generators as deeper nested loops
- later generators can therefore depend on earlier ones
- Defining guards: `[x | x <- [1 .. 10], even x]`

### Zip function
- Map tWo lists to a list of pairs until one of the two lists ends
    - `zip :: [a] -> [b] -> [(a, b)]`
- `zip ['a', 'b', 'c'] [1, 2, 3, 4]` - `[('a',1),('b',2),('c',3)]`

### String comprehensions
- Strings are represented as char lists, so they can be used like lists

## Recursive Functions

## Higher Order Functions
- Function which accepts functions as arguments and/or returns a function
- e.g. `map f xs = [f x | x <- xs]`
- `filter p xs = [x | x <- xs, p x]`
- General reduce / fold pattern: `f (x : xs) = x (+) f xs` where `(+)` is some operator
- folder pattern is defined with `foldr`
    - first argument: operator like `(+)` above
    - second argument: result for base case `[]`
    - e.g. `sum = foldr (+) 0`
- `(.)`-function: "of"
    - `f . g = \ x -> f (g x)`

## Data Types

### Polymorphism
- Slide 30: This is parametric polymorphism
- Haskell uses type classes to achieve ad-hoc polymorphism
- Similar to interfaces in Java
- class declarations specify which functions the type must have, and the type of the functions
- class types can be extended: `class Eq a => Ord a where ...` extends `Eq`
- Functor is similar to the Visitor-Pattern
- The compiler can automatically generate default implementations for polymorphism with `deriving`

## Interactive Programming
- We need a way to input data with a keyboard and show data on a screen (side effects)
- Side effects are integrated into the type system of Haskell
- Basic Type: `IO a`: The type of actions that return a value of type `a`
- Intuition: Function takes "the world" and returns it (possibly changed) along with a value
- `IO ()` is a type that returns no value
- `getChar` and `putChar` read and write characters from keyboard to screen
- `do` composes sequential actions together
    - `return` returns a value in a `do`
    - assignment with `x <- func`