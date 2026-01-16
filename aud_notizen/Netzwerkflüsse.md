---
tags:
  - foliensatz/06
  - cleaned
aliases:
  - Fluss
---

## Netzwerkflüsse: Idee

Kanten haben einen (aktuellen) Flusswert und eine (maximale) Kapazität
Jeder Knoten außer $s$ und $t$ hat den gleichen eingehenden und ausgehenden Fluss
Ziel: Finde maximalen Fluss von $s$ nach $t$

![[aud_folien_06_graphen_algorithmen.pdf#page=179|aud_folien_06_graphen_algorithmen, page 179]]

## Definition

Ein Flussnetzwerk ist ein gewichteter, gerichteter Graph $G = (V, E)$, in dem jede Kante eine Kapazität(sgewicht) $c$ hat, sodass $c(u, v) \geq 0$ für $(u, v) \in E$ und $c(u, v) = 0$ für $(u, v) \notin E$.
Zudem gibt es zwei Knoten $s, t \in V$ (Quelle und Senke), sodass jeder Knoten von $s$ aus erreichbar ist und $t$ von jedem Knoten aus erreichbar ist.

Ein Fluss für ein Flussnetzwerk $G = (V, E)$ (mit Kapazität $c$, Quelle $s$ und Senke $t$) ist eine Funktion $f: V \times V \rightarrow \mathbb{R}$. 
Für alle $u, v \in V$ ist  $0 \leq f(u, v) \leq c(u, v)$, der Fluss ist also kleiner gleich dem Kapazitätsgewicht .
Zudem gilt für jeden Knoten bis auf Quelle und Senke $u \in V - \{s, t\}$, dass der eingehende Fluss dem ausgehenden Fluss entspricht:
$\sum_{v \in V}f(u, v) = \sum_{v \in V}f(v, u)$

