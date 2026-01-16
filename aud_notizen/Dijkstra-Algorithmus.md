---
tags:
  - foliensatz/06
  - cleaned
aliases:
  - Dijkstra
---

## Dijkstra-Algorithmus

Voraussetzung: Alle Kanten haben ein Gewicht $\geq 0$

![[aud_folien_06_graphen_algorithmen.pdf#page=151|aud_folien_06_graphen_algorithmen, page 151]]

### Erklärung

Z1: Setze die Entfernung jedes Knotens auf $\infty$ und den Vorgänger auf `NIL`, setze die Entfernung des Anfangsknotens auf 0
Z2: Speichere alle Knoten in der Menge `Q`
Z3: Solange in `Q` noch Knoten sind (es also noch unbearbeitete Knoten gibt):
	Z4: Extrahiere den Knoten mit der kleinsten Distanz aus `Q` 
	Z5: Für jeden benachbarten Knoten
		Z6: Aktualisiere die Entfernung

## Beispiel

Am Anfang bekommt der Wurzelknoten die Entfernung 0, alle anderen Knoten die Entfernung $\infty$ und jeder Knoten bekommt den Vorgänger `NIL`

![[aud_folien_06_graphen_algorithmen.pdf#page=152|aud_folien_06_graphen_algorithmen, page 152]]

In der ersten Iteration der `FOR`-Schleife wird der Knoten mit der kleinsten Entfernung (also die Wurzel $1$) aus `Q` extrahiert und die Entfernung aller Nachbarn aktualisiert:

![[aud_folien_06_graphen_algorithmen.pdf#page=153|aud_folien_06_graphen_algorithmen, page 153]]

Der Knoten $6$ hat jetzt die kleinste Entfernung. Die Entfernung dessen Nachbarn wird als nächstes aktualisiert. Da dabei ein kürzerer Pfad zur $2$ entdeckt wird, bekommt diese auch eine neue Entfernung und Vorgänger:

![[aud_folien_06_graphen_algorithmen.pdf#page=154|aud_folien_06_graphen_algorithmen, page 154]]

Da die $2$ jetzt die kürzeste Entfernung hat, ist sie als nächstes dran:

![[aud_folien_06_graphen_algorithmen.pdf#page=155|aud_folien_06_graphen_algorithmen, page 155]]

Dann hat die $3$ die kleinste Entfernung:

![[aud_folien_06_graphen_algorithmen.pdf#page=156|aud_folien_06_graphen_algorithmen, page 156]]

Und danach die $5$

![[aud_folien_06_graphen_algorithmen.pdf#page=157|aud_folien_06_graphen_algorithmen, page 157]]

Und zu guter Letzt bleibt nur noch $4$ in der Menge `Q`:

![[aud_folien_06_graphen_algorithmen.pdf#page=158|aud_folien_06_graphen_algorithmen, page 158]]

Da jeder Knoten jetzt einen Vorgänger hat, können wir ohne Probleme den kürzesten Pfad zu jedem Knoten bestimmen, indem wir einfach bis zur Wurzel dem Zeiger zum Vorgänger folgen:

![[aud_folien_06_graphen_algorithmen.pdf#page=159|aud_folien_06_graphen_algorithmen, page 159]]

## Korrektheit

![[aud_folien_06_graphen_algorithmen.pdf#page=160|aud_folien_06_graphen_algorithmen, page 160]]

![[aud_folien_06_graphen_algorithmen.pdf#page=161|aud_folien_06_graphen_algorithmen, page 161]]

![[aud_folien_06_graphen_algorithmen.pdf#page=162|aud_folien_06_graphen_algorithmen, page 162]]

![[aud_folien_06_graphen_algorithmen.pdf#page=163|aud_folien_06_graphen_algorithmen, page 163]]

![[aud_folien_06_graphen_algorithmen.pdf#page=164|aud_folien_06_graphen_algorithmen, page 164]]

## Dijkstra-Algorithmus Und Negative Kantengewichte

Der Algorithmus funktioniert nicht mit negativen Kantengewichten:

![[aud_folien_06_graphen_algorithmen.pdf#page=165|aud_folien_06_graphen_algorithmen, page 165]]

Um zu verstehen warum, schauen wir uns einmal an wie der Algorithmus mit negativen Kanten umgeht:

![[aud_folien_06_graphen_algorithmen.pdf#page=166|aud_folien_06_graphen_algorithmen, page 166]]

![[aud_folien_06_graphen_algorithmen.pdf#page=167|aud_folien_06_graphen_algorithmen, page 167]]

![[aud_folien_06_graphen_algorithmen.pdf#page=168|aud_folien_06_graphen_algorithmen, page 168]]

![[aud_folien_06_graphen_algorithmen.pdf#page=169|aud_folien_06_graphen_algorithmen, page 169]]

![[aud_folien_06_graphen_algorithmen.pdf#page=170|aud_folien_06_graphen_algorithmen, page 170]]

Da der Algorithmus immer als nächstes den Knoten abschließt, der momentan die geringste Entfernung hat, und ihn danach nicht mehr aktualisiert, wird die Entfernung der $5$ nicht mehr aktualisiert, nachdem durch die negative Kante ein kürzerer Pfad gefunden wird

![[aud_folien_06_graphen_algorithmen.pdf#page=171|aud_folien_06_graphen_algorithmen, page 171]]

## Kantengewichte Nicht-negativ Machen

Versuch: addiere absoluten Wert der kleinsten Kante zu allen Kanten
Problem: man addiert den Wert so oft, wie die Anzahl Kanten auf dem kürzesten Weg

![[aud_folien_06_graphen_algorithmen.pdf#page=172|aud_folien_06_graphen_algorithmen, page 172]]

