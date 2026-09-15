# Lecture 3 - Neural Computation

*Source: Lecture 3, slides 1–115.*

## Big Picture
The lecture develops neural computation from biological signaling through simplified neuron models, neural codes, network architectures, plasticity, sensory computation, and large-scale brain networks.

## Roadmap
1. Nervous system, brain, and neurons
2. Neural signaling
3. Single-neuron models
4. Neural coding and discrimination
5. Network architectures
6. Synaptic plasticity
7. Neural information-processing examples
8. Retina and visual feature detection
9. Detailed neural activation
10. Large-scale brain networks

## Learning Objectives
- Explain membrane potential, action potentials, EPSPs, IPSPs, synapses, and refractory periods.
- Compare threshold, rate, integrate-and-fire, Izhikevich, and biophysical models.
- Distinguish rate, temporal, synchrony, spatial, and spatiotemporal coding.
- Explain feed-forward, recurrent, CPG, retinotopic, lateral-inhibition, and WTA networks.
- Interpret Hebbian learning, gated Hebbian rules, and STDP.
- Explain receptive fields, feature detectors, population codes, place cells, and grid cells.
- Distinguish structural and functional connectivity and integration vs segregation.

## 60-Second Summary
Neurons integrate postsynaptic potentials over dendrites and soma. If somatic membrane potential reaches threshold, an action potential is generated and propagated down the axon. Computational neuron models preserve different amounts of this biology. Information may be represented by firing rate, spike timing, synchrony, or distributed population activity. Network connectivity creates additional computations such as competition, oscillation, recurrence, and spatial mapping. Synaptic plasticity changes connections through activity and timing. These principles scale from retinal feature detection to spatial representation, motor control, and dynamic brain-wide functional networks.

## 1. Biological Neurons and Synapses
*Slides 2–17.*

Slides 2–6 introduce the nervous system, brain architecture, and multiple neuron morphologies: cortical pyramidal cells, hippocampal pyramidal cells, cerebellar Purkinje cells, and retinal amacrine cells. The common computational organization is dendritic input, somatic integration, and axonal output.

Neurons connect at directed **synapses**. The sender is presynaptic; the receiver is postsynaptic. Every neuron has a membrane potential, with resting potential given as roughly **-65 mV to -90 mV**.

If somatic membrane potential rises above firing threshold, the neuron emits an **action potential**, described as rising to about +30 mV and lasting about 1 ms. A refractory period follows.

Slide 9 explains saltatory conduction: myelin limits charge leakage, while nodes of Ranvier regenerate the spike.

An arriving presynaptic action potential causes neurotransmitter release and a postsynaptic potential:
- EPSP = excitatory postsynaptic potential.
- IPSP = inhibitory postsynaptic potential.

PSPs integrate throughout dendrites and soma. If the combined effect reaches threshold, the neuron fires.

### Dale's Law
The lecture states that a biological presynaptic neuron either excites all targets or inhibits all targets according to its neurotransmitter. ANN units typically relax this and may have both positive and negative weighted connections.

Slides 15–17 demonstrate threshold computation: one input pattern produces total activation above threshold and fires; another includes enough inhibition to remain below threshold.

Links: [[Concepts/Ch03 - Biological Neuron and Synapse|Biological Neuron and Synapse]], [[Concepts/Ch03 - Membrane Potential and Action Potential|Membrane Potential and Action Potential]], [[Concepts/Ch03 - Excitation Inhibition and Neural Integration|Excitation, Inhibition, and Neural Integration]].

## 2. Single-Neuron Models
*Slides 18–21.*

| Model | Lecture characterization |
|---|---|
| Multi-compartment biophysical | Neurotransmitters, receptors, ion channels, morphology, membrane dynamics |
| Integrate-and-fire | Single compartment, synaptic integration, threshold, spikes/reset |
| Izhikevich | Phenomenological spiking model capable of realistic spike shapes/types |
| Rate | Summed input, no internal dynamics, simple response |
| Threshold | Summed input, no internal dynamics, all-or-none response |

