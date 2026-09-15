---
title: Chapter 1 - Exam Cram
course: Introduction to Artificial Intelligence
lecture: Chapter 1
source: aima_ch1_intro_ai_detailed_slides(1).pdf
type: review
---
# Chapter 1 - Exam Cram
## Tier 1 - MUST KNOW ⭐⭐⭐
- Four views of AI and why AIMA favors rational agents.
- Expected-utility rule; belief vs preference.
- Perfect vs limited rationality.
- Fixed objective vs uncertain human objective.
- Eight disciplinary foundations.
- Computability vs tractability.
- Historical pattern of success, limits, and methodological renewal.
- Three early scale failures.
- Expert-system strengths/limitations.
- Perceptron/XOR, backpropagation, Bayesian networks, big data, deep learning.
- Benchmark capability vs robust beneficial behavior.

## Tier 2 - VERY IMPORTANT ⭐⭐
- Turing test and cognitive modeling.
- Planning from goals to means.
- Decision theory, MDPs, control feedback.
- DENDRAL and MYCIN.
- AI winter.
- Alignment, corrigibility, King Midas problem.

## Equation Cheat Sheet
$$a^*(e)=rg\max_{a\in A}\sum_sP(s\mid a,e)U(s,a)$$
$$c^*=rg\max_{c\in C}(\mathbb E[U\mid c,e]-Cost(c))$$
$$P(H\mid E)=rac{{P(E\mid H)P(H)}}{{P(E)}}$$
$$V^*(s)=\max_a[R(s,a)+\gamma\sum_{{s'}}T(s,a,s')V^*(s')]$$
$$\hat y=\mathbf 1[w^	op x+b\ge0],\quad w\leftarrow w+\eta(y-\hat y)x$$
$$	heta\leftarrow	heta-\eta
abla_	heta L$$
$$P(X_1,\ldots,X_n)=\prod_iP(X_i\mid Parents(X_i))$$

Full treatment: [[Ch01 Mathematics]].

## If You Only Remember 10 Things
1. AI is an integration problem.
2. AIMA centers rational agents.
3. Probability = belief; utility = preference.
4. Exact rationality can be infeasible.
5. Approximation may be rational.
6. Objectives can be misspecified.
7. AI draws from eight disciplines.
8. AI history repeatedly exposes scaling/representation limits.
9. Modern AI combines learning, probability, optimization, data, and computation.
10. Capability does not guarantee safety, robustness, or benefit.
