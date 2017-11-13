# Computation with the Lambda Calculus
## Normal Form
- A \(\lambda\) Term is in \(\beta\)-normal form, iff no further reductions can be applied to it
- It's possible to have a different ordering of the resolution, but they all lead to the normal form
- Every \(\lambda\)-term has at most one normal form
    - That makes computation deterministic
- Not all \(\lambda\)-terms terminate i.e. have a normal form
    - e.g. \((\lambda x.\,x\,x)(\lambda x.\,x\,x)\)
    - Necessary to make it Turing-complete

## Currying
- \(\lambda\)-terms only allow single argument functions
- How to implement functions with multiple Arguments?
- Currying: \(f(x, y) = f\,x\,y\)
    - Apply \(f\) to \(x\), which returns a function that takes \(y\)
    - Apply this function to \(y\)

## \(\delta\)-Reduction
- Substitute a defined symbol with its definition
- e.g. \(square(x)\) substituted is \(\lambda x.\,*\,x\,x\)

## Higher Order Functions
- Functions that either takes a function as input or returns a function
- functions are "first-class citizens"

## Evaluation Strategies
- A redex (reducible expression) is a any Delta- oder Beta-reducible lambda term
- Strategie plays a role in the length of derivations and if they terminate
- There are an arbitrary number of evaluation strategies
- Innermost- and Outermost-First are "extreme" cases

### Innermost-first (applicative order)
- The innermost redex is reduced first
- If multiple possible, the leftmost is reduced first
- A redex is innermost if there is no other redex inside it

### Outermost-first (normal order)
- The outermost redex is reduced first
- If multiple possible, the leftmost is reduced first
- A redex is outermost if there is no other redex outside it

### Comparison
- innermost-first: Arguments are reduced exactly once (even if they're not used)
- outermost-first: Arguments are reduced as often as they're needed (can be multiple times for one)
- innermost-first doesn't always result in shorter derivations
- Outermost-first always ends in a normal form if it exists
    - innermost-first may not terminate, e.g. when a non-terminating redux is an argument, but never used
- innermost-first is like "call by value", outermost-first like "call by ref"

### Lazy Evaluation
- Make call-by-name more efficient
- Cache evaluations to evaluate arguments only once
- Default for Haskell

## Encoding Data and Operations
- Pure lambda does not have primitive data types
- We need numbers, booleans & pairs to construct arbitrary data types
- These definitions correspond to AND/OR-Gates on a real CPU (low-level)

### Booleans
- It's hard to have an intuition for these, try to prove some properties that must hold (truth tables)

### Arithmetic
- For every number n, apply a function n times