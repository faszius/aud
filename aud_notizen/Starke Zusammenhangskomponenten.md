---
tags:
  - foliensatz/06
  - cleaned
aliases:
  - SCC
  - Strongly Connected Component
  - Starke Zusammenhangskomponente
Related:
  - "[[Depth-First Search (DFS)]]"
---
Eine starke Zusammenhangskomponente eines gerichteten Graphen $G = (V, E)$ ist eine Knotenmenge $C \subseteq V$, sodass 
1. es zwischen je zwei Knoten $u, v \in C$ einen Pfad von $u$ nach $v$ gibt, und
2. es keine Menge $D \subseteq V$ mit $C \subset D$ gibt, für die 1. auch gilt (C ist maximal)

![[aud_folien_06_graphen_algorithmen.pdf#page=68|aud_folien_06_graphen_algorithmen, page 68]]

Ein Graph kann mehrere starke Zusammenhangskomponenten haben

## Eigenschaften

Verschiedene SCCs $C$, $D$ sind disjunkt, sonst gäbe es $v \in C \cap D$ und für beliebige $u \in C$ und $w \in D$ auch einen Pfad von $u$ nach $w$ über $v$ (und umgekehrt), somit wären $C$ und $D$ identisch

Wenn es für verschiedene SCCs $C$, $D$ mit $u, v \in C$ und $w, x \in D$ einen Pfad $u \rightarrow w$ gibt, dann kann es keinen Pfad $x \rightarrow v$ geben, sonst wären $C$ und $D$ identisch

![[aud_folien_06_graphen_algorithmen.pdf#page=69|aud_folien_06_graphen_algorithmen, page 69]]

## Algorithmus: Ansatz

Lasse zweimal [[Depth-First Search (DFS)|DFS]] laufen:
- einmal auf Graph $G$
- einmal auf transponiertem Graphen $G^T = (V, E^T)$: $E^T = \{(v, u) | (u, v) \in E\}$ (drehe Kanten in G um)

![[aud_folien_06_graphen_algorithmen.pdf#page=70|aud_folien_06_graphen_algorithmen, page 70]]

## SCCs Im Transponierten Graphen

SCCs in $G$ und $G^T$ bleiben identisch
(in beiden Fällen gibt es in jeder SCC einen Weg von jedem Knoten zum anderen Knoten)
nur Übergänge zwischen SCCs drehen sich um

![[aud_folien_06_graphen_algorithmen.pdf#page=71|aud_folien_06_graphen_algorithmen, page 71]]

## Algorithmus

![[aud_folien_06_graphen_algorithmen.pdf#page=72|aud_folien_06_graphen_algorithmen, page 72]]

### Erklärung

Zuerst führen wir normale [[Depth-First Search (DFS)|Tiefensuche]] aus.
Dann transponieren wir den [[Graphen]], bedeutet, wir drehen einmal alle Pfeile um.
Dann führen wir nochmal Tiefensuche aus. Dieses Mal arbeiten wir die Knoten aber nach ihrer Abschlusszeit ab - angefangen mit dem Knoten, der beim ersten Durchlauf der Tiefensuche die *höchste* Abschlusszeit hatte.
Bei jedem Aufruf von der Tiefensuche auf einen Knoten merken wir uns alle Knoten, die wir bei diesem Aufruf besuchen. Sobald wir zu keinem weiteren Knoten mehr gehen können, und zu einem neuen Knoten springen müssen, speichern wir uns die bisher besuchten Knoten als eine starke Zusammenhangskomponente.

## Beispiel

Das sind die Ergebnisse der Tiefensuche auf dem normalen Graphen:
An jedem Knoten steht die Abschlusszeit.

![[aud_folien_06_graphen_algorithmen.pdf#page=77|aud_folien_06_graphen_algorithmen, page 77]]

Nun führen wir die Tiefensuche am transponierten Graphen aus. 
Wir beginnen mit dem Knoten `1`, da er die höchste Abschlusszeit hat. Von der `1` springen wir zur `5`, dann zur `4` (weil die `4` eine höhere Abschlusszeit hat als die `2`), danach zurück zur `5` und von da aus zur `2`. Danach gehen wir zurück zur `5` und zur `1` und stellen fest, dass wir keine weiteren Knoten mehr erreichen können. Wir wissen also, dass die `1`, `2`, `4` und `5` eine starke Zusammenhangskomponente bilden.
Der Algorithmus macht also beim Knoten `9` weiter, da der die nächsthöhere Abschlusszeit der unbesuchten Knoten hat. Von da aus können wir zur `7` und zur `8` und haben dann alle Knoten erreicht. Jetzt wissen wir, dass die `7`, `8` und `9` eine starke Zusammenhangskomponente bilden.
Als letztes besuchen wir die `3` und entdecken von da die `6`, sodass wir jetzt wissen, dass die `3` und `6` eine starke Zusammenhangskomponente bilden.
Es bleiben keine unentdeckten Knoten mehr übrig, und so haben wir alle starken Zusammenhangskomponenten entdeckt.

![[aud_folien_06_graphen_algorithmen.pdf#page=78|aud_folien_06_graphen_algorithmen, page 78]]