Mesa-optimization is a concept from AI alignment. It is directly relevant to theories of [[surrogation]], [[opticratics]], and (most centrally), [[coordination]]. 

To be a "mesa-optimizer" is merely to take a perspective in a system of layers. While the coining authors discuss systems that have a single base-optimizing layer and a single mesa-optimizing layer, there can be many systems of nested selection and optimization. Many [[superorganisms]] are composed of nested optimization layers or [[Markov blankets]]: societies are selected based on economic power within the larger geopolitical landscape; governments attempt to incentivize and assist businesses which can usher in economic flourishing; these businesses have their own goals only partially aligned with the government's, and their economic success within the larger market is largely premised on employee behavior; companies hire and promote employees that they believe will advance their own goals; these employees have goals of their own which are only somewhat aligned with the goals of their employer, etc.

A given generation of mesa optimizer is only guaranteed to meet the criteria of the base optimizer conditional on the environment being identical to that experienced by the previous generation." (Which is impossible in all real-world, open/complex systems, in which no two states are ever identical.)

# Hubringer et al 2019: Risks from Learned Optimization

## What is mesa optimization?

![](/mesaOptimization.jpg)

The authors introduce the concept of _mesa-optimization_, 

> a framework that distinguishes what a system is optimized to do (its “purpose”), from what it optimizes for (its “goal”), if it optimizes for anything at all

Mesa-optimizers are selected by "base optimizers." "Inner alignment" refers to an alignment between the base and mesa optimizer. 

Not all optimized systems optimize (i.e., are "mesa"): a bottlecap is optimized to selectively contain and release liquids from a bottle, but it is not an optimizer. It has been optimized by human beings (much like, say, our food as superstimulus). A system is an optimizer "if it is internally searching through a search space (consisting of possible outputs, policies, plans, strategies, or similar) looking for those elements that score high according to some objective function that is explicitly represented within the system." 

Mesa-optimizers are not dedicated to optimization per se, rather, the optimization is a natural strategy of a dynamic, adaptive agent to achieving their actual end goals, or "scoring high" in their situating reward function.

The "base objective" is the "criterion the base optimizer was using to select between different possible systems." The "mesa objective" is "whatever criterion the mesa-optimizer is using to select between different possible outputs." 

> In reinforcement learning (RL), for example, the base objective is generally the expected return. Unlike the base objective, the mesa-objective is not specified directly by the programmers. Rather, the mesa-objective is simply whatever objective was found by the base optimizer that produced good performance on the training environment.

The authors are careful to distinguish the mesa-optimizer from a "sub-agent"; in their factoring, they are strictly discussing algorithms. They also distinguish mesa-objective from what they call the "behavioral objective," which is "the objective which appears to be optimized by the system's behavior," the objective "recovered" from observation rather than that which actually drives its behavior.

## Types of alignment

_Pseudo-alignment_ is when the mesa-objective and base objective appear aligned in training, but decouple when exposed to non-train environments. There is inner alignment (between base and mesa optimizer) and outer alignment.

The _inner alignment problem_ stands in contrast to the _outer alignment problem_, which the authors characterize as "the gap between the base objective and the intended goal of the programmers." That is, the outer alignment problem is one of specifying, in letter, the spirit of a selection mechanism—implementing a reward function that actually matches the subjective, holistic decisions the designer would make. 

> A given mesa-optimizer’s mesa-objective is determined entirely by its internal workings. Once training is finished and a learned algorithm is selected, its direct output—e.g. the actions taken by an RL agent—no longer depends on the base objective. Thus, it is the mesa-objective, not the base objective, that determines a mesa-optimizer’s behavioral objective. Of course, to the degree that the learned algorithm was selected on the basis of the base objective, its output will score well on the base objective. However, in the case of a distributional shift, we should expect a mesa-optimizer’s behavior to more robustly optimize for the mesa-objective since its behavior is directly computed according to it.

Evolution vs. human behavior is an example of this uncoupling:

> The objective function stored in the human brain is not the same as the objective function of evolution. Thus, when humans display novel behavior optimized for their own objectives, they can perform very poorly according to evolution’s objective. Making a decision not to have children is a possible example of this. Therefore, we can think of evolution as a base optimizer that produced brains—mesa-optimizers—which then actually produce organisms’ behavior—behavior that is not necessarily aligned with evolution.

_Robust alignment_: when "mesa-optimizers with mesa-objectives... robustly agree with the base objective across distributions." This is compared to "pseudo-aligned" systems, which "refer to mesa-optimizers on past training data, but not robustly across possible future data." Pseudo-aligned systems require an environment "in which the base and mesa-objectives diverge." We might think of this as the [[indexicality]] of a spirit's [[spirit vs letter|implementation in letter]]: problems emerge when we port one implementation to a new environment, where the previous implementation's choice elisions and distinctions no longer carve the new territory as they did in a previous environment.

Finally, the authors introduce _deceptive alignment_: "wherein a sufficiently capable misaligned mesa-optimizer could learn to behave as if it were aligned without actually being robustly aligned." Deceptive alignment, cf. [[Opticratics]], is a kind of biding ones time, giving the appearance of coordinating while secretly defecting.