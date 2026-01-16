---
tags:
  - foliensatz/06
  - cleaned
  - "#MoC"
Related:
  - "[[Single-Source Shortest Path (SSSP)]]"
  - "[[Bellman-Ford-Algorithmus]]"
  - "[[SSSP-Algorithmus für Dags]]"
  - "[[Dijkstra-Algorithmus]]"
  - "[[A-Star-Algorithmus]]"
---

## Negative Zyklen

![[aud_folien_06_graphen_algorithmen.pdf#page=125|aud_folien_06_graphen_algorithmen, page 125]]

Wir müssen aufpassen, dass unser Graph keine Zyklen mit einer negativen Gesamtlänge enthält, da ein wiederholtes Durchlaufen des Zyklus' dann eine beliebig kleine Gesamtlänge ergeben würde

Negative Kantengewichte sind erlaubt, aber keine (erreichbaren) Zyklen mit negativem Gesamtgewicht!

## Positive Zyklen

![[aud_folien_06_graphen_algorithmen.pdf#page=126|aud_folien_06_graphen_algorithmen, page 126]]

Kürzeste Pfade können keine Zyklen mit positivem Gesamtgewicht enthalten, da wir sonst ohne den Zyklus einen kürzeren Pfad erhalten würden

Kürzeste Pfade enthalten also höchstens (eliminierbare) Zyklen mit Gewicht 0
Es gibt stets einen kürzesten Pfad mit Kantenlänge $\leq \vert V \vert - 1$

## Kürzeste Teilpfade

![[aud_folien_06_graphen_algorithmen.pdf#page=127|aud_folien_06_graphen_algorithmen, page 127]]

Haben wir einen kürzesten Pfad von $s$ nach $z$ durch Knoten $x$, dann ist der Teilpfad $s \rightarrow x$ eines kürzesten Pfades $s \rightarrow x \rightarrow z$ auch stets der kürzeste Pfad von $s$ nach $x$, sonst gäbe es einen kürzeren Pfad von $s$ nach $z$

## Algorithmen Für [[Single-Source Shortest Path (SSSP)|SSSP]]

![[aud_folien_06_graphen_algorithmen.pdf#page=128|aud_folien_06_graphen_algorithmen, page 128]]

## Relax

Idee: verringere aktuelle Distanz von Knoten $v$, wenn durch Kante $(u, v)$ eine kürzere Distanz erreichbar ist:

![[aud_folien_06_graphen_algorithmen.pdf#page=129|aud_folien_06_graphen_algorithmen, page 129]]

