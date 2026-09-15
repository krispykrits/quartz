---
course: Introduction to Artificial Intelligence
lecture: Chapter 2
source: Intelligent-Agents-Lecture.pdf
title: Chapter 2 - Comparisons and Distinctions
type: review
---

# Chapter 2 — Comparisons and Distinctions

  -----------------------------------------------------------------------
  Concept A               Concept B               Main Difference
  ----------------------- ----------------------- -----------------------
  Percept                 Percept sequence        Instantaneous sensor
                                                  content vs. complete
                                                  percept history

  Agent function          Agent program           Abstract mapping
                                                  vs. concrete
                                                  implementation

  Rationality             Omniscience             Best expected decision
                                                  with available
                                                  information
                                                  vs. knowledge of actual
                                                  outcomes

  Performance measure     Utility function        External criterion of
                                                  success vs. agent's
                                                  internalized
                                                  desirability function

  Fully observable        Partially observable    Complete
                                                  action-relevant state
                                                  available vs. relevant
                                                  state hidden/noisy

  Deterministic           Nondeterministic        One determined
                                                  successor vs. multiple
                                                  possible successors

  Stochastic              Nondeterministic        Probabilities
                                                  quantified
                                                  vs. possibilities
                                                  unquantified

  Episodic                Sequential              Episodes independent
                                                  vs. current actions
                                                  affect future decisions

  Static                  Dynamic                 World stable during
                                                  deliberation vs. can
                                                  change during
                                                  deliberation

  Dynamic                 Semidynamic             World changes vs. world
                                                  fixed but performance
                                                  changes with time

  Discrete                Continuous              Distinct values/steps
                                                  vs. smoothly varying
                                                  ranges

  Known                   Observable              Knowledge of action
                                                  outcomes vs. access to
                                                  current state

  Simple reflex           Model-based reflex      Current percept only
                                                  vs. internal state
                                                  informed by
                                                  history/models

  Goal-based              Utility-based           Goal satisfaction
                                                  vs. graded
                                                  preference/trade-offs
                                                  under uncertainty

  Atomic                  Factored                Opaque state identity
                                                  vs. vector of
                                                  attributes

  Factored                Structured              Fixed attributes
                                                  vs. explicit objects
                                                  and relationships

  Localist                Distributed             One concept/location
                                                  vs. representation
                                                  spread across many
                                                  locations
  -----------------------------------------------------------------------

> [!warning] **Known ≠ fully observable.** The lecture explicitly
> treats these as independent dimensions.

> [!warning] **Rational ≠ successful in hindsight.** A rational action
> can have a bad outcome.

> [!important] **Performance measure ≠ utility function.** The
> performance measure is external; utility is an internalization that
> can support rational action when aligned with that measure.

## Agent Architecture Ladder

  ----------------------------------------------------------------------------------------
  Architecture         Current     Internal         Model                Goal      Utility
                       percept        state                                   
  --------------- ------------ ------------ ------------- ------------------- ------------
  Simple reflex              ✓          ---           ---                 ---          ---

  Model-based                ✓            ✓             ✓                 ---          ---
  reflex                                                                      

  Goal-based                 ✓            ✓             ✓                   ✓          ---

  Utility-based              ✓        often        may be              may be            ✓
                                              model-based   implicit/relevant 
                                            or model-free                     
  ----------------------------------------------------------------------------------------

The lecture explicitly notes that not all utility-based agents are
model-based.

## Environment Examples from Lecture

  -----------------------------------------------------------------------
  Environment                         Key classification insight
  ----------------------------------- -----------------------------------
  Chess with clock                    fully observable, multiagent,
                                      deterministic, sequential,
                                      semidynamic, discrete

  Poker                               partially observable, multiagent,
                                      stochastic, sequential, static,
                                      discrete

  Taxi driving                        partially observable, multiagent,
                                      stochastic, sequential, dynamic,
                                      continuous

  Part-picking robot                  partially observable, single-agent,
                                      stochastic, episodic, dynamic,
                                      continuous
  -----------------------------------------------------------------------
