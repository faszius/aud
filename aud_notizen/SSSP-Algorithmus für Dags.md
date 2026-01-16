---
tags:
  - foliensatz/06
  - cleaned
Related:
  - "[[Topologisches Sortieren]]"
aliases:
  - SSSP für Dag
  - SSSP für Dags
---

## SSSP Mittels Topologischer Sortierung

Aus einem Dag mit Gewichten können eir mithilfe topologischer Sortierung den kürzesten Pfad finden

![[aud_folien_06_graphen_algorithmen.pdf#page=142|aud_folien_06_graphen_algorithmen, page 142]]

## SSSP-Algorithmus Für Dags

![[aud_folien_06_graphen_algorithmen.pdf#page=143|aud_folien_06_graphen_algorithmen, page 143]]

### Erklärung

Z1: Zuerst geben wir jedem Knoten den Vorgänger `NIL` und die Entfernung $\infty$, bis auf den Wurzelknoten, der die Entfernung 0 bekommt.
Z2: Dann sortieren wir den Graphen topologisch
Z3: Dann gehen wir alle Knoten einmal in topologischer Reihenfolge durch
	Z4: Und für jeden Knoten gehen wir einmal alle Nachbarn durch
		Z5: Und führen `relax` aus

Der Algorithmus ist sehr ähnlich zu [[Bellman-Ford-Algorithmus|Bellman-Ford]], nur dass wir hier unseren Graphen vorher topologisch sortieren und die Kanten nur ein Mal durchgehen müssen (anstelle von $|V|-1$ Mal)

## Beispiel

Am Anfang bekommt jeder Knoten den Vorgänger `NIL` und die Entfernung $\infty$, bis auf den Wurzelknoten, der die Entfernung 0 bekommt. Dann sortieren wir den Graphen topologisch.

![[aud_folien_06_graphen_algorithmen.pdf#page=144|aud_folien_06_graphen_algorithmen, page 144]]

Dann fangen wir beim ersten Knoten an und führen `relax` auf jede Verbindung zu Nachbarn aus.

![[aud_folien_06_graphen_algorithmen.pdf#page=145|aud_folien_06_graphen_algorithmen, page 145]]

Das gleiche machen wir dann mit dem zweiten Knoten

![[aud_folien_06_graphen_algorithmen.pdf#page=146|aud_folien_06_graphen_algorithmen, page 146]]

Und gehen so von links nach rechts (der topologischen Sortierung entsprechend) alle Knoten durch und aktualisieren die Entfernungen der Nachbarn

![[aud_folien_06_graphen_algorithmen.pdf#page=147|aud_folien_06_graphen_algorithmen, page 147]]

![[aud_folien_06_graphen_algorithmen.pdf#page=148|aud_folien_06_graphen_algorithmen, page 148]]

## Korrektheit + Laufzeit

Korrektheit, da die Kanten auf dem kürzesten Pfad nacheinander "gelockert" werden (vgl. [[Bellman-Ford-Algorithmus|Bellman-Ford]])

Laufzeit von $\Theta(\vert E \vert + \vert V \vert)$

![[aud_folien_06_graphen_algorithmen.pdf#page=149|aud_folien_06_graphen_algorithmen, page 149]]