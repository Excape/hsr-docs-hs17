# Prolog under the hood
- Prolog is a subset of *FoPCe*
- A horn clause is a disjunction of literals where at most one literal is positive

## Proof by resolution
- Union Sets in clauses and goals where a predicate is positive in one and negative in the other
    - e.g. \({\lnotA, \lnotB, C} \union {\lnotC}\)
- Repeat until set of goal clauses is empty