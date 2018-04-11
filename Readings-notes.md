# Week 4 - Nicolas

## Strategy Selection as Rational Metareasoning			
Falk Lieder and Thomas L. Griffiths

### Big picture:				
The debate on whether people are rational has traditionally been focused on whether people’s judgments and decisions follow the rules of normative theories (e.g. logic or probability). Numerous studies have shown that people systematically violate these. These observed cognitive biases have been shown to stem from people’s use of simple heuristics that sacrifice accuracy for speed and efficiency. Some have argued that these heuristics are a proof against human rationality. Others have tried to understand whether these heuristics are chosen adaptively to their contexts given the limited constraints of an agent (i.e. time and computational resources)- with the hypothesis that people may be resource-rational. This paper tries to understand how people select strategies (/heuristics) to show that people learn to become rational about which strategies they use.

### Model:
The optimal strategy selection learning mechanism maximises the agent’s total expected value of computation across all sequences of possible problems in a given environment, for a set number of strategies.
#### Hypothesis: 
People learn a model (i.e. set of weights) that predicts value of applying a strategy (defined by Utility - Cost) given a problem’s features. 

### Hypotheses: 
- People predict individual strategies’ value for each problem based on problem features (they don’t  just compute an average value across all problems as described by  previous historical models)  
- People’s decisions/predictions improve with experience 
- People learn about the value of strategies and explore to remove uncertainty (hence, explore-exploit dilemma on whether to stick with best predicted strategy 
- They do this for external and internal representations.
- People predict cost and reward separately (since VOC can not be observed directly)

### Experiments:
#### Experiment 1:
- Sorting selection algorithms problem on different lists  (only 2 strategies)
  - People can select based on features
  
- Risky choice: gambling with different payoffs/probabilities, with vs w/o time constraints.
  - People can do this on interlnal representations
  - People can select adaptively based on resource constraints	

#### Experiment 2 : gambling tasks with different conditions
  - 1) People learn to perform fewer computations when it’s not worth the effort. 
  - 2) People learn to think more when it’s critical (high stakes)
  - 3) People improve in selecting adaptively with experience


### Open questions/limits
