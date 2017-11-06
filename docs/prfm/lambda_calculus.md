# Lambda Calculus
- We will only look at pure untyped calculus
- LC builds directly on Sequent Calculus

## Conventions
- Application \(M M\) binds tighter than abstraction
- Application is left associative

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