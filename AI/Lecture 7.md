---
id: Lecture 7
aliases:
  - Constraint Satisfaction
  - Lecture 7
tags:
  - AI. University
---

# Constraint Satisfaction

> **The Dilema**
> Sometime solution need to be in a certain way like: *some criteria, satisfying constraint, meeting requirement*
> Like *sudoku, class registration*

- **Constraint Satisfaction Problem (CSP)**: Represent a problem defined by set of variables with certain domain.
    - Backtracking (DFS): is one way to solve CSPs
- Have 3 components:
    - X: finite set of variables
    - D: Non-empty set of domain for each variable
    - C: finite set of constraints that specify allowable combination of values
- Type of constraints:
    - Simple var
    - ?

You should be able to tell how many atom, precidate, rules are there in prolog code

## Examples

We have:
```
Ex. 1
X1 (Variable) = {1, 2, 3, 4} (Domain)
X1 != 3
Solution: X1 = {1, 2, 4}

Ex. 2
A = { 1, 2, 3 }
B = { 1, 2, 3 }
C = { 1, 2, 3 }

Constraints: A > B, B != C, A != C
Solution(s): A = 3, B = 2, C = 1 or A = 3, B = 1, C = 2

Backtrack:
A = 1 -> B = 1 (X)
A = 1 -> B = 2 (X)
A = 1 -> B = 3 (X)
A = 2 -> B = 1 (Y)
A = 2 -> B = 1 -> C = 1 (X)
A = 2 -> B = 1 -> C = 2 (X)
A = 2 -> B = 1 -> C = 3 (Y) [Solution Founded]

Ex. 3 (Map Coloring Problem)
Variables: Each region on the map is a variable 
Domain: Each variable has a domain of { red, green, blue }
Constraints: No two region can have the same color

```



> **Midterm**
> With story: imagine ur AI Engineer...

# Dealing with Uncertainty

- A pain in the ass that happen frequently in the real world
    - Real world knowledge is incomplete noisy and exception-filled.

- Two-valued logic (true / false) is only suitable for absolute facts in everyday reasoning -> this could lead to incorrect conclusion.
    - "*All bird can fly, Penguin is bird -> Penguin can fly*" (?!)

- Using fuzzy logic is better: "*Nearly all bird can fly*"
- Symbolic AI Agent must handle uncertainty of:
    - Partial Observability
    - Non-deterministicsm
- **Fuzziness**: Representing and reasoning with vague/imprecise information
    - Not strictly true or false but have partial truth value in a spectrum/continuum (Degree of truth)
    - Have gradual boundary

- A way to deal with this is using statistical model (like neural network)
- The most promsing is: *Probabilistic Reasoning* works with *Conditional Probability*

> A rule *A -> B* is assigned with certainty factor like $P (B | A) = \beta$

## Bayesian Networks
- From intuitive clarity with clean semantic of conditional probability (*tf does this mean*)

## Types of uncertainty
- *Epistemic uncertainty* AKA Model uncertainty (Incomplete Knowledge) - Reducible (Uncertainty can be lower if more information are available)
- *Aleatory uncertainty* (Stemming from randomness) - Irreducible, need probabilistic model.
    - Often seen in ML, it can't be eliminate

## Uncertainty in Planning
- Let action Leave(t) denote leaving for the airport t minutes before the flight.
- For a given t will Leave(t) be on time?
- Problems:
    - partial observability (traffic, other cars)
    - noisy inaccurate sensors (traffic reports)
    - uncertainty of some action (flat tire, accident)
    
## Dealing with uncertainty
### Implicit method
- Ignore the uncertainty as much as possible.
- "*Assume nothing went wrong*"

### Explicit method
-   Building a model of the world and incorporate uncertainty about the system's state & dynamics
- Reason about the effect of action given the model

- Using purely logical approach has 2 problems:
     - Might risk falsehood
     "*Leave(30) will get me there*"
     - May lead to conclusion that are too weak.
     "*Leave(30) will be on time if there is no accident and nothing went wrong*"
     "*Leave(10,000,000) probably work but not helpful*"

- Making assumptions, unless contradict by evidence
- Use rules with Fudge Factor
    - Sprinkler -> 0.99 Wet Gress, Wet Gress -> 0.7 Rain
    - Could lead to misleading conclusion like "Sprinkler cause rain"

- Fuzzy Logic highly used in control theory & control engineering
- Fuzzy Logic deals with degrees of truth while Probability deal with likelihood of event

## Probability Theory
- Has clear semantics and support principled reasoning for:
    - Combining evidence.
    - incorporating new evidence.
- Probabilistic knowledge (ex. 99% of birds can fly) allow more accurate and realistic inferences and also be learned from data.

- **Probabilistic Learning**
    - ML are called Probabilistic / Statistical models because they deal with uncertainty and estimate it.

- Belief and Bayesian probability, subjective probability express likelihood of the proposition based on current knowledge
- Ex. $P(Leave(t) on time | no reported accident) = 0.7$

- Which action to choose?
    - Utility Theory is used to represent and infer preferences
    - Decision Theory = Probability Theory + Utility Theory
- The revision of prior knowledge is carried out using *Bayes' Rule*
    - The new probability assigned to the event after the revision is called *posterior probability*

> **Midterm**
> BAYESIAN RULE
