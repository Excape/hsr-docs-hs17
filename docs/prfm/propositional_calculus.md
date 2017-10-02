# Propositional Calculus
## Basic PC
- Contains the basic set of PC (like NAND in computing)
- A *Predicate* is a formal statement that is either *true* or *false*
- \(\vdash\): "Turnstile" or "tee"
- \(H \vdash G\): "Prove \(G\) under Hyphotheses \(H\)"
- Turnstiles are "implications" on the level of a sequent, whereas "\(\Rightarrow\)" is an implication on the predicate level

## BasicPC Syntax
- Examples of possible strings: \(\bot\), \(\lnot\bot\), \(\bot \land \bot\)

## Proof Rule Schemas
- Schemas represent an infinite number of proof rules of the same form
- They use *meta variables*. If these are instantiated, they become a concrete proof rule

## Proof Rules of basicPC
!!! todo
    Put \(\land\ goal\) as outer fraction

Example: Prove \(P \land Q \vdash Q \land P\)

$$\frac{\frac{\frac{}{P, Q \vdash Q}hyp \frac{}{P, Q \vdash P} hyp}{P, Q \vdash Q \land P} \land goal}{P\land Q \vdash Q \land P} \land hyp$$

- Every "string" you can generate using the basicPC Syntax can be used to instantiate a meta variable
- \(H\) can be an empty set

## Extending the syntax
- We extend basicPC by introducing "syntactic sugar", new Symbols like \(T\) for True and \(\lor\)
- These syntactical equivalences can be used like proof rules
    - All the new rules of PC can be proven with the basicPC proof schemas
