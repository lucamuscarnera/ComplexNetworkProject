# ComplexNetworkProject
Lo scopo del progetto é quello di analizzare un grafo bipartito $\mathcal G(X,Y,E)$ dove $X$ é l'insieme dei DISEASE , $Y$ é l'insieme dei CHEMICALS e $E \subset X \times Y$ é l'insieme dei collegamenti che indicano un'interazione malattia-farmaco.<br>
L'algoritmo chiave é il seguente.<br>
Immaginiamo che ogni DISEASE $x$ possieda un pacchetto di informazione ${\bf v_x}$ e ogni CHEMICAL $y$ possieda un pacchetto di informazione ${\bf w_y}$ <br>
Denotiamo come $V := { {\bf v_x} : x \in X} $ e $W := { {\bf w_y} : y \in Y }$
