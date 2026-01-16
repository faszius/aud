---
tags:
  - foliensatz/06
  - cleaned
aliases:
  - DMST
  - Directed MST
  - Gerichteter MST
  - Gerichteten MST
Related:
  - "[[Algorithmus von Kruskal]]"
  - "[[Algorithmus von Prim]]"
  - "[[Minimale Spannbäume (MST)]]"
---
Ein directed [[Minimale Spannbäume (MST)|MST]] (DMST) in Wurzelknoten `r` ist ein Spannbaum mit minimalen Gewicht (über alle Spannbäume mit Wurzel `r`)

![[aud_folien_06_graphen_algorithmen.pdf#page=118|aud_folien_06_graphen_algorithmen, page 118]]

[[Algorithmus von Prim|Prims Algorithmus]] findet einen Spannbaum mit Wurzel `r` (sofern es einen gibt), aber nicht immer einen minimalen Spannbaum

![[aud_folien_06_graphen_algorithmen.pdf#page=119|aud_folien_06_graphen_algorithmen, page 119]]

[[Algorithmus von Kruskal|Kruskals Algorithmus]] findet evtl. keinen Spannbaum mit Wurzel `r`:

![[aud_folien_06_graphen_algorithmen.pdf#page=120|aud_folien_06_graphen_algorithmen, page 120]]

Wenn man in der Iteration bereits besuchte Knoten ausschließt findet [[Algorithmus von Kruskal|Kruskals Algorithmus]] evtl. keinen minimalen Spannbaum mit Wurzel `r`:

![[aud_folien_06_graphen_algorithmen.pdf#page=121|aud_folien_06_graphen_algorithmen, page 121]]