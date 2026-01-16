---
tags:
  - foliensatz/06
  - cleaned
aliases:
  - Prim
---

## Algorithmus Von Prim

Idee: der Algorithmus fügt, beginnend mit dem Wurzelknoten $r$, immer die leichte Kante zur zusammenhängenden Menge hinzu (die Wahl der Wurzelknotens ist beliebig!)

![[aud_folien_06_graphen_algorithmen.pdf#page=107|aud_folien_06_graphen_algorithmen, page 107]]

## Zeilenweise Erklärung

Z1: Für jeden Knoten setzen wir den Schlüssel auf $\infty$ und den Vorgänger auf `NIL`
Z2: Setze den Schlüssel des Wurzelknotens auf $-\infty$ und packe alle Knoten in eine Menge `Q`
Z3: Solange `Q` nicht leer ist
	Z4: Setze `u` auf den Knoten in `Q` mit dem kleinsten Wert
	Z5: Für jeden zu `u` adjazenten Knoten `v`
		Z6: Falls `v` noch in `Q` ist und das Gewicht der  Kante von `u` nach `v` kleiner ist als der Schlüssel von `v`
			Z7: Setze den Schlüssel von `v` auf das Gewicht der Kante von `u` nach `v`
			Z8: Setze den Vorgänger von `v` auf `u`

## Beispiel

Am Anfang werden alle Knoten mit einem Schlüssel $\infty$ und einem Vorgänger `NIL` initialisiert. Der Knoten, auf dem der Algorithmus aufgerufen wird (in diesem Fall Knoten $6$) bekommt den Schlüssel $-\infty$. Alle Knoten sind in `Q`

![[aud_folien_06_graphen_algorithmen.pdf#page=108|aud_folien_06_graphen_algorithmen, page 108]]

Als erstes fangen wir bei Knoten $6$ an, da er den kleinsten Schlüssel hat. Jeder benachbarte Knoten bekommt den Vorgänger $6$ und als Schlüssel den Wert der Kante zwischen ihm und dem Knoten $6$.

![[aud_folien_06_graphen_algorithmen.pdf#page=109|aud_folien_06_graphen_algorithmen, page 109]]

Da Knoten $5$ jetzt der Knoten in `Q` ist, der den kleinsten Wert hat, machen wir mit ihm weiter. Der minimale Spannbaum umfasst jetzt Knoten $6$ und $5$. Er hat nur einen Nachbarn $4$, dessen Werte jetzt aktualisiert werden.

![[aud_folien_06_graphen_algorithmen.pdf#page=110|aud_folien_06_graphen_algorithmen, page 110]]

Als nächstes Knoten $4$, der die Werte vom Nachbarn $3$ aktualisiert.

![[aud_folien_06_graphen_algorithmen.pdf#page=111|aud_folien_06_graphen_algorithmen, page 111]]

Dann gucken wir uns die $3$ an. Die $3$ hat als Nachbarn den Knoten $7$. Die $7$ hat zwar schon von $6$ einen Schlüssel und einen Vorgänger bekommen, jedoch ist das Gewicht der Kante von $3$ zu $7$ kleiner als der Schlüssel von $7$. Also wird der Schlüssel von $7$ aktualisiert und auf das Gewicht der Kante gesetzt, also auf 9. Zudem wird der Vorgänger auf Knoten $3$ gesetzt.

![[aud_folien_06_graphen_algorithmen.pdf#page=112|aud_folien_06_graphen_algorithmen, page 112]]

Genau so verfahren wir mit Knoten $2$.

![[aud_folien_06_graphen_algorithmen.pdf#page=113|aud_folien_06_graphen_algorithmen, page 113]]

Und ebenso mit Knoten $1$.

![[aud_folien_06_graphen_algorithmen.pdf#page=114|aud_folien_06_graphen_algorithmen, page 114]]

Zu guter letzt wird noch Knoten $7$ in den minimalen Spannbaum aufgenommen. Dann ist `Q` leer, und der Algorithmus ist leer.

![[aud_folien_06_graphen_algorithmen.pdf#page=115|aud_folien_06_graphen_algorithmen, page 115]]

## Korrektheit

Die Kanten in $A$ laufen nur zwischen den bereits aufgesammelten Knoten in $V-Q$
Folglich respektiert der Schnitt $(Q, V-Q)$ die Menge $A$
Alle Knoten $v \in Q$ enthalten als Wert `v.key` immer das kleinste Kantengewicht zu einem bereits aufgesammelten Knoten `v.pred` in $V-Q$
Daher beschreibt der in Schritt $4$ ausgewählte Knoten `u` eine überbrückende, leichte Kante (`u`, `u.pred`)

## Laufzeit

Mit vielen Optimierungen: $\mathcal{O}(\vert E \vert + \vert V \vert \cdot \log \vert V \vert)$

![[aud_folien_06_graphen_algorithmen.pdf#page=117|aud_folien_06_graphen_algorithmen, page 117]]