---
title: Chapter 1 - Artificial Intelligence
aliases: [Artificial Intelligence Definitions Foundations History and Risks]
tags: [artificial-intelligence, rational-agents, ai-history]
course: Introduction to Artificial Intelligence
lecture: Chapter 1
source: aima_ch1_intro_ai_detailed_slides(1).pdf
type: lecture
---
# Artificial Intelligence: Definitions, Foundations, History, and Risks
_Source slides: 1-40_

## 🎯 Big Picture
This lecture introduces AI as both a scientific and engineering discipline. AI asks how physical systems can perceive, understand, predict, decide, learn, and act in complex worlds. The lecture explicitly rejects the idea that intelligence is one technique; intelligence is an **integration problem** linking representation, inference, learning, decision making, and action.

It then compares four definitions of AI: thinking humanly, acting humanly, thinking rationally, and acting rationally. AIMA emphasizes the [[Concepts/Rational Agents and Limited Rationality|rational-agent approach]] because it defines intelligence through effective action rather than human imitation. Rational action is formalized through expected utility, but the lecture stresses that exact optimization may be infeasible under finite time, memory, data, and model accuracy.

The lecture also challenges the standard model of a perfectly specified objective. Human preferences may be incomplete, context-sensitive, or inconsistent, motivating [[Concepts/Beneficial Machines and Value Alignment|beneficial machines]] that remain uncertain about human objectives and can learn, ask, defer, and preserve corrigibility.

Finally, AI is reconstructed as a multidisciplinary and historically evolving field. Philosophy, mathematics, economics, neuroscience, psychology, computer engineering, control theory, and linguistics contribute core ideas. AI history repeatedly alternates between ambitious claims, narrow successes, scale limits, methodological corrections, and new computational opportunities. The closing claim is that capability alone is insufficient; AI must also be robust, beneficial, safe, and governable.

## Lecture Roadmap
```text
Definitions → Four Views → Rational Agents → Expected Utility
       → Limited Rationality → Alignment
       → Foundations → History → Modern AI → Risks/Benefits
```

## What I Should Know After This Lecture
- Compare all four views of AI and explain why AIMA favors rational action.
- Explain the Turing test and cognitive modeling approaches.
- Read and apply the expected-utility action rule.
- Distinguish belief from preference.
- Explain limited rationality and the value of computation.
- Explain fixed-objective specification errors and alignment uncertainty.
- Name and connect the eight foundations of AI.
- Distinguish computability from tractability.
- Trace AI history from 1943 through deep learning.
- Explain symbolic search, expert systems, perceptrons, Bayesian networks, backpropagation, big data, and deep learning at the lecture's level.
- Explain why benchmark capability does not guarantee robust beneficial behavior.

## ⏱️ 60-Second Lecture Summary
AI can model humans or engineer rational behavior. AIMA centers rational agents that choose actions for the best expected result. Probability models uncertain belief, utility models preference, and decision rules connect the two. Real agents are computationally bounded, so approximation may be rational. Objectives may also be misspecified, so aligned systems may need uncertainty about human preferences. AI draws from eight disciplines and has progressed through repeated cycles of symbolic methods, scale failures, expert knowledge, statistical learning, data, and deep learning. Modern capability is substantial, but safety, transparency, robustness, and governance remain separate requirements.

## 1. Why Study AI?
Slides 2-3 ask: **How can a machine select actions that are effective, safe, and beneficial in novel situations?**

The slide 3 diagram is a feedback loop:
```text
Complex world → percepts/data/text/images → model/knowledge/beliefs
      ↑                                         ↓
      └──────────── feedback ← action/decision/control
```
AI is both explanatory (understanding intelligence) and constructive (building intelligent artifacts).

## 2. Four Views of AI
Slide 4 uses two axes: thought vs behavior and human-centered vs rationality-centered. See [[Concepts/Four Views of Artificial Intelligence]].

### Acting Humanly
Slide 5 uses the Turing test: can a machine's written behavior fool a human interrogator? A demanding system needs NLP, knowledge representation, automated reasoning, and machine learning. The total Turing test adds perception and physical action.

### Thinking Humanly
Slide 6 says a program becomes a cognitive model only when its mechanisms and timing match human data, not merely because it gets the answer right.

### Thinking Rationally
Slide 7 treats logic and valid inference as a foundation, but notes that real knowledge is uncertain and that belief alone does not choose actions.

### Acting Rationally
Slide 8 defines an agent as perceiving and acting. A rational agent seeks the best outcome or best expected outcome under uncertainty.

## 3. Expected Utility
Slide 9 separates belief $P(s\mid a,e)$ from preference $U(s,a)$. The action rule is a normative ideal, but exact computation may be impossible in large, uncertain, changing environments. See [[Ch01 Mathematics#Expected-Utility Action Rule]].

## 4. Limited Rationality
Slide 10 says perfect rationality assumes unlimited computation. Real agents have finite time, memory, data, and model accuracy. Approximation may be the only rational option. The figure shows solution value increasing, computational cost increasing, and net value eventually peaking. See [[Ch01 Mathematics#Metalevel Computation Rule]].

## 5. Beneficial Machines and Value Alignment
Slides 11 and 39 challenge fixed objectives. A helpful machine can remain uncertain about human preferences and learn, ask, defer, preserve options, and allow correction. See [[Concepts/Beneficial Machines and Value Alignment]].

## 6. Foundations of AI
Slide 12 places AI at the center of eight disciplines. See [[Concepts/Foundations of Artificial Intelligence]].

- Philosophy: logic, mind, empiricism, induction, action.
- Mathematics: logic, probability, computability, complexity.
- Economics: utility, games, decision theory, MDPs.
- Neuroscience: neurons, connectivity, brain-machine adaptation.
- Psychology: internal representations and mental models.
- Computer engineering: hardware/software, parallelism, accelerators.
- Control theory: feedback and optimization.
- Linguistics: syntax plus knowledge, context, goals, discourse.

## 7. History and Methodological Shifts
Slide 24 timeline:
```text
1943 McCulloch-Pitts → 1956 Dartmouth → 1960s microworlds
→ 1970s reality check → 1980s expert systems → 1986 backprop
→ 1988 Bayesian nets + RL → 2000s big data → 2012 deep learning → today
```
The lecture's explicit pattern is **broad claims → narrow successes → scale limitations → methodological corrections → new computational opportunities**. See [[Concepts/AI History and Methodological Shifts]].

## 8. Symbolic AI and Expert Systems
Slides 26-31 cover Logic Theorist, General Problem Solver, Lisp, Advice Taker, microworlds, combinatorial explosion, DENDRAL, MYCIN, and the expert-system boom/winter cycle. See [[Concepts/Symbolic AI and Expert Systems]].

## 9. Neural and Probabilistic AI
Slides 25, 27, and 32-36 cover threshold neurons, Hebbian learning, perceptrons, backpropagation, Bayesian networks, benchmarks, big data, and deep learning. See [[Concepts/Neural and Probabilistic AI]].

## 10. Capabilities, Benefits, and Risks
Slides 37-39 list capabilities across robotics, language, planning, games, vision, medicine, climate, and scientific discovery. The lecture warns:

> [!warning]
> Performance on benchmarks is not the same as robust, transparent, beneficial behavior in open-ended environments.

See [[Concepts/AI Capabilities Benefits and Risks]].

## Chapter 1 Takeaways
Slide 40 emphasizes seven conclusions: multiple definitions of AI; rational-agent organization; limitations of fixed objectives; multidisciplinary foundations; historical humility; modern integration of data/learning/probability/optimization/computation; and the need for beneficial, safe, governable intelligence.
