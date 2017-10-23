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
- For the query, try unifying it with an expression from the knowledge base. Repeat for every found unification.
- When proof is found, backtrack upwards to find the instantiation
- Search Tree example: Try unify, then check every possible instantiaton (here `a` and `b`)
- Recursive with backtracking, i.e. it goes down of the left side first ("depth-first"), then backtrack upwards
- Every branch is a proof. The proof search tree searches for all possible proofs. Not to confuse with the proof tree from PC, where only 1 proof was needed!
