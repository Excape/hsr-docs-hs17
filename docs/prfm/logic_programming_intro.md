# Logic Programming Introduction
## Hello World
- Hypthoses are the "knowledge base"
    - Rules `m(X):- h(X).`<-> \(\forall x.H(x) \Rightarrow M(x)\)
        - "implied by" - it's reversed!
    - Facts: `h(s).`
- Query: `?- m(s).`
- \(\forall x\) is implied with uppercase variables
