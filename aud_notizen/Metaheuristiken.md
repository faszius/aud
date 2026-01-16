---
tags:
  - foliensatz/07
  - "#MoC"
  - cleaned
Related:
  - "[[Hill-Climbing]]"
  - "[[Iterative Lokale Suche]]"
  - "[[Simulated Annealing]]"
---

## Heuristiken Und Metaheuristiken

Heuristik:
dedizierter Suchalgorithmus für ein Optimierungsproblem,
der eine gute (aber evtl. nicht optimale) Lösung für ein spezielles Problem findet
Ist also problem-abhängig, arbeitet direkt "am" Problem

## Metaheuristik

Allgemeine Vorgehensweise, um die Suche für ein beliebiges Optimierungsproblem zu leiten
Ist also problem-unabhängig, arbeitet mit abstrakten Problemen

## Lokale Suche

Wir befinden uns in diesem Fall in einem abstrakten "Raum voller Lösungen" und wollen die "beste Lösung" finden - wie gehen wir vor?

![[aud_folien_07_advanced_designs.pdf#page=83|aud_folien_07_advanced_designs, page 83]]

## Lokale vs. Globale Maxima

Eine Möglichkeit ist [[Hill-Climbing|Hill Climbing]], Eventuell bleibt der Hill-Climbing-Algorithmus jedoch in einem lokalen Maximum hängen, da wir nur leichte Lösungsänderungen in aufsteigender Richtung übernehmen

![[aud_folien_07_advanced_designs.pdf#page=86|aud_folien_07_advanced_designs, page 86]]

### Lokale vs. Globale Maxima Beim [[Traveling Salesperson Problem (TSP)|TSP]]

Wir betrachten lokale und globale Maxima beim Traveling Salesperson Problem:

![[aud_folien_07_advanced_designs.pdf#page=87|aud_folien_07_advanced_designs, page 87]]

Wir vertauschen so lange zwei Knoten in der Reihenfolge, bis wir ein Maximum erreichen, in diesem Fall den Pfad $1 \rightarrow 2 \rightarrow 3 \rightarrow 5 \rightarrow 4 \rightarrow 1$. An diesem Punkt lässt sich keine bessere Lösung mehr finden, indem man zwei Knoten vertauscht, wir haben also ein lokales Maximum gefunden.

![[aud_folien_07_advanced_designs.pdf#page=88|aud_folien_07_advanced_designs, page 88]]

Tauschen wir $4$ und $5$, erhalten wir eine Lösung, die schlechter ist als die vorige. Tauschen wir dann jedoch $3$ und $5$, finden wir die optimale Lösung. Wir mussten also das lokale Maximum verlassen und eine schlechtere Lösung besuchen, um das globale Maximum zu finden.

![[aud_folien_07_advanced_designs.pdf#page=89|aud_folien_07_advanced_designs, page 89]]

In einem Graphen veranschaulicht sieht das Ganze dann so aus:

![[aud_folien_07_advanced_designs.pdf#page=90|aud_folien_07_advanced_designs, page 90]]

## Weitere Metaheuristiken

Tabu Search
- Ausgehend von der aktuellen Lösung, suche eine bessere Lösung in der Nähe
- Speichere eine Zeit lang schon besuchte Lösungen, und vermeide diese Lösungen
- Wenn keine bessere Lösung in der Nähe, akzeptiere auch schlechtere Lösung

Evolutionäre Algorithmen
- Beginne mit Lösungspopulation
- Wähle beste Lösungen zur Reproduktion aus
- Bilde durch Überkreuzungen und Mutationen der besten Lösungen neue Lösungen
- Ersetze schlechteste Lösung durch diese neue Lösungen

