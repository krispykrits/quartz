---
course: Machine Learning
chapter: 2
source: chapter02_concept_learning.pdf
type: lecture-note
---
# Chapter 2 - Concept Map

Target concept $c:X\to\{0,1\}$  
↓  
Training examples $\langle x,c(x)\rangle$  
↓  
Hypothesis space $H$  
↓  
[[Concepts/General-to-Specific Ordering|General-to-Specific Ordering]]  
↙　　　　　　　　　　　　　　↘  
[[Algorithms/FIND-S|FIND-S]]　　　　　 [[Concepts/Consistency and Version Spaces|Version Space]]  
↓　　　　　　　　　　　　　　　↓  
one maximally specific h　　 [[Concepts/S and G Boundaries|S / G Boundaries]]  
　　　　　　　　　　　　　　　↓  
　　　　　　　　 [[Algorithms/Candidate Elimination|Candidate Elimination]]  
　　　　　　　　　　　　　　　↓  
　　　　　　　 Remaining uncertainty  
　　　　　　　　　　　　　　　↓  
　　　　 [[Concepts/Active Learning and Query Selection|Active Queries]]  

Generalization beyond observed data  
↓  
[[Concepts/Inductive Bias|Inductive Bias]]

## Main Relationship
Representation defines what can be expressed. The ordering defines how the learner can search. Training examples eliminate or force movement among hypotheses. Version spaces represent uncertainty. Inductive bias provides the assumptions needed to predict unseen instances.
