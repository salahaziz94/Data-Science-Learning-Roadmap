PSSH informed methods toward AI. General Problem Solver (GPS) was able to solve simple _toy_ problems (Tower of Hanoi, Sliding Tile Puzzle) but couldn't handle real world problems due to too much information. This eventually developed into a common model of cognition, i.e., SOAR architecture. 

**Problem Solving**: the process of _searching_ through the _problem space_ until a _goal state_ is found. We start with an _initial state_, and go through _operators_ (transform given a state to another state) until we reach our _goal state_.

**Problem space**: (a.k.a. the search space) is the set of all possible problem "states". This can be represented via a graph, tree, etc.

A state is a representation of the problem in some "degree" of solution. But the path from the initial state to the goal state represents the solution.  To get the solution, a AI operates on the according to the _search strategy_, applying the relevant operators. The search strategy determines in what order states are tested to see if they are the goal. 

An algorithm is the "recipe" in which the task can be accomplished. We have _uninformed search_ and _informed search_.  
	**Uninformed search**: no domain-specific knowledge is used. Unfortunately, this means it can take a very long time to reach solutions.
		Breadth first search (BFS): we go through all the nodes in a current 'row', adding each node children, before the next row. This is a queue , where it is a (FIFO) first in, first out structure. The code here in Python would be, to pop(0).
		Depth first search (DFS): we go through the entire depth in a current 'column', adding each node children, before the next column. This is a stack, where it is (LIFO) last in, first out structure. The code here in Python would be, to pop(-1).
	**Informed search**: heuristics are used to simplify the search.
			Not every heuristic is _admissable_. We don't want them that overestimate the true cost or distance to reach the goal state. Manhattan Difference (MD) = absolute difference between the x-coordinates and y-coordinates of two points. |x1-x2| + |y1-y2| (Skipping the rest of these lectures)
	