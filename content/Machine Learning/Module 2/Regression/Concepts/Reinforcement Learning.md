---
title: "Reinforcement Learning"
tags: [machine-learning, chapter-01]
type: concept
---


# Reinforcement Learning

_Source slides: 43–45_

## Policy

An RL agent learns:

$$
a=\pi(x),
$$

mapping a state to an action.

## Lecture Examples

- Space Invaders: game image → move/fire.
- Humanoid walking: joint angles → motor torques.

## Feedback Difference

Supervised learning supplies desired outputs. RL supplies evaluative reward, often delayed.

## Credit Assignment

The learner must determine which earlier actions caused later reward.

## Sample Efficiency

The lecture notes that demonstrations and unlabeled interaction data can help mitigate sparse reward.

## Mathematics

See [[Ch01 Mathematics#Reinforcement-learning policy]].