The simplified neuron computes a weighted net input and applies a response function:

$$
s_i=\sum_j w_{ij}x_j
$$

$$
y_i=f(s_i)
$$

See [[Concepts/Ch03 - Computational Neuron Models|Computational Neuron Models]] and [[Mathematics/Ch03 - Mathematics|Mathematics]].

## 3. Neural Discrimination and Coding
*Slides 22–28.*

**Discrimination** separates input classes using a threshold. **Tuning** gives a strong response over a preferred stimulus range. The slide summarizes: **tuning is a rough measurement; discrimination is classification.**

Spatial discrimination depends on patterns across inputs. Temporal discrimination depends on spike sequences. Spatiotemporal discrimination depends jointly on where and when spikes occur; slide 24 emphasizes coincidence.

**Rate coding** represents stimulus information through firing frequency. **Temporal coding** uses repeatable spike patterns. **Synchrony-based coding** uses coordinated timing; slide 28 presents synchrony as a solution to the binding problem.

See [[Concepts/Ch03 - Neural Coding|Neural Coding]].

## 4. Network Architectures
*Slides 29–34.*

Canonical networks:
- Central Pattern Generators: repeating activity for gait, breathing, etc.
- Retinotopic networks: preserve spatial relationships across layers.
- Lateral inhibition/excitation networks: structured competition/cooperation.
- Recurrent networks: feedback supports equilibria, sequences, and attractors.
- Feed-forward networks: lower layers project only toward higher layers.

Slides 31–32 show CPG oscillators and quadruped locomotion. Each limb has a unit CPG; interactions among CPGs generate coordinated patterns under simple top-down drive/modulation.

Slide 34 shows winner-take-all competition: primary neurons laterally inhibit one another until an initially advantaged neuron dominates.

See [[Concepts/Ch03 - Neural Network Architectures|Neural Network Architectures]].

## 5. Synaptic Plasticity
*Slides 35–42.*

The basic Hebb rule is:

$$
\Delta w_{ij}(t)=\eta y_j(t)y_i(t)
$$

For binary activity:

$$
\bar w_{ij}\propto\langle y_i y_j\rangle
$$

The lecture explicitly states that the basic rule is **dynamically unstable** and summarizes it as **"Neurons that fire together wire together."**

The presynaptically gated rule is:

$$
\Delta w_{ij}(t)=\eta y_j(t)[y_i(t)-w_{ij}(t)]
$$

For binary activity, its equilibrium weight is:

$$
\bar w_{ij}\approx p(y_i=1\mid y_j=1)
$$

The postsynaptically gated rule is:

$$
\Delta w_{ij}(t)=\eta y_i(t)[y_j(t)-w_{ij}(t)]
$$

with:

$$
\bar w_{ij}\approx p(y_j=1\mid y_i=1)
$$

Slide 41 derives the conditional-probability interpretation and explains that the gated rule is self-stabilizing for small learning rate.

Slide 42 introduces STDP. Weight change depends on:

$$
T_{post}-T_{pre}
$$

and the timing curve distinguishes LTP and LTD.

See [[Algorithms/Ch03 - Hebbian Learning Rules|Hebbian Learning Rules]], [[Algorithms/Ch03 - Spike Time-Dependent Plasticity|Spike Time-Dependent Plasticity]], and [[Mathematics/Ch03 - Mathematics|Mathematics]].

## 6. Neural Information Processing Examples
*Slides 43–52.*

Slide 44 shows a direction- and stimulus-specific working-memory neuron that maintains activity after the stimulus disappears until a response is produced.

Slide 45 shows motor-cortex direction tuning with a cosine-like tuning curve. Movement direction is represented across a population.

Slides 46–47 show distributed coding and hippocampal place cells. Slide 48 introduces grid cells, whose firing fields form grid patterns; nearby cells may share spatial frequency/orientation but differ by offset. The lecture presents grid and place cells as cooperating in spatial representation.

Slide 50 shows distributed feature-specific activity in macaque inferotemporal cortex. Complex objects are represented by combinations of feature columns.

