---
tags:
  - foliensatz/06
  - cleaned
aliases:
  - A*
  - A*-Algorithmus
---

## A*-Algorithmus

In diesem Spezialfall suchen wir direkt von einem Knoten die schnellste Verbindung zu einem anderen Knoten, ohne uns um die schnellste Verbindung zu anderen Knoten zu kümmern

![[aud_folien_06_graphen_algorithmen.pdf#page=173|aud_folien_06_graphen_algorithmen, page 173]]

Die Idee ist, dass wir eine Heuristik hinzufügen, die uns grob sagt, welcher Knoten wie weit vom Ziel entfernt ist (z.B. wäre eine Heuristik im echten Leben die Luftlinie zwischen Städten)
Jeder Knoten `u` bekommt also zusätzlich einen Wert `u.heur` zugewiesen
Und das Minimum bestimmen wir über `u.dist` + `u.heur`

![[aud_folien_06_graphen_algorithmen.pdf#page=174|aud_folien_06_graphen_algorithmen, page 174]]

## Heuristiken

A* findet die optimale Lösung, wenn gilt:
1. Die Heuristik überschätzt nie tatsächliche Kosten:
   $\texttt{u.heur} \leq \text{shortest}(\texttt{u}, \texttt{t})$
und
2. Die Heuristik ist monoton, d.h. für alle $(\texttt{u}, \texttt{v}) \in E$ gilt:
   $\texttt{u.heur} \leq \texttt{w}(\texttt{u}, \texttt{v}) + \texttt{v.heur}$

## A* Und [[Dijkstra-Algorithmus|Dijkstra]]

Dijkstra ist A* mit Heuristik 0

A* mit monotoner Heuristik ist Dijkstra mit Kantengewichten $\texttt{w}(\texttt{u}, \texttt{v}) + \texttt{v.heur} - \texttt{u.heur}$ und $\texttt{s.dist} = \texttt{s.heur}$

![[aud_folien_06_graphen_algorithmen.pdf#page=176|aud_folien_06_graphen_algorithmen, page 176]]