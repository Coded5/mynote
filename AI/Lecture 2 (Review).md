---
id: Lecture 2 (Review)
aliases:
  - Lecture2
tags:
  - University
  - AI
---

#  Symbolic vs Sub-Symbolic
- Symbolic & Sub-Symbolic are 2 camps (or sub-fields) of AI

## Symbolic
- Based on representing knowledge explicitly with symbols and rules enabling reasoning and logical inference.
- Symbolic paradigm: use human-readable symbols to represent entities, concept and logical relationship.
- Approach: Have knowledge representation using formal logic and manipulation of symbols.


## Sub-Symbolic
- "*Operate at a level below that of symbolic representation*"
- Based on *implicit distributed representation* enabling the system to learn pattern without any pre-defined symbolic structures
- *Connectionist* approach (Inspired by the brain)
- A.K.A Connectionist models or Statistical Model.
- Statistical Learning: A paradigm that represent problem as a set of inter-connected nodes and finds weight that will lead to solution
- Also includes ML, DL
- Very good at pattern recognition and robust to noisy / incomplete data (Handle uncertainty)

## Neuro-Symbolic
- Combines both Symbolic and Sub-Symbolic, getting best of both world.
- AI require less data, more flexible and can do more complex task.
- Learning and reasoning = fast and slow congnitive process.

## Statistical vs Symbolic AI System

![Symbolic_Statistical.png](Symbolic_Statistical.png)

|Criteria|Statistical|Symbolic|
|-|-|-|
|Explainability|Hard|Easy|
|Generalizing algebraic operations|Hard|Easy|
|Robustness to noise|Easy|Hard|
|Robustness to ambuguity|Easy|Hard|
|Robustness to mislabeling|Easy|Hard|


### Explainability
- Refers to the ability of AI System to provide human-readable explaination and justification for its action.
- Enhance trush, transparency.
- Good for ethical AI practice.

## Current trends in Symbolic AI
- Applied to knowledge graph
- Contribute to multi-modal and cross-modal AI for richer data analysis:
    - briding semantic gps by connecting conceptual knowledge with data from images.

## Measure of intelligence

### Turing Test (Imitation Game) (1950)
- Alan turing argue that if machine can imitate human behavior that the interviewer can't reliablydetermine whether they're machine or human then it can think

### ARC
- Proposed ARC (Abstraction and Reasoning corpus) to measure intelligence instead.
- New definition based on Information Theory on skill-aquisition efficicency.

## Theoretical Foundation of Symbolic AI
1. Knowledge Representation
    - Symbols that explicitly represent knowledge.
2. Logical Reasoning
    - Use logic to reason about knowledge and draw inference.
- *This process can create new knowledge based on foundational understanding*: **Symbolic Learning**

# Logic
- Propositional Logic: A statement that can be true or false.
- Predicate Logic (A.K.A. First-order logic / First-Order Predicate Logic / Predicate Calculus) - logic with variables and quantifiers.

## Semantics
- The study of meaning in a language or system particulary how formulas and expressions are interpreted (Like grammar?).

> **Syntax vs Semantic (Gemini)**
> Syntax refers to the set of rules, principles, and processes that govern the structure of sentences or code. It defines which combinations of symbols are considered "valid."
> Semantics is the study of meaning. It’s the relationship between the symbols (syntax) and what they represent in the real world or in the computer's memory.

## Type of reasoning

1. Deductive Reasoning
- Deriving a conclusion based on premises that logically guarantee the conclusion.
- **Top-down** approach
- "*If this then that*"

2. Inductive Reasoning
- Generalize from observation to broader principle
- **Bottom-up** approach
- "*If sunrise today and yesterday, then it'll rise tomorrow*"

3. Abductive Reasoning
- Concluded most plausible explaination given the context and available information
- "*What is out there?*"
- **Not certain**

## Syllogism
- Subset of deductive reasoning
- Have exactly 2 premise and conlcusion
- Involve with All, Some, None

>Major Premise: All human are mortal>
>Minor Premise: Miri is human.
>Conclusion: Miri is mortal.

