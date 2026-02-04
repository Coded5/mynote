---
id: Lecture5
aliases:
  - Lecture5
tags:
  - University
  - AI
---

# Expert Systems

_Like if-then statement with conditions and actions_

- Computer Program that simulate decision of **human expert** (Ex. Medicine)

  ### Components:
  - Knowledge base: store knowledge in form of facts, rules and relationships
  - Inference Engine: Applies rule & facts to derive new fact and draw conclusions / recommendation.

- Rule-based approach is good for narrow area of expertise
- Example: [Drools](https://www.drools.org), CLIPS, Jess

**Rule Engines** executes rules of the expert system

## Inference in expert systems

### Two Types of inference

- Forward Chaining (Data Driven): Starts from known facts and apply rules to get new facts
- Backward Chaining (Goal-driven, Reverse-Engineer): Starts from goal and work backward with rules which determine which facts need to be true to support the goal.
  _Prolog commonly use backward chaining_

## Backward Chaining Expert Systems

- Backward chaining is a Symbolic AI system that use goal-driven reasonng
- Begin with goal and work backward
- Avoid unnecessary exploration improving reasoning efficiency

_Explosion of the search space can cause some agent to loop indefinitely_

## Mycin

- _Mycin_ (1970s) is classic expert system that use backward chaining to diagnose bacterial infection and recommended treatments
- Designed to reason under uncertainty, Have medical knowledge base.
- **Did not learn autonomously**
- Knowledge-base was built through _Knowledge Engineering_ by human experts, adding facts, rules and relationships
  - Can be updated (by human) this is **Knowledge Acquisition not ML**.

# Agents

**Terminologies**

- **Rational**: Property of an agent that selects action to maximize expected utility given its precepts and knowledge.
- **Autonomy**: The extent of which agent's behavior is determined by its own experience rather than only by its initial programming.
- **Reflex Agent**: Agent that chooses action based only on the current percepts without memory or consideration of the future. (React only)
- **Model-base agent**: Agent that maintains internal model of the world and updated over time.
- **Utility-base agent**: Agent that evaluate possible outcome.
- **Learning agent**: Agent that improves its performance over time from experience.
- **Knowledge-based Agent**: Agent that use explicit knowledgebase (FRR) and logical reason to infer new information.
- **Goal-based agent**: Agent that represent explicit goal and selects actions.
- **Planning Agent**: A goal-based agent construct a plan (Sequence of actions) to reach its goal by reasoning about future state of the world.
- **Distributed Agent**: Cooperation of many agents (Hive-mind?).

> **Note**
> The environment is observable if agent always knows the complete state of the world. Otherwise its only partially observable and if an action wlays leads to the same result(s),
> then the environment is deterministic

- **Agent** is something that acts or a program that implements a mapping from perceptions to actions.
- **AI Agent** is autonomous entity that perceives its environment through _sensory_ input and select action base on the environment

## Symbolic AI Agents

- Symbolic AI Agent consists of (Computational Model):
  - perception (sensing the environment)
  - reasoning (drawing conclusion and select option)
  - action (affecting the environment)
  - goals (state that agent seek to achieve)

### Knowledge-based agents

- Maintain explicit representation of the world and use reasoning to decide action.
- **Core Capabilities**
  - State & Action Represention: State of the world and available action.
  - Incorporate new percepts: Receive and update its knowledge accordingly.
  - Update world model: Revise its internal representation as new information arrives.
  - Infer Fact
  - Action Selection

# Search

- **Very fundamental**
- Explore possible state and find sequence of actions that lead to the goal state
- Need to formulate search problem must define:
  - Start state
  - Goal state (Might be multiple)
  - Set of operators (a.k.a actions) that change state
  - Path: sequence of operators (actions) that change state.
  - _Path cost function_ measures cost of a sequence of actions
- State space (s.k.a search space): set of all state with transitions between state that caused by actions
  - _Can be viewed as graph whose nodes are states and edges represent state transitions_
- Solution Space: set of all possible solutions that satisfy the problem.

> State space is set of all possible state, the search space is the portion explored by an algorithm,
> and the problem space includes states together with actions and goals.

- Agent often operate with incomplete knowledge and multiple possible action
- If actions are uncertain it can explore those sequence of action
- Search find path (solution) that is the most efficient (minimize cost)

- Search space problemn refer to **Explosive Growth** of the search space making the search of the solution extremely inefficient.

> Search & Planning are closely related:
> Search explores the solution space to find paths while planning is the process of _searching_ for actions that achieve the goal

# GPS (General Problem Solver)

- Developed in mid 1950s, was an attempt to build a general-purpose problem-solving program.
- Apply problem-solving method to solve different kind of problem. **Not solve all problems**

- Represent problems as state space where state is a _configuration_ of the problem (tf does configuration mean?)
- **Means-Ends Analysis** try to reduce the difference/distance between the current state and goal state an.
- Action / Operators are chosen based on pre-defined rules:
  - Transforming objects
  - Reducing discrepencies
  - Apply problem solving actions

> Primary Example: Tic Tac Toe & 8 Puzzle (Might be in midterm)

![8Puzzle.png](8Puzzle.png)

### Approach

```python
# Heuristic
while True:
    doAction()
    if goalReach() or goalUnreachable():
        return solution
```

- _Logic Theorist_ (for proving mathematical theorem) GPS aimed to solve general problem across many domain.
  - _Use heuristic search_

> **Heuristic (Midterm!)**
> Strategies or Rules of Thumb that simplify decision-making by relying on _intuition_ or _informed estimation_
> rather than strict formal logic.

> A search algorithm is **optimal** if (the solution exists) always
> find the solution with the _lowest cost_

- Heuristic trade guaranteed correctness & optimality for speed and simplicity and human-like problem solving

### General Search Concept

- Problem is modeled as set of states represented as nodes in graph or tree.
- "Just like data structure you have to represent them in a certain way to achieve peak efficiency"
- A node is expanded when applying operators / actions which create **successor nodes** corresponding new state.
- Search graph / tree is structure constructed when searching a sub-graph of the full state space. (Explored state so far)
- Use data structure call **Fringe** (or frontier, open-list) which might be stack, queue, priority queue.

> Graph consist of node and links
> Tree is graph with no cycle which can be rooted (have root node) or unrooted (no designated root node) and each node in a tree has exactly one parent.
> **leaves** is node with not node wit

![tree_graph.png](tree_graph.png)

- **Tree search algorithm** expand nodes from a root(starting state) into a tree of possible paths.
- **Graph search algorithm** keeps track of visited node avoiding redundant exploration and infinite loops in cycle state spaces.

> **Fringe / Frontier / Open-list**
> (???)
> A Data structure containing all nodes that have been generated but not yet expanded(?)
> states that have been discovered but whose successor have not yet been explored.

### Explore Example

![graph.png](graph.png)

| No. | Current | Fringe               |
| --- | ------- | -------------------- |
| 1   | -       | S(0)                 |
| 2   | S(0)    | **A(1), B(1), C(1)** |
| 3   | A(1)    | B(1), C(1), **E(2)** |
| 4   | E(2)    | B(1), C(1), **D(3)** |
| 5   | D(3)    | B(1), C(1), **G(2)** |
| 6   | G(4)    | B(1), C(1)           |

### Real world search problems

- Game Playing: Chess engine, Tic Tac Toe, 8 Puzzle
- Scheduling, Logistic, Resource Allocation
- Robotics Navigation
- Robot Assembly
  - States: Real-valued coordinates of joints.
  - Actions: Continuous motion of joints.
  - Goal: Complete assembly.
  - Path cost: Time to execute.
- 8-Puzzle
  - State: Integers locations
  - Actions: move left, right, up, down
  - Goal test: Given goal state.
  - Path cost: #steps

### Terms & Variables

- `g`: Cost of the path
- `h`: Heuristic cost
- `f`: `f = g + h` total estimate cost

# Homework (Lecture)

- Implements tic-tac-toe

# Summary

- **Forward-chaining**: work your way to from start derive fact until goal is reach
- **Backward-chaining**: start from the goal and work your way to the start and see what has to be true.
- **Expert system** is a computer program that make decision like human expert
  - Consist of: Knowledge-base, Inference Engine
  - Can either be forward-chaining or backward-chaining
  - Due to the rule-based approach it has narrow area of expertise
  - The knowledge base is updated & maintained by human expert
  - _Example_: **Mycin** use knowledge-base and inference to diagnose bacterial infection + provide treatment plan
- **Agent**: Something that can sense and act
- **Search**: A way to find a sequence of actions that lead to the goal state
  - Need: Start state, Goal state, Operators (actions), Cost function
  - **Search Space**: Set of all state and transition state
  - **State Space**: Set of state that is explored
  - **Problem Space**: Set of all possible state both explored and unexplored.
  - **Solution Space**: Set of all possible solution of the problem.
- **GPS (General Problem Solver)**
  - Try to solve different kind of problem (_Not all problem_)
  - Use Means-Ends Analysis (Heuristic): Minimize discrepencies between start and goal state.
  - Represent the state using graph: Node is state, Edge is transitional state
  - Use data structure called **Fringes** to search the space.
