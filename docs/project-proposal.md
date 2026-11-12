# Project proposal

## 1. The problem and goal

(Explain the problem you want to solve and why it matters. Describe what you
want to improve, how you will measure improvement, and which limits or
requirements must be respected. A short example can help someone outside your
field understand the problem.)

**The problem and goal in my project:**
A small furniture factory makes three products: chairs, tables and sofas. Each
product needs several raw materials: wood, screws, paint, fabric and foam. Some
materials are shared: chairs and tables both need paint, and all three need wood
and screws. If one material runs out, every product that needs it stops, and the
factory loses sales. If the factory orders too much, the warehouse fills up and
money is stuck in materials it does not use yet.

My goal is to find an ordering rule for each material (when to order, how much,
and from which supplier) that keeps the total yearly cost as low as possible.
The total cost includes storage, ordering and lost sales. The limits are: the
warehouse has a fixed capacity shared by all materials, and at least 95% of
customer demand must be met.

## 2. The simulator

(Describe a program or model that could simulate your system and calculate what
happens under different conditions. Explain what inputs it takes and what
results it produces. State whether it can run on your computer and accept inputs
in a text file, such as JSON or YAML. If you have not chosen a simulator yet,
name an option you want to explore and explain what you need to check.)

**The simulator in my project:**

I will write a simulation in Python (possibly with the SimPy library) that plays
out one year in the factory, day by day, in a few seconds. Each day, customer
orders arrive, the factory uses materials to build products, stock goes down,
and new deliveries arrive. Demand changes during the year; for example, sofas
sell more in winter. Each material can be bought from a cheap supplier that is
slow or from a more expensive supplier that is fast.

Input: the ordering rule for each material, in a JSON file.
Output: a report for each material and product: how many days it ran out,
which products stopped because of it, average stock, warehouse use, and the
total cost.

The simulation uses a random seed, so the same rules always give the same
result. I still need to check that the simulation is correct, for example by
comparing a simple one-material case to the classic textbook formula (EOQ).
## 3. The agent's role

(Explain what the language-model-based agent will decide or change, and how it
will use the simulator's results to choose its next action. If known, list the
variables it may change and their allowed ranges. Explain what you expect the
language model to contribute: could a simple program that tries different
options and picks the best result achieve the same goal? Include one question
you still need to answer.)

**The agent in my project:**

The agent chooses the ordering rule for each material: when to order, how much,
from which supplier, and whether to order the same amount all year or more in
busy seasons. After each simulated year, it reads the detailed report and
decides what to change. For example, if chairs and tables stopped because paint
ran out, it changes the paint rule instead of changing everything. Each round
depends on what it learned in the previous round.

An optimizer without a language model (for example Optuna) can search the same
choices, because it sees only the total cost. I will compare the agent against
it and against random search. My open question is whether the agent, by reading
the detailed report, reaches good rules in fewer simulated years than the
optimizer, or whether the optimizer does just as well.

## Explain your project to someone outside your field

(Now describe your whole project again, as if you were explaining it to someone
from another field who has no background in your topic. For example, if you
study chemical engineering, imagine explaining it to a physicist; if you study
aeronautical engineering, imagine explaining it to someone in medicine; if you
study data science, imagine explaining it to a materials engineer. In one or two
short paragraphs, connect all three parts: the problem you want to solve, how
the simulator helps you test ideas, and what the agent will decide or change.
Use everyday language, explain any technical terms you need, and avoid
unexplained abbreviations. Do not simply copy your answers above.)

**My project in simple words:**

Imagine a small furniture workshop. To build chairs, tables and sofas it needs
wood, paint, fabric and other materials. If the paint runs out, both chairs and
tables stop; if it buys too much fabric, the storeroom is full. In my project, a
computer program plays out a whole year in the workshop in a few seconds. An AI
assistant acts like the workshop manager: it decides when and how much of each
material to buy, looks at what went wrong during the year, and improves its
decisions step by step.