# Prolog Recursion
- Loops use a global state, declarative programming languages don't have that
    - Therefore, recursion is the only way to do such computation
- Non-terminating programs give an "out of stack" error
- Prolog processes the knowledge base from top to bottom and left to right
    - This determines the order of the output
- Recursion call must always be placed torwards the end of a rule, otherwise it will iterate over the incursion infinitely!
