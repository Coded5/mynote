---
id: Lecture 6
aliases:
  - Lecture 6
tags:
  - AI
  - University
---

# Lecture 6

## Pseudocode for a Goal-Based agent

```Pseudocode
function GoalBaseAgent(percept) returns action


plan = Plan(state, goal, model)
action = first (plan)
first <- rest (plan)
return 

```

> **Midterm**
> Pseudocode of an agent -> modify it

## Solving Problem by Searching
- Goal-based agent is a problem-solving agent 
- Problem solving agent use atomic representations:
    - each state of the world is treated as *single indivisible whole* with no internal structure.
- Goal-based agents use richer representations and explicit construct detailed sequences of actions to achieve their goal are called *planning agent*
- Starts with *symbolic definitions* of states, actions, goal and solution(s).
- Maximize its performance measure.
- Searching by simplifiy the current goal (?).

### Goal Formulation
- Suppose Goal-Based agent: Agent
- Agent goal is to move from the point S (Starting) to point G (Goal)
- Any action that doesn't reach the goal will be discard.
- Goals: limiting what is it trying to achieve -> what action to consider?
- Goal formulation: First Step

### Problem Formulation
- Once goal is defined, then the problem must be formulated before searching.
- (Well-defined) Problem consists of:
    - Initial State
    - Set of action
    - Transition model: How action change the state?
    - Goal Test: Are we there yet?
    - Path cost function: Is this a good solution?
- The problem environment is represented as *state space / search space*
- Solution is the path through *state space / search space* that leads to Goal (Starting from S)

> **Summary**
> State Space: All possible states an agent or system can be in.
> Search Space: State that can be reach (Subset of State Space)
> Operators/Action: Rules that transform one state to another
> Solution: A goal state that satisfies the problem and the sequence of actions that reach the goal state.
> *Search is the process of systematically exploring the state space to find a solution*

### Key Search Terms
- *Visiting a node*: The agent / algorithm reaches a node and considering it.
- *Expanding a node*: Applying operators to the node's state to generate successor states.
- *Generating nodes:* Creating new nodes by applying operators to existing states.
> The fuck is the difference?
- *Exploing the state space*: Visiting + Expanding + Generating and evaluate whether they may lead to solution

## Search Methods

> **Midterm**
> Shouldn't require too much remembering

> **Observable**: The agent always knows it current state
> **Discrete:** Each satate has a finite set of possible action.
> **Known:** Know the result of each action
> **Deterministic:** Each action leads to *exactly* 1 outcome state.

- Environment must be *observable, discrete, known and deterministic*
- Search methods can be modeled as trees, graphs of state and actions.

### Search Algorihm
- Common Search Algorithm: *BFS, DFS, Uniform-Cost search (like Dijkstra), Best-First Search (like A\*), Hill Climbing, Beam Search, Branch & Bound*
- Each have strength, assumptions and trade-offs.
- Choose wisely.
- Search Algorithm are typically evaluate using four criteria:
    - **Completeness**: Is the solution guaranteed?
    - **Optimality**: The is solution have the least cost?
    - **Time Complexity**: How long it takes?
    - **Space Complexity**: How much memory it takes? (Maximum nubmer of states to store)

- Time & Space Comlexity depend on
    -```b```: branching factor (average number of successor per node)
    -```d```: depth of the shallowest solution

> **Generated vs Expanded Nodes**
> Generated:
> Expanded: When the algorithm removes it from the fringe and consider it and generate successor node

### Classification of Decision Problems (Not in midterm)
- P vs NP 

> **Complete vs Incomplete**
> Complete search algorithm are guaranteed to find a solution if it exists given enough time and memory.
> - Doesn't require the state space to be finite
> - Require some condition like *finite branching, positive step costs*
> Complete and Optimal serach algorithm means they guaranteed to find the best solution
> - Requires addition condition: *Admissable Heuristics*
> Probably will be time or memory intensive.
> Incomplete search algorithm are not guaranteed to find a solution even if solution exists
>   - Explore only part of the serach space
>   - More efficient at the cost of Completeness and Optimality
>   - Useful when the search space very large / infinite

