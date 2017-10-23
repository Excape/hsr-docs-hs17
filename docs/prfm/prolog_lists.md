# Prolog Lists
- List elements can have arbitrary "types" (mixed)

## Recursive Definition
- Either
    - an empty list: `[]`
    - a non-empty list:
        - a head = first element
        - tail: every other element (another list)
- `[H|T]` to split head and tail for pattern matching
- Use wildcards `_` as "anonymous variables"

## Member Predicate
- `member/2`: Determine whether something is an element of a list
```prolog
member(X,[X|T]).
member(X,[H|T]) :- member(X,T)
```

## a2b Predicate
- first argument is list of `a`s, second argument is list ob `b`s with same length of first list

```prolog
a2b([], []). % base case
a2b([a|La], [b|Lb]) :- a2b(La, Lb)
```
## append/3
- `append(L1, l2, L3)`
- `L3` is `L1 + L2`

```prolog
append([], L, L).
append(L, [], L).
append([H|T], L2, L4) :- append(T, L2, L3),
                         L4 = [H|L3].
```

### sublist
- `sublist(Lsub, L)`
- Sublists are the prefixes of suffixes
```prolog
sublist(Sub,List) :-
    suffix(Suffix, List),
    prefix(Sub, Suffix)
```
