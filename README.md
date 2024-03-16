# Complex Networks Project
Understanding the causes behind the interaction among pharmaceutical drugs and diseases is not an easy task. 
Even if the expertise of doctors can certainly build some level of intuition, it is important to understand that those kind of relationships may be subtle and difficult to discover.
The current project tries to tackle this problem by extracting information from a suitable bipartite graph, that represents pharmacological interaction among drugs and diseases.

# Description of the problem
Suppose that we are able to produce some kind of representation of diseases and chemicals. Let us denote as $X$ the set of diseases, and $Y$ the set of chemicals.
Mathematically speaking, we can define a relationship over the cartesian product of this two sets and we can denote it as $E \subset X \times Y$, representing the known interactions, which are the observed ones.
Let us now denote as $E^\*$ the subset of the cartesian product that represents the true relationship, which is unknown.
The question now is simple. Suppose that there is a couple $(x^\*, y^\*) \in X \times Y$ that does not belong to $E$. What is the likelihood of it appearing in $E^\*$?

In particular given a bipartite graph whose <b> biadjacency matrix </b> $B$ is defined such that

$$
B_{ij} = \begin{cases}
      1 & \textrm{ if the drug } i \textrm{ interacts with the disease } j \\
      0 & \textrm{ if there is no interaction} \\
      0.5 & \textrm{ there is no prior information about interaction }
\end{cases}     
$$

We would like to construct a new matrix $\hat B$ such that

$$
\hat B_{ij} = \begin{cases}
      1 & \textrm{ if the drug } i \textrm{ interacts with the disease } j \\
      0 & \textrm{ if there is no interaction}
\end{cases}     
$$

Trying, therefore to overcome uncertainty in observed data.

# Modellistic Assumption
In order to give a precise answer to the previous question, we should expect to know --- precisely --- the set of rules that describes the establishing of an interaction. As we mentioned, our idea is to try to exploit information contained in data in order to construct empirically some sort of description --- even an approximation --- of them.
Therefore, we make a substantial preliminary assumption

Every $x \in X$ and every $y \in Y$ are equipped with a --- not observable --- <b> information packet </b>. Let us denot as $\mathscr I_X$ and $\mathscr I_Y$ the spaces of information packets for $X$ and $Y$ and let us describe two suitable functions $h_X : X \rightarrow \mathscr I_X$ and $h_Y : Y \rightarrow \mathscr I_Y$ which simply extract the information packet (obviously we are talking in an abstract sense, since those information are not known). 

We make therefore another assumption; the generation of the interaction among objects is a solely a function of the two information packets involved. Formally

$$
\exists \phi : \mathscr I_X \times \mathscr I_Y \rightarrow (0,1)
\textrm{ such that }
\phi(h_X(x),h_Y(y)) \approx 1 \iff (x,y) \in E^\* \ \ \forall x,y \in X \times Y
$$

Basically, we are assuming that there exists a function that given two information packets return a probability of interaction.
Apparently we aren't able to treat this problem. In fact we don't know either $h_X,h_Y$ nor $\phi$.
Suppose now that both $\mathscr I_X$ and $\mathscr I_Y$ are isomorphic to euclidean spaces, which means that it suffices to have a finite number of real parameters to provide a full description of them.
We make now a strong statement: since we are not directly able to describe $h_X$ and $h_Y$ we will describe them in terms of <b> action against objects in the two sets </b>.
Hence instead of retrieving the map $h_X : X \rightarrow \mathscr I_X \sim \mathbb R^n$ we will simply try to retrieve, for each $x \in X$, its image thru this unknown map. And now an even stronger assumption:
Let $f : X \times Y \rightarrow (0,1)$ we can contruct a mapping $h_x : X \mapsto \mathbb R^N$ and $h_y: Y \mapsto \mathbb R^N$ such that

$$
      \underset{N \rightarrow \infty}{\textrm{lim}} || f(\cdot,\cdot) - \sigma \left( h_X(\cdot)^T h_Y(\cdot) \right) || = 0
$$

where $\sigma$ is the  usual sigmoid function.

We will not include proofs of this statement, but as a proof of concept you can imagine this procedure as very similar to overfitting in logistic regression.

# Solution to the problem
Given the aforementioned consideration the discussion can be casted into an optimization problem
$$
\underset{X \in \mathbb R^{N_c,n},Y \in \mathbb R^{N_d,n}}{\textrm{Minimize}} || B - \sigma\left( XY^T \right) ||^2 
$$
In the very same fashion of a logistic regression, but with "data acting also as weights vectors"

# Continuous relaxation of the problem
Unlike logistic regression,t he duality among weights and data make the problem non-convex.
Our strategy is to use a non convex optimization algorith in order to solve it, by creating a sequence of continous relaxations of the problem.

