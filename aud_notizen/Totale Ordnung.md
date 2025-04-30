---
tags:
  - foliensatz/02/a
  - cleaned
---

Sei $M$ eine nicht leere Menge und $\leq \subseteq M \times M$ eine binäre Relation auf $M$

Die Relation $\leq$ auf $M$ ist genau dann eine totale Ordnung, wenn gilt:

Reflexivität: $\forall x \in M : x \leq x$
(Jedes Element ist kleiner gleich sich selbst)

Transitivität: $\forall x, y, z \in M: x \leq y \land y \leq z \Rightarrow x \leq z$
($x$ kleiner gleich $y$ und $y$ kleiner gleich $z$ bedeutet dass $x$ kleiner gleich $z$)

Antisymmetrie: $\forall x, y \in M: x \leq y \land y \leq x \Rightarrow x = y$
(Wenn $x$ kleiner gleich $y$ und $y$ kleiner gleich $x$ sind $x$ und $y$ gleich, beziehungsweise haben den gleichen Wert)

Totalität: $\forall x, y \in M: x \leq y \lor y \leq x$
(Jedes beliebige Paar an Werten ist miteinander vergleichbar)

Bemerkung: Totale Ordnung $\leq$ impliziert Relation $>$ durch $x > y \Leftrightarrow \neg (x \leq y)$