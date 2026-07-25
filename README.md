# Representation-of-a-Real-World-Problem-as-a-Markov-Decision-Process


# Aim

To represent a Shopping Mall Service Robot problem as a Markov Decision Process (MDP) by defining its states, actions, transition probabilities, reward function, and implementing the model using Python dictionaries.

# Problem Statement
## Problem Description

A shopping mall uses an autonomous service robot to guide customers to their desired locations. The robot starts at the mall entrance and moves through different areas such as the food court, clothing store, and escalator to reach the customer's current location.

The robot must choose the correct direction at every step. If it reaches the customer, it receives a high reward. If it moves in the wrong direction, it receives a penalty. The objective of the robot is to learn the shortest and safest path to the customer.

## MDP Components

The Markov Decision Process is represented as

MDP=(S,A,P,R,γ)
Symbol	Meaning
S	Set of States
A	Set of Actions
P	Transition Probability
R	Reward Function
γ	Discount Factor

## State Space

The robot can be in one of the following locations:

S = {
    Entrance,
    Food Court,
    Clothing Store,
    Escalator,
    Customer Location
}

## Sample State
Current State = Food Court

The robot is currently standing at the food court.

## Action Space

The robot can perform the following actions:

A = {
    Move Left,
    Move Right,
    Move Forward,
    Stop
}

## Sample Action
Action = Move Forward

The robot moves from the Food Court toward the Clothing Store.

## Transition Probability

The transition probability determines the likelihood of reaching the next state after performing an action.

P(s
′
∣s,a)

Example:

From Entrance → Move Forward → Food Court (Probability = 1.0)
From Food Court → Move Right → Clothing Store (Probability = 1.0)
From Clothing Store → Move Forward → Customer Location (Probability = 1.0)

Since the environment is deterministic, every valid action always leads to the expected next state.

## Reward Function

The reward function is

R(s,a,s
′
)

Reward values:

Situation	Reward
Reach Customer	+100
Move in Correct Direction	+10
Wrong Direction	-5
Stay Without Progress	-2

The robot learns to maximize the total reward while minimizing unnecessary movements.

## Graphical Representation
                 +10
Entrance ----------------> Food Court
                              |
                              | +10
                              V
                      Clothing Store
                              |
                              | +10
                              V
                        Escalator
                              |
                              | +100
                              V
                    Customer Location (Goal)

Wrong Direction = -5
Stay Idle = -2


---

## Python Representation

Write your code here.

Use Python dictionaries to represent the MDP.


```python# MDP Representation using Python

print("Name: Vigensh M")
print("Register Number: 212223240176")

states = [
    "Entrance",
    "Food Court",
    "Clothing Store",
    "Escalator",
    "Customer Location"
]

actions = [
    "Move Left",
    "Move Right",
    "Move Forward",
    "Stop"
]

transitions = {
    "Entrance": {
        "Move Forward": "Food Court"
    },
    "Food Court": {
        "Move Right": "Clothing Store"
    },
    "Clothing Store": {
        "Move Forward": "Escalator"
    },
    "Escalator": {
        "Move Forward": "Customer Location"
    },
    "Customer Location": {
        "Stop": "Customer Location"
    }
}

rewards = {
    ("Entrance", "Move Forward"): 10,
    ("Food Court", "Move Right"): 10,
    ("Clothing Store", "Move Forward"): 10,
    ("Escalator", "Move Forward"): 100,
    ("Wrong Direction"): -5,
    ("Stop"): -2
}

discount_factor = 0.9

print("\nStates:")
print(states)

print("\nActions:")
print(actions)

print("\nTransitions:")
for state, action in transitions.items():
    print(state, "->", action)

print("\nRewards:")
for reward in rewards.items():
    print(reward)

print("\nDiscount Factor:", discount_factor)

```
---
## Output
<img width="1047" height="557" alt="image" src="https://github.com/user-attachments/assets/2a85b703-23c9-467c-b1b7-a5affd896eef" />



---

## Result

Thus, the Shopping Mall Robot problem was successfully represented as a Markov Decision Process (MDP) using states, actions, transitions, rewards, and Python.



---

