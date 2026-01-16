---
tags:
  - foliensatz/08
  - cleaned
  - "#MoC"
Related:
  - "[[Komplexitätsklassen P und NP]]"
  - "[[P vs. NP vs. NPC]]"
  - "[[2-Färbbarkeit und 2SAT in P]]"
  - "[[NP-Vollständigkeit]]"
  - "[[Berechnungsprobleme vs. Entscheidungsprobleme]]"
---

## Leichte Und (nicht zu) Schwierige Probleme

Ansatz: Ein Problem ist "leicht", wenn es in Polynomialzeit lösbar ist, wenn die (Worst-Case-)Laufzeit des Algorithmus' also $\Theta(\sum_{i=0}^k a_in^i) = \text{poly(n)}$ für konstante $a_i, k$ ist

Wir unterscheiden weiter zwischen leicht zu lösenden Problemen:
- Sortieren eines Arrays
- [[Breadth-First-Search (BFS)|Breitensuche]] im Graphen
- [[Minimale Spannbäume (MST)|Minimale Spannbäume]] berechnen
- ...
Leicht zu überprüfende Lösungen:
- [[Traveling Salesperson Problem (TSP)|TSP]]
- Faktorisieren
- ...
Und unentscheidbaren Problemen:
- Halteproblemen
- Code-Erreichbarkeit
- ...