# Summary

## Prolog
- Variables start with an uppercase letter
- Atoms are in `''` quotes or start with a lowercase letter
- `Arity` is the number of arguments of a complex term
    - Predicates with different arity are different ("overloading")
- Two terms unify if either:
    - they are identical 
    - or can be instantiated uniformly such that the resulting terms are equal
- Arithmetic: `2 + 3 = 5` -> `2+3 is 5`
    - Syntactic sugar for `is(+(2,3),5)`

### Recursion
- List recursion: `[H|T]`
- Prefer tail recursion (e.g. with accumulators), the search tree will be smaller
- in a recursive clause, base case should always come before the recursive "call", or it won't terminate!

### Proof search
<img style="height: 250px" src="../img/prolog_search_tree.png" />

### Collecting Solutions
- Find all solutions from a goal for a specific object (here `X` and collect them in List `L`)
    - Always succeeds, empty List if no solutions found
    - `findall (X, descend(martha,X), L).`

## Lambda Calculus
- Application binds tighter than abstraction
    - \(\lambda x. M_1 M_2 \Leftrightarrow \lambda x. (M_1 M_2)\)
- Application is left-associative
- A \(\lambda\) term is in normal form if no further reductions can be applied to it
    - Every \(lambda\) term has *at most* one normal form (this makes computation deterministic)
- \(\delta\)-reduction: substitution of a defined symbol with its definition

### Strategies
- **Innermost-first**: the innermost *reducible expression* (redex) first, i.e. there's no other redex inside it
    - if ambiguous, the left-most first
    -  with this strategy, function arguments are reduced exactly once
    -  corresponds to **call by value**
- **outermost-first** (normal form): the outermost redex first, i.e. there's no redex outside it
    - if ambiguous, the left-most first
    - Always ends in a normal form
    - with this strategy, function arguments are reduced as many times as they're needed -> unneeded arguments won't be reduced
    - corresponds to **call by name**

## Haskell

### Types
- `Int` has a fixed precision (64 bit), while `Integer` has an arbitrary precision
- Function application is left-associative, while the type definition `t1 -> t2` is *right-associative*
- `type` declares a type as an alias of other types
    - No recursion allowed
    - may have parameters
    - example: `type Assoc k v = [(k,v)]`
- `data` declares a new type
    - Recursive definitions possible
    - with type parameters: `data Shape = Circle Float | Rect Float Float`
    - if type has a single constructor, `newtype` can be use for efficiency: `newtype Nat = N int`
    - example: `data Tree a = Leaf a | Node (Tree a) a (Tree a)`

### Classes
- like an interface, defines what methods a type must have
- can have default definitions

``` haskell
class Eq a where
    (==), (/=) :: a -> a -> Bool
    x /= y = not (x == y) -- default definition
```

- classes can be extended: `class Eq a => Ord a where ...`
- Defining instances:

``` haskell
instance Eq Bool where
    False == False = True
    True == True = True
    _ == _ = False
```

- instances can be defined directly inside the type definition `data` with `deriving`

``` haskell
data Bool = False | True -- order matters here, such that False < True
    deriving (Eq, Ord, Show, Read)
```

### Functions
- Guarded Equations (read `|` as "such that"):

``` haskell
abs n | n >= 0    = n
      | otherwise = -n
```

- cons `:` is right-associative: `1:2:3:[] == [1,2,3]`

### Foldr / Foldl
- `foldr`
``` haskell
foldr :: (a -> b -> b) -> b -> [a] -> b
foldr f v [] = v
foldr f v (x :xs) = f x (foldr f v xs)
```

- `foldl`
``` haskell
foldl :: (a -> b -> a) -> a -> [b] -> a
foldl f v [] = v
foldl f v (x :xs) = fold f (f v x) xs
```

- as non-recursive patterns:

$$ foldr \, (\#) \, v \, [x_0,x_1,\ldots,x_n] = x_0 \; \# \; (x_1\, \# \, (\ldots \, (x_n \, \# \, v) \, \ldots )) $$
$$ foldl \, (\#) \, v \, [x_0,x_1,\ldots,x_n] = (\ldots ((v \, \# \, x_0) \, \# \, x_1) \; \ldots) \, \# \, x_n $$

### Function composition
- `f . g`: Read "f of g of ..."
- `f . g = \x -> f (g x)`

### Interactive Programming
- `IO` is an built-in type
- Modeled as `type IO a = "world" -> (a, "world")`, i.e. with side effects, "impure"
- Sequencing

``` haskell
act :: IO (Char,Char)
act = do x <- getChar
         getChar -- result discarded
         y <- getChar
         return (x,y)
```

### Functors

- Functors abstract the idea of `map` to a general `fmap`
- e.g. with `Maybe`: `fmap g (Just x) = Just (g x)`
- Applies a function to the inner elements of a data struture

### Applicatives
- Extends `Functor`
- Extends the concept of `fmap` to an arbitrary amount of function arguments (whereas `fmap` just takes 1 function)

``` haskell
class Functor f => Applicative f where
    pure :: a -> f a
    (<*>) :: f (a -> b) -> f a -> f b
```

- Applicative form: `pure g <*> x1 <*> ... <*> xn`
- `g` takes `n` arguments
- e.g. `pure (+1) <*> [1,2] = [2,3]` = `fmap (+1) [1,2]`

### Monads
- Allows the `do` notation
- Extends `Applicative` with a "bind"-operator `>>=`
    - `(>>=) :: m a -> (a -> m b) -> m b`
- `return = pure`

``` haskell
eval (Val n) = Just n -- applicative `pure` of Maybe is `just`
eval (Div x y) = eval x >>= \n -> -- n is the result of eval x
                 eval y >>= \m ->
                 safediv n m

-- equivalent to --
eval (Div x y) = do n <- eval x
                    m <- eval y
                    savediv n m
```

<!-- ## Notes Q&A Session
- Exercise 2.4 Proof rules, 2nd rule: difficult because of cut rule
    - In exam: Try everything first, some things looks hard but are easy - and vice versa
- Exercise 3.1 FoPC
    - `A => b = c`: `b = c` is bound tighter than `=>` because `b = c` is a predicate
- Exam in general easier than exercises
- PC doesn't have left- or right associative
    - \(A \land B \land C \land D\) is ambiguous, i.e. not well formed
- Monads: look at the type of the functions first
- summary sheet: one example of every concept allowed
- exam format
    - rules of the summary sheet included
    - haskell library functions included (except list syntax like `(x:xs)`)
    - all questions are independent
    - haskell will account for the most points (each topic in proportion to the amount of material covered) -->