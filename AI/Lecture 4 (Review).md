---
id: Lecture 4 (Review)
aliases:
  - Lecture4
tags:
  - University
  - AI
---

# Knowledge Representation
- How to model and store knowledge in a way to computer can understand and reason with it.
- A method of knowledge representation must be: *declarative, expressive, context, independent and unambiguious* which must define:
    - Syntax: Rule for how expression are structured
    - Semantic: Rule for how to interpret expression (No misinterpret)

- **Inference Engine**: Use knowledge to infer new knowledge.
- **Knowledge Acquisition/Parsing**: Extract knowledge from text, input
- **Knowledge Representation**: A way to store knowledge that we can reason with.

- **Objects**: Instance.
- **Categories**: Simplify knowledge through inheritance.

## Automated Reasoning

- Deriving to a new knowledge / conclusion from the existing knowledge.

# Knowledge Representation Method

## Symbolic Representation
- Use human-readable symbols to encode knowledge
- Knowledge represented as Formal Logic or First-Order predicate logic

> **Symbolic Natural Langauge**
> Natural Language can't be use as a way to represent knowledge because it require context(Context Dependent) and could be interpret in many ways (Ambiguious)

### Challenges
- Common sense: How do we encode everyday knowledge? like social norms, cause-effect relations?
- Uncertainty: Can't really model probabilistic model or ambiguious model. How to reason with noise?
- Communicating: ??

## Embodied Representation
- Use sensory information and interact with physical environment.
- AI agent would be autonomous, perceiving the environment and do action.
- Robotics (*Hardware Agents*)
    - Sensors: Perceive the environment
    - Actuator: Do action
- "*Intelligence emerge from bodily action and interaction with the world*"

![Embodied Representation.png](Embodied%20Representation.png)

## Rule-based Representation
- If-then rules

## Frames
- Organize information into hierarchical and structured ways
- *Think of it as struct in Rust or C*

## Semantic Network
- Node represent concept
- Edge represent relationship
- Very broad
- Frames is also subset of Semantic Network.
- *Capture how concept are related to one another in a meaningful way*

![Semantic Network.png](Semantic%20Network.png)

## Ontologies
- Structure knowledge by having:
    - Classes: concepts or cateogries
    - Properties: Attribute
    - Relationship
    - Instance: Individual entities
- Explicitly formal 

### Why?
- Everything is explicitly defined -> Can do automated reasoning and inference
- Support deduction and subsumption. (*Other do as well????*)
- Little to no ambiguity

## Description Logic
- Family of logic-based knowledge representation formalism
- Model and reason about conceptual structure of a domain in a precise way (*tf does this mean*)
- Domain have 3 components:
    - Concepts: class
    - Roles: relationship, predicates
    - Individual: Object, instances
- Evolved from Semnatic Network (make it more formal)
- Is decidable: Reasoning procedures are guaranteed to terminate (*Does this mean turing incomplete?*)
- Modern system usually build on DL using Ontologies and knowlege graphs to have shared-vocab

> **Example**
> *Concepts:* Person, Animal
> *Role*: hasChild (Relates a parent to a child)
> *Individual*: John, Mary
> *Assertions*: hasChild(John, Mary) -> John is a parent of Mary.


## Knowledge Graphs
- Nodes represent entities, concept
- Edges represent relationship
- Implement using graph database, semantic web technology.
- Ex. Search engine
- Can represent 3 kinds of knowledge:
    - Factual: Specific facts about the world (Bangkok is a city)
    - Conceptual: Relationship between concept (Dog is a mammal)
    - Procedural: Info about actions (How to make a pipebomb)

## World Assumption
1. **Closed world assumption**: If not explicitly state then it is false.
2. **Open world assumption**: If it not explicitly stated doesn't imply falsehood.

