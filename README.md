# A graph-based engine for reproducing object behavior from trajectory data
Overview
This project demonstrates an experimental simulation engine that learns to reproduce object behavior directly from observed trajectories.

Instead of relying on a hand-written physics engine or an end-to-end neural network predictor, the system represents world dynamics as a graph of states and transitions:

states represent recurring local motion regimes of an object
transitions represent changes between those regimes
transition conditions depend on the relative context of surrounding objects
After a short seed sequence, the system performs a generative rollout and predicts future object behavior step by step.

# Core Idea
The main idea is to model behavior not as one global continuous formula, but as a set of local motion regimes and transition rules between them.

In this formulation:

an object is described not only by its position
it also has a current learned motion state
the next state is selected according to the current scene context
This makes the system closer to a structured learned world model than to a standard next-step predictor.

# What the Current Demonstration Shows
The current demonstration focuses on a 3D scene with two balls.

The system learns from recorded motion data and then reproduces:

future ball motion
plausible rebounds
state changes driven by the relative spatial context of the scene
Importantly, after initialization, the simulation does not replay pre-recorded future frames. Instead, it generates future behavior by moving through the learned graph.

# Videos
The repository includes 3 simulation video examples.

These correspond to models trained on different amounts of data:

69 million frames
119 million frames
169 million frames
Each example shows a rollout produced after training on the corresponding amount of observed motion data.

# Why This Is Interesting
This approach may be useful in problems where:

behavior is difficult to script manually
exact dynamic equations are unavailable or inconvenient
interaction with other objects matters
long-horizon rollout quality is more important than one-step prediction accuracy
Potential strengths of the approach:

interpretability
explicit state-transition structure
the ability to test hypotheses about which factors actually influence behavior
the ability to extend transition conditions with new parameters without changing the core architecture

# Repository Contents
This repository is a demonstration repository.

It contains:

simulation videos
a project description
a high-level explanation of the method

The public version of this repository does not contain:

source code
the training pipeline
internal data processing tools
implementation details of the engine
# Status
This project is currently a research and engineering prototype.

At this stage, the goal is to demonstrate the viability of the approach:

learning object behavior from trajectories
representing dynamics through a graph of states and transitions
generating future behavior through rollout
