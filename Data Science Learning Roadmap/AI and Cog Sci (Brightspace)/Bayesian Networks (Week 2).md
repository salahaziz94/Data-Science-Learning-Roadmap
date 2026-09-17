Both humans and artificial agents act and/or make decisions based on **beliefs** about states in the world, where beliefs can be represented using probability.

_P_ is always a number between 0 and 1, i.e., 0 <= P <= 1

A Bayesian way to decide what action to take: consider not only the probability of the current event but also _information that could affect that probability_.

Notation: P refers to probability. _Prior probability is the degree of belief in something in the absence of other information. _Posterior probability is the degree of belief of something in the presence of other information. 

Bayes' Rule: P(H | e) = (P(e | H)P(H))/P(e)

Where: 
	P(e | H) is the likelihood (how probable is the evidence given that our hypothesis is true); P(H) is the prior (how probable was our hypothesis _before_ considering the evidence); P(e) is the marginal (how probable is the new evidence under all possible hypotheses?); and P(H | e) is the posterior (how probable is our hypothesis given the observed evidence?)

Bayesian Network: a framework for reasoning under uncertainty. It supplies an _inference_ mechanism for: calculating probabilities of events based on prior beliefs, conditional beliefs, and evidence, and doing so efficiently.

A Bayesian Network represents dependencies between variables, and it is a directed acylic graph. (i.e., nodes connected by one-way arrows and no loops). Nodes are connected by arrows. Each node represents a state that we want to model, called a random variable. Each node has a probability distribution encoded in its conditional probability table. 

E.g., one direction, where tampering and fire (individually) --> alarm --> leaving ---< report. 

A probability distribution: probabilities for the node's values given the values of its parents, if any. Each random variable (node) has a set of values it can take on called its _domain_ (typically Boolean but varies).



