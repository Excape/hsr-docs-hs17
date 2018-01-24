# Lambda Calculus
- We will only look at pure untyped calculus
- LC builds directly on Sequent Calculus

## Conventions
- Application \(M M\) binds tighter than abstraction
    - A match with (\(\lambda x. M\)) is attempted before a match with \(M M\).
- Application is left associative
    - When trying to match \(M1 M2\), the largest possible subterm is matched with \(M1\).

Although it may sound counter intuitive, the tighter an operator is to be bound, the later its corresponding syntax rule is to be applied during parsing.

## Free and Bound variables
- \(\lambda y.\) can be thought of as a quantifier
- Bound variables are like parameters
    - e.g. in an integral \(\int{yx^2}{dx}\), x is bound

## Beta Redcution
- Replace every \(x\) in the abstraction \(M\) with \(N\) 

$$\frac{}{H\vdash (\lambda x. M) N = [x := N]M}\beta$$

- Examples:
    - \((\lambda x. square x) 5 = square 5\)
    - \((\lambda x. square x) (\lambda y. square y) 5 = (square (\lambda y. square y)) 5\)
        - No further resolution!

- Even if there are different strategies of how to resolute something, the result is always the same
