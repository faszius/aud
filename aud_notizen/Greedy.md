---
tags:
  - foliensatz/07
  - cleaned
---

## Prinzip Greedy

Finde Lösungen $x = (x_1, x_2, \ldots, x_2)$ indem die Teillösung $(x_1, x_2, \ldots, x_{i-1})$ durch den Kandidaten $x_i$ ergänzt wird, der lokal am günstigsten erscheint.

## Unsere Greedy-Algorithmen

Beispielsweise [[Dijkstra-Algorithmus|Dijkstra]] und [[Algorithmus von Kruskal|Kruskal]]

![[aud_folien_07_advanced_designs.pdf#page=73|aud_folien_07_advanced_designs, page 73]]

### Probleme Mit Greedy

Greedy-Algorithmen funktionieren nicht immer!

![[aud_folien_07_advanced_designs.pdf#page=74|aud_folien_07_advanced_designs, page 74]]

## Greedy-[[Traveling Salesperson Problem (TSP)|TSP]]

Ansatz Greedy-Algorithmus für TSP:
Starte mit beliebigem oder gegebenem Knoten. Nimm vom gegenwärtigen Knoten aus die Kante zu noch nicht besuchtem Knoten, die kleinstes Gewicht hat. Wenn kein Knoten mehr übrig, gehe zu Startpunkt zurück.

![[aud_folien_07_advanced_designs.pdf#page=77|aud_folien_07_advanced_designs, page 77]]

### Greedy-TSP Ist Zu Gierig

Man betrachte den folgenden vollständigen Graphen mit Knoten $V = \{1, 2, 3, \ldots, n\}, n \geq 3$ und folgenden Kantengewichten für eine beliebig große Konstante $N$:

![[aud_folien_07_advanced_designs.pdf#page=78|aud_folien_07_advanced_designs, page 78]]

Dann ist der optimale Pfad ein anderer als der, den der Greedy-Algorithmus findet:

![[aud_folien_07_advanced_designs.pdf#page=79|aud_folien_07_advanced_designs, page 79]]

### Effizienter Algorithmus Für TSP?

Es ist vermutlich schwierig, einen effizienten Algorithmus zu finden

