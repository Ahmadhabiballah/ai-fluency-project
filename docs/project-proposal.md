# Project proposal

## 1. The problem and goal

(Explain the problem you want to solve and why it matters. Describe what you
want to improve, how you will measure improvement, and which limits or
requirements must be respected. A short example can help someone outside your
field understand the problem.)

**The problem and goal in my project:**
A store sells many products, and customers buy different amounts every day.
For each product, the store must decide when to order more and how much to
order. Ordering too much fills the warehouse and costs money; ordering too
little means products run out and customers leave. All products share the same
warehouse space. My goal is to find ordering rules for all products that keep
the total cost low while most customers still find what they want.

## 2. The simulator

(Describe a program or model that could simulate your system and calculate what
happens under different conditions. Explain what inputs it takes and what
results it produces. State whether it can run on your computer and accept inputs
in a text file, such as JSON or YAML. If you have not chosen a simulator yet,
name an option you want to explore and explain what you need to check.)

**The simulator in my project:**

I want to write a simulation in Python (possibly with the SimPy library) that
simulates one year in the store, day by day. The input is the ordering rule for
each product (when to order and how much), for example in a JSON file. The
output is the total cost, how many customers did not find a product, and how
full the warehouse was. I will use a fixed random seed so the same input always
gives the same result. I still need to check how to make the demand realistic
enough.
## 3. The agent's role

(Explain what the language-model-based agent will decide or change, and how it
will use the simulator's results to choose its next action. If known, list the
variables it may change and their allowed ranges. Explain what you expect the
language model to contribute: could a simple program that tries different
options and picks the best result achieve the same goal? Include one question
you still need to answer.)

**The agent in my project:**

The agent decides the ordering rules for each product. After each simulated
year, it reads the results, for example which products ran out and why, and
changes the rules. Because the products share space and money, changing one
product affects the others, so there are too many combinations to try all of
them. A simple program that tries many rules could also work, so an open
question is whether the agent can find a better solution, or the same solution
faster.

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

Imagine you run a small shop. If you buy too much stock, your storeroom is full
and your money is stuck in boxes. If you buy too little, customers come and
leave empty-handed. In my project, a computer program plays out a whole year in
the shop in a few seconds. An AI assistant acts like a shop manager: it decides
when and how much to order, looks at what happened during the year, and keeps
improving its decisions.