Slides 51–52 show somatosensory and motor homunculi, emphasizing unequal cortical representation of body regions.

See [[Concepts/Ch03 - Population and Distributed Coding|Population and Distributed Coding]].

## 7. Retina, Receptive Fields, and Feature Detection
*Slides 53–72.*

The retinal pathway includes photoreceptors, bipolar cells, ganglion cells, horizontal cells, and amacrine cells, with ganglion-cell output forming the optic nerve toward the LGN.

A **receptive field** is the sensory region influencing a neuron's response. **Retinotopic mapping** preserves spatial relationships.

Slides 59–62 build an on-center/off-surround ganglion cell: center excitation and surround inhibition make the cell sensitive to spatial contrast.

Slides 63–64 show visual-cortex feature detectors such as edge and orientation detectors.

Slides 65–72 build a simplified letter recognizer. Feature detectors create a feature vector, then a classifier produces the output. The initial design cannot distinguish A and Z; adding inhibition and changing threshold resolves the ambiguity. Sharper feature detectors use excitation from selected pixels and inhibition from the rest.

See [[Concepts/Ch03 - Receptive Fields and Feature Detection|Receptive Fields and Feature Detection]].

## 8. Appendix: Detailed Neural Activation
*Slides 73–94.*

Slides 76–80 explain membrane voltage from asymmetric ion distributions and selective permeability. Potassium is more concentrated inside and sodium outside. Slide 79 names the Goldman-Hodgkin-Katz equation and states that when sodium permeability is approximately zero, potassium equilibrium potential approximates resting potential.

Slide 82 distinguishes ligand-gated and voltage-gated channels. Ligand-gated channels contribute to PSPs; voltage-gated channels generate and propagate action potentials.

Slide 86 gives the electrical membrane model:

$$
I_C=C\frac{dV_m}{dt}
$$

$$
I_{Na}=g_{Na}(V_m-V_{Na}),\quad
I_K=g_K(V_m-V_K),\quad
I_{Cl}=g_{Cl}(V_m-V_{Cl})
$$

Slides 87–92 introduce Hodgkin-Huxley gating variables \(m,h,n\). Sodium conductance is \(g_{Na}m^3h\), while potassium conductance is \(g_Kn^4\). Rapid sodium activation drives depolarization; sodium inactivation and slower potassium activation drive repolarization/hyperpolarization and contribute to refractoriness.

Slides 93–94 show compartmental neuron models with connected passive and active compartments.

See [[Concepts/Ch03 - Detailed Neural Activation|Detailed Neural Activation]].

## 9. Large-Scale Brain Networks
*Slides 95–115.*

Slide 96 depicts multi-scale cortical modularity. Slide 97 places perception, cognition, and action around 100 ms–1 s among a hierarchy of longer phenomenological time scales.

Slide 98 presents the perception-action cycle as **Sense → Think → Act** through sensory, association, prefrontal/premotor, and motor systems.

Slides 99–102 discuss stereotypical actions, sequential movement, and motor synergies.

> [!question]
> **Professor Questions from slide 101**
> - Where are the synergies stored?
> - How are they configured (genetic or learned)?
> - How are gains and delays specified?
> - How and where are new actions learned?
>
> The slide raises these as questions rather than supplying definitive answers.

Slide 103 compares random, small-world, and fat-tailed network structures.

Slide 105 discusses segregation and integration. A strongly connected high-degree core or **rich club** links functional communities.

Slide 106 shows similar local gamma power with and without perception but much higher cross-regional coherence during perception, emphasizing emergent coordination.

Slides 107–111 distinguish structural and functional connectivity. Slide 108 introduces transfer entropy and states that nonzero TE indicates causal influence from \(y_t\) to \(x_{t+1}\) in the lecture's formulation.

Slides 109–114 show dynamic functional communities. Slide 113 names five: SSM, TIL, TPN, TNN, and VIS. Connectivity changes dramatically across successive 60-second windows.

See [[Concepts/Ch03 - Large Scale Brain Networks|Large-Scale Brain Networks]].
