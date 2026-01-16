---
tags:
  - foliensatz/06
  - cleaned
aliases:
  - Bellman Ford
  - Bellman-Ford Algorithmus
  - Bellman-Ford
---

## Bellman-Ford-Algorithmus

![[aud_folien_06_graphen_algorithmen.pdf#page=130|aud_folien_06_graphen_algorithmen, page 130]]

## Zeilenweise Erklärung

Z1: Setze die Entfernung jedes Knoten auf unendlich und den Vorgänger jedes Knoten auf `NIL`, setze die Entfernung des Anfangsknotens auf 0
Z2: Schlimmster Fall: alle Knoten befinden sich in einer Linie vom Startknoten ausgehend aneinandergereiht, sodass der der Endknoten die maximale Entfernung vom Startknoten hat. Also für jede Kante des theoretisch längsten Pfades:
	Z3/4: führe `relax` auf jede Kante des Graphen aus (in lexographischer Ordung, also 1->2 vor z.B. 3->1)
Z5-7: Prüfe ob negative Zyklen erreichbar sind, und gebe in dem Fall `false` wieder
Z8: Gebe `true` wieder

Genau dann, wenn es keinen Pfad von `s` zu einem Knoten `u` gibt, dann bleibt `u.dist` = $\infty$
Am Ende steht in jedem Knoten `u.dist` = $\text{shortest}(s, u)$ und `u.pred` zeigt auf Vorgängerknoten in kürzestem Pfad

## Idee/Korrektheit

![[aud_folien_06_graphen_algorithmen.pdf#page=131|aud_folien_06_graphen_algorithmen, page 131]]

![[aud_folien_06_graphen_algorithmen.pdf#page=132|aud_folien_06_graphen_algorithmen, page 132]]

![[aud_folien_06_graphen_algorithmen.pdf#page=133|aud_folien_06_graphen_algorithmen, page 133]]

![[aud_folien_06_graphen_algorithmen.pdf#page=134|aud_folien_06_graphen_algorithmen, page 134]]

![[aud_folien_06_graphen_algorithmen.pdf#page=134|aud_folien_06_graphen_algorithmen, page 134]]

![[aud_folien_06_graphen_algorithmen.pdf#page=136|aud_folien_06_graphen_algorithmen, page 136]]

## Beispiel

Am Anfang werden alle Knoten mit einer Entfernung $\infty$ und einem Vorgänger `NIL` initialisiert, außer dem Startknoten $1$, der die Entfernung $0$ bekommt.

![[aud_folien_06_graphen_algorithmen.pdf#page=137|aud_folien_06_graphen_algorithmen, page 137]]

Im ersten Durchlauf gehen wir alle Kanten in lexographischer Ordnung durch - d.h. erst alle Kanten, die von $1$ ausgehen, dann alle Kanten, die von $2$ ausgehen usw. und rufen `relax` auf. 
Der `relax`-Aufruf bei $(3, 1)$ und $(5, 4)$ bewirkt dabei keine Änderung, da z.B. die $5$ mit ihrer Entfernung von $\infty$ keinen kürzeren Pfad bieten kann.

![[aud_folien_06_graphen_algorithmen.pdf#page=138|aud_folien_06_graphen_algorithmen, page 138]]

![[aud_folien_06_graphen_algorithmen.pdf#page=139|aud_folien_06_graphen_algorithmen, page 139]]

Im zweiten Durchlauf wird nochmal `relax` auf alle Kanten aufgerufen, wobei jetzt die meisten `relax`-Aufrufe keine Änderung herbeibringen.

![[aud_folien_06_graphen_algorithmen.pdf#page=140|aud_folien_06_graphen_algorithmen, page 140]]

Die `FOR`-Schleife wird noch ein paar Mal durchgelaufen, wobei sich nichts mehr ändert. Am Ende gibt der Algorithmus `true` zurück. Jetzt können wir anhand der Vorgängerwerte den kürzesten Pfad zu jedem Knoten bestimmen.

![[aud_folien_06_graphen_algorithmen.pdf#page=141|aud_folien_06_graphen_algorithmen, page 141]]