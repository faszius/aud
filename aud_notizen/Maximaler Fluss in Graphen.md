---
tags:
  - foliensatz/06
  - cleaned
aliases:
  - Maximaler Fluss
  - Maximale Flüsse
  - Maximalen Fluss
---

## Maximale Flüsse

Der Wert $|f|$ eines Flusses $f: V \times V \rightarrow \mathbb{R}$ für ein Flussnetzwerk $G = (V, E)$ mit Kapazität $c$ und Quelle $s$ und Senke $t$ ist
$|f| = \sum_{v \in V} f(s, v) - \sum_{v \in V} f(v, s)$,
also die Summe aller Flüsse, die die Quelle verlassen, minus die Summe aller Flüsse, die in die Quelle fließen

In dem Beispiel ist $|f| = 6$, der Fluss ist aber nicht maximal, da man z.B. über die oberen Kanten jeweils noch einen "Fluss" hinzufügen könnte

![[aud_folien_06_graphen_algorithmen.pdf#page=181|aud_folien_06_graphen_algorithmen, page 181]]

## Transformationen

Wir müssen antiparallele Kanten eliminieren
Und alle Quellen und Senken vereinen

![[aud_folien_06_graphen_algorithmen.pdf#page=182|aud_folien_06_graphen_algorithmen, page 182]]