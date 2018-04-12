## The successor representation in human reinforcement learning    (Week 3 - Pablo)
Memmennejad, Russek, Cheong, Botvinick, Daw and Gershman

### Big picture:				

The paper discusses the classical distinction in reinforcement learning (RL) and psychology between __model-based__ (RL) or __deliberative__ and __model-free__ or habitual choice. Model-based approaches trade flexibility against computational costs, as they constantly have to recompute the utility of actions. In contrast __model-free__ approaches store pre-computed values and are efficient. However, this efficiency comes at the cost of a lack of flexibility to changes in the environment. 
The authors show in between this fundamentally different approaches an intermediate algorithmic family exists that can balances flexibility and efficiency. 
This family of algorithms reuses previously calculated paths given their past utility and thus can match __model-free__ efficiency. If no previous evaluation is applicable the model resembles a __model-based__ approach. The authors call this family of algorithms __successor representations__. 

The paper contrasts the predictions for the three classes of models for changes in task sequences, task rewards and policy changes and compares them to human data. They show that humans exhibit sensitivity for reward changes but not for sequence changes. This asymmetry cannot be accounted for in terms of the classical __model free__ vs. __model based__ accounts, but in terms of __successor representation__ or successor-model based hybrids. 


### Open questions/limits

- The tasks used in the experiments are susceptible to standard criticisms of RL domains. It is unclear if these sort of tasks are representable for real-world situations, where time and space can exhibit non-discrete structure and varying scale of feedback. 
- In the real world the length of successor paths will vary considerably, thus some compression or encoding (for non-trivial/short paths) will be necessary? 
- Path-length also influences confidence in precomputed calculation. 
- It makes sense that some flexibility in reusing subsets of the successors is available. It would have been interesting to see how length of sequences affects human performance and how it compares to the models.


## [Strategy Selection as Rational Metareasoning](https://osf.io/6yugk/download?format=pdf)			(Week 4 - Nicolas)
Falk Lieder and Thomas L. Griffiths

### Big picture:				
The debate on whether people are rational has traditionally been focused on whether people’s judgments and decisions follow the rules of normative theories (e.g. logic or probability). Numerous studies have shown that people systematically violate these. These observed cognitive biases have been shown to stem from people’s use of simple heuristics that sacrifice accuracy for speed and efficiency. Some have argued that these heuristics are a proof against human rationality. Others have tried to understand whether these heuristics are chosen adaptively to their contexts given the limited constraints of an agent (i.e. time and computational resources)- with the hypothesis that people may be resource-rational. This paper tries to understand how people select strategies (/heuristics) to show that people learn to become rational about which strategies they use.

### Model:
The optimal strategy selection learning mechanism maximises the agent’s total expected value of computation across all sequences of possible problems in a given environment, for a set number of strategies.

### Hypotheses: 
- People learn a model (i.e. set of weights) that predicts value of applying a strategy (defined by Utility - Cost) given a problem’s features. (they don’t  just compute an average value across all problems as described by  previous historical models)  
- People’s decisions/predictions improve with experience 
- People learn about the value of strategies and explore to remove uncertainty (hence, explore-exploit dilemma on whether to stick with best predicted strategy. In the model this is done by thompson sampling from the weights distributions. 
- They do this for external and internal representations.
- People predict cost and reward separately (since VOC can not be observed directly)

### Experiments:

#### Experiment 1:
- Sorting selection algorithms problem on different lists  (only 2 strategies)
  - People can select based on features
  
- Risky choice: gambling with different payoffs/probabilities, with vs w/o time constraints.
  - People can do this on interlnal representations
  - People can select adaptively based on resource constraints	

#### Experiment 2 : gambling tasks with different conditions
  - 1) People learn to perform fewer computations when it’s not worth the effort. 
  - 2) People learn to think more when it’s critical (high stakes)
  - 3) People improve in selecting adaptively with experience


### Open questions/limits
The two main limits regard the representation that people hold over their environment, and the "bag" of heuristics people might have. 
- Representation learning
  - Some problems might share similar features and require widely different strategies for optimal performance. Does this dismiss the learned model, or do people hold more intricate representations over contexts?
  - How do we learn/represent the features of a problem, especially in high dimensional spaces? We discussed the example of chess, where choosing a heuristic becomes irrelevant without an understanding of the board. 
- Strategies
  - The second limiting assumption, that the authors also pointed out, is about the strategies available to people (The quantitative differences between the model fits should be taken with a grain of salt because [..] of the assumption that people use the exact [..] strategies available to the models and no other strategies. p.42). How do people acquire/generate new heuristics (e.g. take the best, weighted additive strategy, ...? )?



## Perceptions as Hypothesis, Saccades as experiments (Week 5 - Matt)
Karl Friston, Rick A Adams, Laurent Perrinet, Michael Breakspear

## High level claims
This paper is part of several produced by Friston's group espousing the 'Free Energy Principle'; which claims that organisms act to minimise an upper bound on the log probability of their sensory data, averaged over time, estimated under their model of the world. 

This is argued to be (a) equivalent to the organisms performing approcimate inference on the causes of their sensory data and (b) a necessary consquence of organims' need to minimise the entropy of states they encounter in the world, over time; which in turn is claimed to be a necessary consequence of having evolved to survive as a structured entity in a world governed by the second law of thermodynamics. 

## Process level claims

Internally, this minimisation corresponds to percieving; if equipped with a hierarchical generative model of the sufficient statistics of possible world states, an organism that updates its state to minimise the gap between the actual value of incoming sensory data and its predicted value (activity, firing rate, whatever) should end up in a state that is most isomorphic to (or relevantly representative of) the actual state of the world.

Functionally, the idea of the hierarchical model is that that each level in the hierarchy tries to predict the activity of the one below, and sensory information disseminates up the hierarchy as the errors, or residual signals of this process. This has advantages in that updates need only be local (something that is almost certainly true of most of the brain), and that we can conceive as the hierarchicy as a sort of cerebral sieve; incoming signals are decomposed into subparts which can be modelled, weighted according to our model confidence, and then the unmodelled part passed in for further processing.

Expectations, or priors, flow down the brain; errors, or residuals, flow up. This is supported in a general sense by evidence that there is as much downflow as upflow of signal in the brain. It is much less clear how a neuronal architecture would cope with two distinct types of signals - having different populations of neurons, one for uplflow and one for downflow, would be one solution, but no such structure has been observed.

When the downflow of expectations reach proprioceptive level, action manifests as a result of minimising the error between these expectations and the proprioceptive signals that represent the state of the world. I move my arm to pick up a cup because I expect to move my arm like so, because I am engaged in a task that involves me picking up the cup.

## Model

The implemented model is pretty shallow; the authors simply show that a basic implementation of the free energy maths, where the model can fixate on different parts of an image and is equipped with flat image priors, generates fixations that tend towards the same sorts of places that human fixations do (eyes on a face, for example). This isn't super compelling if you look at their example images; the model just tends to fixate on the patches of highes entropy, which is natural because these will differentiate competing priors most rapidly (which is what the model is set up to do by comuting expected future minimisation in a counterfactual fashion- 'if I look here, how much will my errors be minimised, given what I currently believe?').

## Further comments/ points for discussion

How do we tie this together with rational metareasoning? What would that look like under this model?
The counterfactual processing makes this quite model-based (expected error minimised is computed given some current beliefs at each time step) - is there a way around this?
Dark room problem - if this a fundamental issue with the whole minimsation of sensory entropy account?
Relationship with the 'where rewards come from' paper?
