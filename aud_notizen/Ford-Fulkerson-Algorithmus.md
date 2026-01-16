---
tags:
  - foliensatz/06
  - cleaned
aliases:
  - Ford-Fulkerson
  - Ford Fulkerson
---

## Ford-Fulkerson-Methode

Idee: Suche einen Pfad von $s$ nach $t$, der bezüglich des [[Netzwerkflüsse|Flusses]] noch erweiterbar ist
Aber: den Pfad suchen wir im "Restkapazitäts"-Graph $G_f$, der die möglichen Zu- und Abflüsse beschreibt

![[aud_folien_06_graphen_algorithmen.pdf#page=183|aud_folien_06_graphen_algorithmen, page 183]]

### Reste

Die Restkapazität $c_f(u, v)$ zwischen zwei Knoten ist gegeben durch
$$c_f(u, v) = \begin{cases}
c(u, v) - f(u, v) & \text{falls $(u, v) \in E$} \\
f(v, u) & \text{falls $(v, u) \in E$} \\
0 & \text{sonst}
\end{cases}$$
Im ersten Fall gibt die Funktion an, wieviel eingehenden Fluss über $(u, v)$ man noch zu $v$ hinzufügen könnte
Im zweiten Fall gibt die Funktion an, wie viel von $v$ ausgehenden Fluss man wegnehmen könnte, um $v$ mehr Kapazität zu geben
Im dritten Fall existiert keine Verbindung zwischen den beiden Knoten

![[aud_folien_06_graphen_algorithmen.pdf#page=184|aud_folien_06_graphen_algorithmen, page 184]]

### Restkapazitäts-Graph

Bemerkung: im Restkapazitätsgraph sind antiparallele Kanten erlaubt

![[aud_folien_06_graphen_algorithmen.pdf#page=185|aud_folien_06_graphen_algorithmen, page 185]]

### Restkapazitäten Ausnutzen

![[aud_folien_06_graphen_algorithmen.pdf#page=186|aud_folien_06_graphen_algorithmen, page 186]]

Wir finden in $G_f$ einen Pfad von $s$ zu $t$ und erhöhen() für Kanten in $G$) bzw. erniedrigen (für Nicht-Kanten) um Minimum $c_f(u, v)$ aller Werte auf dem Pfad in $G$

## Ford-Fulkerson-Algorithmus

![[aud_folien_06_graphen_algorithmen.pdf#page=187|aud_folien_06_graphen_algorithmen, page 187]]

### Erklärung

Z1: Setze den `flow` überall auf 0
Z2: Solange es im Restkapazitätsgraphen $G_f$ einen [[Netzwerkflüsse|Flusspfad]] von $s$ zu $t$ gibt 
	Z3: Finde die kleinste Restkapazität auf dem Pfad
	Z4:Für jede Kante auf dem Pfad in $G_f$:
		Z5/6: Falls die Kante im Flussgraphen ist, füge den Fluss hinzu
		Z7/8: Sonst nehme den Fluss weg

## Beispiel

Am Anfang bekommt jede Kante einen Fluss von 0. Dann finden wir einen Pfad im Restkapazitätengraph und erhöhen an diesem Pfad den Fluss um das höchst mögliche, in diesem Fall also 4:

![[aud_folien_06_graphen_algorithmen.pdf#page=188|aud_folien_06_graphen_algorithmen, page 188]]

Dann finden wir den nächsten Pfad:

![[aud_folien_06_graphen_algorithmen.pdf#page=189|aud_folien_06_graphen_algorithmen, page 189]]

Einen letzten Pfad finden wir noch:

![[aud_folien_06_graphen_algorithmen.pdf#page=190|aud_folien_06_graphen_algorithmen, page 190]]

Dann gibt es keine Pfade mehr, und der Algorithmus terminiert

![[aud_folien_06_graphen_algorithmen.pdf#page=191|aud_folien_06_graphen_algorithmen, page 191]]

## Korrektheit

Die Korrektheit lässt sich mithilfe des Max-Flow Min-Cut Theorems beweisen:

![[aud_folien_06_graphen_algorithmen.pdf#page=192|aud_folien_06_graphen_algorithmen, page 192]]

![[aud_folien_06_graphen_algorithmen.pdf#page=193|aud_folien_06_graphen_algorithmen, page 193]]

Trennen wir unseren Graphen also in zwei Teile $S$ und $V-S$, so ist die "Kapazität" dieses Schnittes die summierte Kapazität aller Kanten, die von $S$ in $V-S$ führen.
Punkt 3 sagt aus, dass wen der von der Quelle ausgehende [[Netzwerkflüsse|Fluss]] $|f|$ der Kapazität des Schnittes mit der geringsten Kapazität entspricht, $f$ ein [[Maximaler Fluss in Graphen|maximaler Fluss]] für $G$ ist

## Ford-Fulkerson Für Ungerichtete Graphen

Bei ungerichteten Graphen können wir ungerichtete Kanten in zwei gerichtete verwandeln
Und dann alle antiparallele Kanten durch Einführung neuer Knoten entfernen

![[aud_folien_06_graphen_algorithmen.pdf#page=196|aud_folien_06_graphen_algorithmen, page 196]]