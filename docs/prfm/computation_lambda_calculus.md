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
