---
title: Toward a Formal Model of Cognitive Synergy
date: 2024-12-06 10:07:57
tags: [cognitive synergy, agent]
mathjax: true
---

*Ben Goertzel. (2017). Toward a formal model of cognitive synergy. arXiv preprint arXiv:1703.04361.*

## What problems does this paper address?
- The formalization of cognitive synergy in the language of category theory, and its relationship with Artifical General Intelligence (AGI).
- The evaluation of the degree of cognitive synergy ebabled by existing or future concrete AGI designs.

## What's the motivation of this paper?
- Humanlike minds form only a small percentage of the space of all possible generally intelligent systems.
  --> **Research Question:** Do there exist general principles which any system must obey in order to achieve advanced general intelligence using feasible computational resources?
- The current mathematical theory of general intelligence focuses mainly on the properties of general intelligences that use massive, infeasible amounts of computational resources.
- Current practical AGI work focuses on specific classes of systems that are hoped to display powerful general intelligence.
- The level of the generality of the underlying design principles is rarely clarified.

## What are the main contributions of this paper?
- This paper revisits the concept of cognitive synergy and gives a more formal description of cognitive synergy in the language of category theory.
- This paper proposes a hierarchy of formal models of intelligent agents.
- This paper evaluates the degree of cognitive synergy enabled by existing or future concrete AGI designs.
- This paper formally describes the relationships between cognitive synergy and homomorphisms, and that between cognitive synergy and natural transformation.
- This paper introduces some core synergies of cognitive systems, such as consciousness, selves and others.

## What is cognitive synergy?
- Basic concept of cognitive synergy: General intelligence must contain different knowledge creation mechanisms corresponding to different sorts of memory, such as declarative, procedural, sensory / episodic, attentional, and intentional memory. These mechanisms must be interconnected in such a way as to aid each other in overcoming memory-type-specific combinatorial explosions.
- Conceptual definition: A dynamic in which multiple cognitive processes, which coorperate to control the same cognitive system, assist each other in overcoming bottlenecks encountered during their internal processing.
- Within Probabilistic Growth and Mining of Combinations (PGMC) agents, based on developing a formal notion of "stuckness", cognitive synergy is defined as a relationship between cognitive processes in which they can help each other out when they get stuck.

## Hierarchy of the formal models of intelligent agents:
{% asset_img figure_1.png 300 200 %}

*(Most generic at the top, most specific at the bottom.)*

## Basic Reinforcement Learning (RL) Agents
{% asset_img rl_basics.png 400 300 %}
- A class of active agents which observe and explore their environment, take actions that may change the state of the environment, and update their behaviors to maximize the expected cumulative rewards received from the environment in the long run.
- Markov Decision Process (MDP): a classical formalization of sequential decision making, where actions affect not only immediate rewards, but also subsequent states and future rewards.
- Markov property: The probability of each possible value for the state and reward depends only on the immediately preceding state and action.

1. Agent sends symbols from a finite *action space* $\mathcal{A}$ to the environment, i.e. taking an action.
2. The environment sends signals to the agent with symbols from a *state space* $\mathcal{S}$
3. Agent receives a reward from the *reward space* $\mathcal{R}$.

- The agent and environment are understood to take turns sending signals back and forth, yielding a history ("trajectory") of states, actions and rewards: s<sub>0</sub>, a<sub>0</sub>, r<sub>1</sub>, s<sub>1</sub>, a<sub>1</sub>, r<sub>2</sub>, ... , s<sub>i</sub>, a<sub>i</sub>, r<sub>i+1</sub>, ...

- The agent is represented by a policy function $\pi: \mathcal{S} \rightarrow \mathbb{R}^{|\mathcal{A}|}$ which maps a state $\mathcal{s}$ to probabilities of selecting each possible action $\mathcal{a} \in \mathcal{A}$.

