# Exercise 4
- `Learn Prolog Now!` chapter 1: <http://www.learnprolognow.org/lpnpage.php?pagetype=html&pageid=lpn-htmlse3>

## 1.4
```c
killer(butch).
married(mia, marsella).
dead(zed).
kill(marsellus, X) :- footMassage(X, mia)
love(mia, X) :- dancer(X)
eat(julex, X) :- tasty(X); nutritious(X)
```

## 1.5
```
wizard(ron).
hasWand(harry).
quidditchPlayer(harry).
wizard(X):-  hasBroom(X),  hasWand(X).
hasBroom(X):-  quidditchPlayer(X). 
```

- `wizard(ron).` -> `true`*
- `witch(ron).` -> `false`
- `wizard(hermione).` -> `false`
- `witch(hermione).` -> `false`
- `wizard(harry).` -> `true`
- `wizard(Y).` -> `Y = ron; Y = harry`
- `witch(Y).` -> `false`

- `*` `wizard(ron)` gibt `true ; false` zurück, weil es zwei Regeln für `wizard` gibt, und die Regel für `ẁizard(X)` `false` zurück gibt

## 2.
