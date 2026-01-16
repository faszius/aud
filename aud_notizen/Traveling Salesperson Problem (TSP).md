---
tags:
  - foliensatz/07
  - cleaned
aliases:
  - TSP
---

## Traveling Salesperson Problem

Wir schauen uns einen vollständigen (un-)gerichteter Graph $G = (V, E)$ mit Kantengewichten $w: E \rightarrow \mathbb{R}$ an und wollen eine Tour $p$ mit minimalem Kantengewicht $w(p)$ finden.
Dabei ist eine Tour ein Weg $p = (v_0, v_1, \ldots, v_{n-1}, v_n)$ entlang der Kanten $(v_i, v_{i+1}) \in E$ für $i = 0, 1, 2, \ldots, n-1$, der bis auf Start- und Endknoten $v_0 = v_n$ jeden Knoten genau einmal besucht ($V = \{v_0, v_1, \ldots, v_{n-1}\}$).

Ein Graph $G = (V, E)$ ist vollständig, wenn es für alle Knoten $u, v \in V$ mit $u \neq v$ eine Kante $(u, v) \in E$ gibt, also wenn es von jedem Knoten eine Kante zu jedem anderen Knoten gibt.

Wenn der Graph nicht vollständig ist, aber eine Tour hat, kann man eine "verboten teure" Kanten $(u, v)$ mit $w((u, v)) = \vert V \vert \cdot \max_{e \in E}\{e(e)\}+1$ hinzufügen.

![[aud_folien_07_advanced_designs.pdf#page=75|aud_folien_07_advanced_designs, page 75]]

## TSP vs. [[Dijkstra-Algorithmus|Dijkstra]]

Allgemeiner TSP-Algorithmus:
finde optimale Route, die durch jeden Knoten geht und zum Ausgangspunkt zurückkehrt

Dijkstra-Algorithmus:
finde optimalen Pfad vom Ausgangspunkt aus
(besucht evtl. nicht alle Knoten und betrachtet auch nicht Rückkehr)
