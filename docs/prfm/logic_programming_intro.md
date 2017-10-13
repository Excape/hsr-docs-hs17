# Logic Programming Introduction
Online Version of Learn Prolog Now: <http://www.learnprolognow.org/>

## Hello World
- Hypthoses are the "knowledge base"
    - Rules `m(X):- h(X).`<-> \(\forall x.H(x) \Rightarrow M(x)\)
        - "implied by" - it's reversed!
    - Facts: `h(s).`
- Query: `?- m(s).`
- \(\forall x\) is implied with uppercase variables

## Knowledge Base
- Hypotheses, called "Knowledge Base"
- Every statement is a "clause" and ends with a `.`
```c
woman(mia).
woman(jody).
woman(yolanda).
playsAirGuitar(jody).
party.
```
- If a query cannot be proven true, it is `false`
- Unknown predicates return either `false` or throw an error (depending on the compiler)

### Rules
```c
happy(yolanda). // fact
listens2music(mia). // fact
listens2music(yolanda):- happy(yolanda). // rule
playsAirGuitar(mia):- listens2music(mia).
playsAirGuitar(yolanda):- listens2music(yolanda).
```
- Read: `happy(yolanda) => listens2music(yolanda)` (Reversed)

### Conjuction
```c
playsAirGuitar(vincent):-
    listens2music(vincent),
    happy(vincent).
```
- Read: "vincent plays air guitar if he listens to music **and** he's happy"

### Disjuction
- `;` instead of `,`
- Same as defining to rules with the same goal

- There's no negation in Prolog. An absence of rule is basically a negation
    - Prolog does no proofs of contradiction, but "negation as failure" (to construct a proof tree)

## Asking for alternatives
- `?- woman(X)` gives every `X` that satisfies \(\exists x.woman(x)\)
- (Uppercase) variables in the Knowledge Base take into account every occurence (\(\forall\) universially quantified)

## Syntax
- Atoms are strings *starting with a lowercase letter* or arbitrary strings in `''`
- Numbers are integers or floats (no type-checking)
- Variables are Strings starting with an *Uppercase Letter* or with a `_`
    - Variables are always "bound" in a \(\exists\) or \(\forall\)
    - The variable `_` is a "wildcard"
- Complex Terms are e.g. `playsAirGuitar(mia)`
    - The functor must be an atom
- "Arity" is the number of arguments in a complex term
    - Two predicates with different arity are treated as sepparate
