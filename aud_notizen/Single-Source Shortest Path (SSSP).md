---
tags:
  - foliensatz/06
  - cleaned
aliases:
  - SSSP
  - Single-Source Shortest Path
  - Single Source Shortest Path
---

## Single-Source Shortest Path (SSSP)

Finde von Quelle $s$ aus jeweils den (gemäß den Kantengewichten) kürzesten Pfad zu allen anderen Knoten

Die Länge eines Pfades $p = (v_1, \ldots, v_k) \in V^k$ von $u = v_1$ zu $v = v_k$ ist dann definiert als:
$w(p) = \sum_{i=1}^{k-1}((v_1, v_{i+1}))$

$$\text{shortest}(u, v) = 
\begin{cases*}
\min \{w(p): p & \text{Pfad von $u$ nach $v$ \}} \\
\infty & \text{wenn $v$ erreichbar von $u$ sonst} 
\end{cases*}$$

## SSSP vs. [[Breadth-First-Search (BFS)|BFS]], [[Depth-First Search (DFS)|DFS]], [[Minimale Spannbäume (MST)|MST]]

BFS + DFS benutzen beide keine Kantengewichte
BFS findet die kürzesten "Kantenwege", aber nicht die kürzesten "Gewichtswege"

MST (für ungerichtete Graphen) minimiert das Gesamtgewicht des Baumes
Unter Umständen ist der kürzeste Weg von einem Knoten zum anderen dann nicht im Baum enthalten

![[aud_folien_06_graphen_algorithmen.pdf#page=124|aud_folien_06_graphen_algorithmen, page 124]]