- The dynamic of the environment can be characterized by a probability distribution $\mathcal{p(s', r\ |\ s, a)}$.

- **Goal-seeking agent:** an agent that receives a goal besides the perception of environment's states and rewards.

## Cognit Agents: agents with cognit-based memory
- Introduce a finite set $\mathcal{C}$ of atomic cognitive actions (aka. atomic cognitions, or "cognits"), denoted as *c<sub>i</sub>*.
- Add $\mathcal{C}$ to the trajectory such that it has the form s<sub>0</sub>, c<sub>0</sub>, a<sub>0</sub>, r<sub>1</sub>, s<sub>1</sub>, c<sub>1</sub>, a<sub>1</sub>, r<sub>2</sub>, ... , s<sub>i</sub>, c<sub>i</sub>, a<sub>i</sub>, r<sub>i+1</sub>, ...
- All these perceptions of states, actions, rewards, goals and cognits are stored in the memory of the agent.
- At each time step, the agent carries out internal cognitive actions on their memories and external actions in the environment.
- When a cognit is activated, it acts on all the other elements in the memory (despite many NULL results in most cases).
- The result of the action of cognition *c<sub>i</sub>* on the element *x* in the memory may be any of the following:
	- causing *x* to get removed from the memory (*"forget"*)
	- causing some new cognit *c<sub>j</sub>* to get created and persist in the memory (*"create"*)
	- if *x* is an action, causing *x* to get actually executed (*"execute"*)
	- if *x* is a cognit, causing *x* to get activated (*"activate"*)
- The process of a cognitive action *c<sub>i</sub>* on the memory may take time, during which other perceptions of states and actions may occur.
- This cognitive model may be conceived in algebraic terms: Consider $\mathcal{c_i} \ast x = c_j$ as a product in a certain algebra.
- **Question:** Should one allow multiple copies of the same cognit to exist in the memory?  
  (When a new cognit is created, what if it is already in the memory?)
	- If we increase the count of this cognit in the memory, then the memory will become a multiset, and the product $\ast$ of cognit interactions will become a hypercomplex algebra over the non-negative integers.
- This setting models the interaction between cognits, and in this way models the actual decision-making, action-choosing actions inside the formal agent.

## Hypergraph Agents
- **Definition:** Agents with labeled hypergraph-based memory.
- A hypergraph is a graph in which links may optionally connect more than two different nodes.
- Assumption: The memory of cognit agents has a more specific structure, i.e. a labeled hypergraph. The nodes and links in the hypergraph may optionally be labeled with strings, or structures of the form *(string, vector of numerical values)*.
	- String label indicates the type of the node / link.
	- Numerical values in the vector may have different semantics based on the type.
- Nodes and links in the hypergraph are collectively denoted as **"Atoms"**.
- The cognits become either Atoms, or sets of Atoms (i.e. subhypergraphs of the overall memory hypergraph).
- When a cognit is activated, one or more of the following happens:
	1. The cognit produces some new cognit. Optionally, this new cognit may be activated.
	2. The cognit activates one or more of the other cognits that it directly links to (or is directly linked to).
		- one important example: The cognit re-activates the cognit that activated it in the first place.
		  $\Rightarrow$ execution of "program graphs"
	3. The cognit is interpreted as a pattern, which is then matched against the entire hypergraph. The matched cognits returned from memory are then inserted into the memory.
	4. Other cognits are removed from the memory.
	5. Nothing happens.

## Rich Hypergraph Agents
- **Definition:** Agents with a memory hypergraph and a rich language of hypergraph's Atom types.
- Assumption: Atom can be assigned labels from {*"variable"*, *"lambda"*, *"implication"*, *"after"*, *"and"*, *"or"*, *"not"*}
- **h-pattern:** a hypergraph with some of its Atoms labeled with *"variable"*.
- To conveviently represent cognitive processes inside the hypergraph, extend the label space with labels *"create Atom"*, *"remove Atom"*.
- To take into account the state of the hypergraph at each time point, extend the label space with labels *"time"*, *"atTime"*.
- The resulting label space is:
  {*"variable"*, *"lambda"*, *"implication"*, *"after"*, *"and"*, *"or"*, *"not"*, *"create Atom"*, *"remove Atom"*, *"time"*, *"atTime"*}.


#### CPT graph
- The implications representing transitions between two states may be additionally linked to Atoms indicating the proximal cause of the transition.
- Assume there are two cognitive processes called *Reasoning* and *Blending*. Then these two processes each corresponds to a subgraph containing the links indicating the state transitions, and the nodes connected by these links.
- This subgraph is called Cognitive Process Transition Hypergraph (**CPT graph**).

## PGMC Agents
- **Definition:** Agents with a rich hypergraph memory, and homomorphism or history-mining based cognitive processes.
- Goal of this formalization: To model the internals of cognitive processes in a more fine-grained and yet still abtract way.

#### Cognitive Processes and Homomorphism
- Hypothesis: The cognitive processes for human-like cognition may be summarized as sets of *hypergraph rewrite rules*.
- A *hypergraph rewrite rule* has an *input h-pattern* and an *output h-pattern*, along with optional auxilliary functions that determine the numerical weights associated with the Atoms in the output h-pattern, which is based on the combination of the numerical weights in the input h-pattern.
- Rules of this nature may be (but are not required to be) **homomorphisms**.

- **Conjecture 1.** Most operations undertaken by cognitive processes take the form:
	- merging two nodes into a new node, which inherits its parents' links, or
	- splitting a node into two nodes, so that the children's links taken together compose the parent's links.

#### Operations on Cognitive Process Transition Hypergraphs
- One can place a natural **Heyting algebra structure** on the space of hypergraphs, using 
	- the *disjoint union for $\ \sqcup$* , 
	- the *categorical product for $\ \sqcap$* , and 
	- a special partial order called the *cost order*.

- This Heyting algebra structure allows one to assign probabilities to hypergraphs within a larger set of hypergraphs.

**What do these Heyting algebra operators mean in the context of CPT graphs?**
- Suppose two CPT graphs *A* and *B*, representing the state transitions corresponding to two different cognitive processes.
- *A $\sqcap$ B* is a graph representing transitions between conjuncted states of the system.
- *A $\sqcup$ B* is a graph representing the two state transition graphs.
- *A<sup>B</sup>* is a graph whose nodes are functions mapping states of *B* to states of *A*.
- Definition of cost order: *A* < *A<sub>1</sub>* , if (1) *A* and *A<sub>1</sub>* are homomorphic, and (2) the shortest path to creating *A<sub>1</sub>* from irreducible source graph, is to first create *A*.
- In the context of CPT graphs, this will hold if *A<sub>1</sub>* is a broader category of cognitive actions than *A* .
- For example, if *A* denotes all facial expression actions, and *A<sub>1</sub>* denotes all physical actions, then *A* < *A<sub>1</sub>* .

#### PGMC: Cognitive Control with Pattern and Probability
**What is Probabilistic Growth and Mining of Combinations (PGMC)?**
- Hypothesis: There exists a common control logic that spans multiple cognitive processes, i.e. adaptive control based on historically observed patterns.
- Consider the subgraph of a particular CPT graph in the system at a specific time point. The **Cognitive Control Process (CCP)** aims to figure out what a cognitive process **should do next** to extend the current CPT graph.
- What is the answer to this question?
	- There are various heuristics. This paper focuses on *pattern mining from the system's history*.
- Assumptions:
	- The system has certain goals, which manifest themselves as a vector of fuzzy distributions over the states of the system.
	- a label *"goal"*
	- At any given time, the system has n specific goals.
	- For each goal, each state may be assoicated with a number indicating the degree to which it fulfills that goal, i.e. goal-achievement score.
	- There is a fixed set of goals associated with the system.
- This way, the CCP aims to figure out how to use the corresponding cognitive process to transition the system to states that will possess the highest goal-achievement score.
- In this case, the CCP may look at h-patterns in the subset of system history stored in the system, do probabilistic calculations to estimate the odds that a given action on the cognitive process's part, and yield a state manifesting a given amount of progress on goal achievement.
- If a cognitive process selects actions in a stochastic way, one can use the h-patterns inferred from the remembered parts of the system's history to inform a probability distribution over potential actions.
- Selecting cognitive actions based on the distribution implied by these h-patterns can be viewed a novel form of **probabilistic programming**, driven by *fitness-based sampling* rather than Monte-Carlo sampling or optimization queries. This is called **Probabilistic Growth and Mining of Combinations (PGMC)**.

- Based on the inference from h-patterns mined from history, a CCP can then
	- create probabilistically weighted links from Atoms representing h-patterns in the system's current state, to Atoms representing h-patterns in potential future states
	- and optionally, create probabilistically weighted links from Atoms representing h-patterns in present- / potential future states, to goals.

## Theory of Stuckness
- Motivation: In a real-world cognitive system, each Cognitive Control Process (CCP) will have a limited amount of resources, which it can either use for its own activity, or transfer to another cognitive process.
- A CCP is stuck, if it does not see any high-confidence, high-probability transitions, associated with its own corresponding cognitive process, that have significantly higher goal-achievement scores.
- If a CCP is stuck, then it may not be worthwhile for the CCP to spend it limited resources on taking any action at that time. In some cases, it may be the best move to transfer some of its allocated resources to other cognitive processes (*"cognitive synergy"*).

#### A Formal Definition of Stuckness
- Let $G_{A}$ be the CPT graph corresponding to cognitive process $A$.
- $G_{A}$ is a subgraph of the overall transition graph of the cognitive process in the system.
- Given a particular situation $S$ ("possible world") involving the system's cognition, and a time interval $I$. Let $G_{A}^{S,I}$ denote the CPT graph of the cognitive process $A$ during time interval $I$.
- Let $P$ be an h-pattern in the system. Let $P(S, I)$ denotes the degree to which the system displays h-pattern $P$ in situation $S$ during time interval $I$. Let $g(S, I)$ denote the average degree of goal-achievement of the system in situation $S$ during $I$.
- If we identify a set $\mathcal{I}$ of time intervals of interest, we can then calculate the degree to which the h-pattern $P$ implies goal-achievement in general:
  {% asset_img equation_1.png 300 200 %}
  <!-- $g(P) = \frac{\sum_{(S,I), I\in\mathcal{I}} g(S,I) P(S,I)}{\sum_{(S,I), I\in\mathcal{I}} P(S,I)}$ -->

- Suppose the system is currently in situation $S$, during time interval $I_{S}$. Then $\mathcal{I}$ might be defined as a set of time intervals in the near future after $I_{S}$. Then we can calculate the degree to which $P$ implies goal-achievement in situations that may occur in the near future after being in situation $S$:
  {% asset_img equation_2.png 600 500 %}

- The confidence of this degree of goal-achievement is:
  {% asset_img equation_3.png 500 400 %}
  - where $\ f$ is a monotone increasing function with range [0, 1].
  - This confidence measures the amount of evidence on which the estimate $g_{S',I_{S}}(P)$ is based.

- Finally, we may define $e_{C,I_{R},S,I_{S}} (P, I, I_{P})$ as the probability estimate that the CCP corresponding to cognitive process *C* holds for the following proposition:
  *In situation S during time interval $I_{P}$, if allocated a resource amount in interval $I_{R}$ for making the choice, C will make a choice leading to a situation in which $P(S, I) \in I_{P}$ during the interval $I$ after $I_{S}$*. A confidence score $c_{C,I_{R},S,I_{S}}(P, I, I_{P})$ may be defined similarly to $c_{S,I_{S},\mathcal{I}}(P)$.

- Given a set $\mathcal{I}$ of time intervals, one can define $e_{C,I_{R},S,\mathcal{I}}(P, I, I_{P})$ and $c_{C,I_{R},S,\mathcal{I}}(P, I, I_{P})$ via averaging over the intervals in $\mathcal{I}$.

- The confidence of $C$ knowing how to move forward toward the system's goals in situation $S$ at time $t$ is then:
  {% asset_img equation_4.png 700 600 %}

- The **stuckness** of a CCP is defined as the **complementary value of the confidence** of a cognitive process knowing how to move forward towards the system's goal in a particular situation at a specific time:
  {% asset_img equation_5.png 300 200 %}

## Cognitive Synergy
- Premise of the existence of cognitive synergy between two cognitive processes $A$ and $B$:
  For many situations $S$ and times $t$, exactly one of $A$ and $B$ is stuck.

- In the metasystem, the set of $(S, t)$ pairs where exactly one of $A$ and $B$ is stuck to a degree of stuckness $\in I_{d} = (L, U)$ has a certain probability $stuck_{A,B,I_{d}}$.

- The set $G_{A,B,I_{d}}^{stuck}$ of CPT graphs $G_{A}^{S,t}$ and $G_{B}^{S,t}$ corresponding to the $(S, t)$ pairs in $stuck_{A,B,I_{d}}$ has a certain probability $Prob(G_{A,B,I_{d}}^{stuck})$.

- An overall **index of cognitive synergy** between cognitive processes $A$ and $B$ is defined as:
  {% asset_img equation_6.png 400 300 %}
  where $\mathcal{P}$ is a partition of [0, 1].

#### Extension of this definition to more than two cognitive processes:
- Given N cognitive processes, consider triplewise synergies between them.
- Let $A$, $B$, $C$ be three cognitive processes. Then, $stuck_{A,B,C,I_{d}}$ is defined as the set of $(S, I)$ where all but one of $A$, $B$, $C$ is stuck to a degree in $I_{d}$.
- The triplewise synergy corresponds to cases where the system get stuck if it had only two of the three cognitive processes.

#### Cognitive Synergy and Homomorphisms

#### Cognitive Synergy and Natural Transformations
<!-- {% asset_img figure_2.png 600 500 %}
{% asset_img figure_3.png 600 500 %} -->
<div style="display: flex; justify-content: space-around; align-items: center;">
  <img src="figure_2.png" alt="Figure 2" style="width: 45%; height: auto;">
  <img src="figure_3.png" alt="Figure 3" style="width: 45%; height: auto;">
</div>

{% asset_img figure_4.png 250 150 %}

<div style="display: flex; justify-content: space-around; align-items: center;">
  <img src="figure_5.png" alt="Figure 5" style="width: 50%; height: auto;">
  <img src="figure_6.png" alt="Figure 6" style="width: 50%; height: auto;">
</div>





## Some Core Synergies of Cognitive Systems

## Cognitive Synergy in the PrimeAGI Design
- Key learning and reasoning algorithms:
	- **PLN:** a forward and backward chaining based probabilistic logic engine, based on the Probabilistic Logic Networks formalism
	- **MOSES:** an evolutionary program learning framework, incorporating rule-based program normalization, prob- abilistic modeling and other advanced features
	- **ECAN:** nonlinear-dynamics-based ”economic attention allocation”, based on spreading of ShortTermImpor- tance and LongTermImportance values and Hebbian learning
	- **Pattern Mining:** information-theory based greedy hypergraph pattern mining
	- **Clustering** and **Concept Blending:** heuristics for forming new ConceptNodes from existing ones

- Curry-Howard correspondence

- Some places where the potential for cognitive syerngy exists:
	- **Pattern mining**
	- **PLN inference**
	- **MOSES**
