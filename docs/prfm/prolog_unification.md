# Prolog Unification and Proof Search
## Unification
- Unification instantiates variables such that two terms are equal
- `woman(Z)` and `woman(X)` unifies, because `X` can be instantiated with `mia`
- `loves(mia, X)` and `loves(X, vincent)` cannnot be unified, `X` needs to be instantiated with one value
- In Prolog, unification can be done with `=`
- Prolog ignores the "occurs check" (recursive)
    - `father(X) = X` does not unify with the theoretical definition (would be `father(father(father(...)...))`)
- Prolog will give the most general solution, e.g. when there are infinite solutions with 1 free variable, it will state a variable for that

## Proof Search
