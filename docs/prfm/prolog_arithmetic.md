# Prolog Arithmetic
- `+, -, /, *` are functors with arity 2
- statements like `3+2` are ordinary terms
    - `+(3,2)`
## is predicate
- like `==`
- both sides of the predicate get evaluated
- Works for integer and real numbers
- Right-hand site must be concrete, e.g. NOT `3+2 is X`

## List Arithmetic
```prolog
% len(list, size)

len([], 0). 
len([H|T], N) :- len(T, N1), N is N1+1.
```
## Tail Recursion
### acclen/3 
- `acclen(list, acc, size)`
- accumulator starts with 0 and counts up
```prolog
len(L,N) :- acclen(L,0,N).
acclen([], A, N) :- A = N.
acclen([H|T], A, N) :- A1 is A + 1, 
                       acclen(T, A1, N).
```

### max/2
- `max(list, maxElem)`
```prolog
max([E], E).
max([H|T], M) :- max(T, MT),
                 H > MT,
                 M = H.
max([H|T], M) :- max(T, MT), 
                 H <= MT,
                 M = MT.
```