### Heuristics
- Problems-solving strategy that use intuition and not neccessary logical
- Make thing faster but doesn't guaranteed solution
- Can rely on to certain extent.
- *Admissable*: Never overestimate the true cost from node n to goal ```h(n) <= TrueCost as n -> G```
    - This property guaranteed optimal solution.
    - "*Optimistic but never wrong in the wrong direction*"

### Uniformed vs Informed Search
- Uniformed: Search algorithm that doesn't use any additional knowledge about the problem beyond states, actions and goal test.
- Informed (AKA. Heuristics search): Have additional knowledge to guide the search more efficiently.
    - Knowledge provided by: Heuristic function (Estimate how close a state is to the goal) like remaining cost and distance.
    - Focus on more promising path

|Uniformed|Informed|
|-|-|
|BFS| A*|
|DFS|Greedy Best-First search|
|UCS|  |
|IDS|  |
|Bidirectional Search|  |


### Breadth-first search
- Explore search space *level-by-level* expanding the shallowest nodes first
- Use FIFO to expand the next level
- Explore all node at one depth before moving to the next

![Breadth](BFS.png)

> *Midterm*
> Add heuristic to Pseudocode

### Depth-first search
- Explore search space by expanding one branch as deeply as possible before backtrack.
- Use stack for fringe
- Prolog backward chaining is an example of DFS
    - Prolog backtrack to the most recent choice
- Store few node in memory at one time (Space efficient)

![DFS](DFS.png)

## Planning
- Try make it in prolog Try make it in prolog
- Planning is task of finding the sequence of actions that transform S to G state.
- Can be view as search problem

<!-- ?? -->
- Representing actions and effects:
    - Actions are described by pre-condition (when action can be done) and effect (how it change the state).
    - Accurate action representations allow a planner to predict outcomes and reason about which actions to apply.
- Common apporaches: *STRIPS, GraphPlan and SATPlan*

- Requirements:
    - Domain description.
    - Initial State.
    - Goal description.
- So, **Plan** is a valid sequence of actions that achieve the G from S.

### Type of Planning
1. Classical Planning
    -Assume environment to be observable, discrete, known, deterministic, finite and static.

2. Non-Classical Planning
    - Environment maybe stochastic, dynamic
    
> *Stochastic environment* contain randomness
> The same state can lead to different possible state with probability
> Ex. Self-driving cars operate in stochastic environment

### STRIPS (Standford Research Institute Problem Solver)
- Is Classical
- Represent the world state as:
    - Set of logical fact
    - Action with defined pre-condition and effects
    - Planning is done by logical reasoning
- Components
    - World description: describe objects, action
    - Problem set
    - Planning domain definition language (PDDL)
- Use means-end analysis

## AI Architectures (NOT IN EXAM :fireworks:)
- Structured approaches to problem-solving, decision making and behavior modeling
- Design the transition of the state / paradigm
- AI paradigms: Symbolic reasoning, Reactive systems, learning-based models, distributed system.

> *Midterm*
> Uncertainty

## EXAM

- Symbolic vs Sub-symbolic
- Fundamental Theory
- Why planning and searching relate so closely?
- Turing test (Measure of intelligence?) -> Why its not that good
- Prolog Basic (MUST)
    - Unification vs Pattern-Matching
    - Question plz :sob:
    - LAB LAB LAB
    - Reasoning capabilities
    - Write a prolog predicate that does this or that. (SHOULD BE BRIEF) (MIGHT USE RECURSION)
    -Creative Question story: read (my natural enemy :skull:)
- Kind of reasoning
- Basic Searching algorithm like DFS, BFS, A*, Dijkstrak
- Uncertainty
    - Bayesian formula
- Exercise in textbook 

