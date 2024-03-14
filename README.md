# Complex Networks Project
Understanding the causes behind the interaction among pharmaceutical drugs and diseases is not an easy task. 
Even if the expertise of doctors can certainly build some level of intuition, it is important to understand that those kind of relationship may be subtle and difficult to discover.
The current project tries to tackle this problem by extracting information from a suitable bipartite graph, that represents pharmacological interaction among drugs and diseases.

# Description of the problem
Suppose that we are able to produce some kind of representation of diseases and chemicals. Let us denote as $X$ the set of diseases, and $Y$ the set of chemicals.
Mathematically speaking, we can define a relationship over the cartesian product of this two sets and we can denote it as $E \subset X \times Y$, representing the known interactions, which are the observed ones.
Let us now denote as $E^\*$ the subset of the cartesian product that represents the true relationship, which is unknown.
The question now is simple. Suppose that there is a couple $(x^\*, y^\*) \in X \times Y$ that does not belong to $E$. What is the likelihood of it appearing in $E^\*$?

# Modellistic Assumption
In order to give a precise answer to the previous question, we should expect to know --- precisely --- the set of rules that describes the establishing of an interaction. As we mentioned, our idea is to try to exploit information contained in data in order to construct empirically some sort of description --- even an approximation --- of them.
Therefore, we make a substantial preliminary assumption

Every $x \in X$ and every $y \in Y$ are equipped with a --- not observable --- <b> information packet </b>. Let us denot as $\mathscr I_X$ and $\mathscr I_Y$ the spaces of information packets for $X$ and $Y$ and let us describe two suitable functions $h_X : X \rightarrow \mathscr I_X$ and $h_Y : Y \rightarrow \mathscr I_Y$ which simply extract the information packet (obviously we are talking in an abstract sense, since those information are not known). 

We make therefore another assumption; the generation of the interaction among objects is a solely a function of the two information packets involved. Formally
$$
\exists \phi : \mathscrI_X \times \mathscrI_Y \rightarrow \{0,1\}
$$



%Lo scopo del progetto é quello di analizzare un grafo bipartito $\mathcal G(X,Y,E)$ dove $X$ é l'insieme dei DISEASE , $Y$ é l'insieme dei CHEMICALS e $E \subset X \times Y$ é l'insieme dei collegamenti che %indicano un'interazione malattia-farmaco.<br>
%L'algoritmo chiave é il seguente.<br>
%Immaginiamo che ogni DISEASE $x$ possieda un pacchetto di informazione ${\bf v_x}$ e ogni CHEMICAL $y$ possieda un pacchetto di informazione ${\bf w_y}$ <br>
%Denotiamo come $V := \{ {\bf v_x} : x \in X \}$ e $W := \{ {\bf w_y} : y \in Y \}$ <br>
%Consideriamo la mappa $a : V \times W \rightarrow (0,1)$ , con $a({\bf v_x},{\bf w_y}) = tanh( {\bf v_x} \cdot {\bf w_y} )$
