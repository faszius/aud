---
tags:
  - foliensatz/06
  - cleaned
---

## (Endliche) Gerichtete Graphen

Ein (endlicher) gerichteter Graph $G = (V, E)$ besteht aus
1. einer (endlichen) Knotenmenge $V$ ("vertices")
2. einer (endlichen) Kantenmenge $E \subseteq V \times V$ ("edges")

$(u, v) \in E$ ist eine Kante von Knoten $u$ zu $v$

In gerichteten Graphen spielt die Richtung der Kante eine Rolle - wenn 1 eine Kante zu 5 hat, hat 5 nicht unbedingt eine Kante zu 1

(Im Unterschied zu [[Bäume|Bäumen]] ist die Anordnung der Knoten in der Darstellung irrelevant)

![[aud_folien_06_graphen_algorithmen.pdf#page=3|aud_folien_06_graphen_algorithmen, page 3]]

## Ungerichtete Graphen

Ein (endlicher) _un_ gerichteter Graph $G = (V, E)$ besteht aus
1. einer (endlichen) Knotenmenge $V$ ("vertices")
2. einer (endlichen) Kantenmenge $E \subseteq V \times V$ ("edges") sodass $(u, v) \in E \Leftrightarrow (v, u) \in E$

In ungerichteten Graphen unterscheidet man also nicht mehr zwischen der Richtung der Kante - wenn eine Kante von 1 zu 5 führt, führt die Kante auch von 5 zu 1

![[aud_folien_06_graphen_algorithmen.pdf#page=4|aud_folien_06_graphen_algorithmen, page 4]]

## Pfade

Knoten $v$ ist von Knoten $u$ im Graphen $G = (V, E)$ erreichbar, wenn es einen Pfad $(w_1, \ldots, w_k) \in V^k$ gibt, sodass $(w_i, w_{i+1}) \in E$ für $i = 1, 2, \ldots, k-1$ und $w_1 = u$ und $w_k = v$

Insbesondere ist $u$ immer von $u$ per "leerem Pfad" ($k=1$) erreichbar.

Länge des Pfades = $k-1$ = Anzahl Kanten

$(w_1, \ldots, w_k)$ ist ein kürzester Pfad von $u$ nach $v$, wenn es keinen kürzeren Pfad gibt.

$\text{shortest}(u, v)$ = Länge eines kürzesten Pfades von $u$ nach $v$

## Zusammenhänge

Ein ungerichteter Graph ist zusammenhängend, wenn jeder Knoten von jedem anderen Knoten aus erreichbar ist

Ein gerichteter Graph ist stark zusammenhängend, wenn jeder Knoten von jedem anderen Knoten aus (gemäß Kantenrichtung) erreichbar ist

![[aud_folien_06_graphen_algorithmen.pdf#page=6|aud_folien_06_graphen_algorithmen, page 6]]

## Graphen Und [[Bäume]]

Ein Graph $G = (V, E)$ ist ein Baum, wenn $V$ leer ist oder es einen Knoten $r \in V$ ("Wurzel") gibt, sodass jeder Knoten $v$ von der Wurzel aus per eindeutigem Pfad erreichbar ist

![[aud_folien_06_graphen_algorithmen.pdf#page=7|aud_folien_06_graphen_algorithmen, page 7]]

## Subgraphen

Ein (gerichteter oder ungerichteter) Graph $G' = (V', E')$ ist ein Subgraph (oder Untergraph oder Teilgraph) des (gerichteten oder ungerichteten) Graphen $G = (V, E)$, wenn $V' \subseteq V$ und $E' \subseteq E$

## Darstellung Von Graphen

### Als Adjazenzmatrix

$A[i, j] = \begin{cases*} 1 \text{ wenn Kante von } i \text{ zu } j \\ 0 \text{ wenn keine Kante } \end{cases*}$
(Zeile $i$, Spalte $j$)

Bei ungerichteten Graphen ist die Matrix (spiegel-)symmetrisch zur Hauptdiagonalen

Speicherbedarf = $\Theta(|V|^2)$

![[aud_folien_06_graphen_algorithmen.pdf#page=9|aud_folien_06_graphen_algorithmen, page 9]]

#### Matrix $\rightarrow$ Eigenschaft

Der Eintrag $a_{i, j}^{(m)}$ in der $i$-ten Zeile und $j$-ten Spalte der $m$-ten Potenz $A^m$ der Adjazenzmatrix $A$ eines Graphen gibt die Anzahl der Wege an, die von Knoten $i$ zu Knoten $j$ entlang von genau $m$ Kanten führen

Beweis per Induktion (Basisfall $m=0$):

![[aud_folien_06_graphen_algorithmen.pdf#page=10|aud_folien_06_graphen_algorithmen, page 10]]

Schritt $m \rightarrow m+1$:

![[aud_folien_06_graphen_algorithmen.pdf#page=11|aud_folien_06_graphen_algorithmen, page 11]]

![[aud_folien_06_graphen_algorithmen.pdf#page=12|aud_folien_06_graphen_algorithmen, page 12]]

![[aud_folien_06_graphen_algorithmen.pdf#page=13|aud_folien_06_graphen_algorithmen, page 13]]

### Als Adjazenzliste

Als Array mit verketteten Listen (sortiert oder unsortiert)

Speicherbedarf $\Theta(|V| + |E|)$

![[aud_folien_06_graphen_algorithmen.pdf#page=14|aud_folien_06_graphen_algorithmen, page 14]]

## Gewichtete Graphen

Ein gewichteter gerichteter Graph besitzt zusätzlich Funktion $w: E \rightarrow \mathbb{R}$
Bei gewichteten ungerichteten Graphen gilt zusätzlich $w((u, v)) = w((v, u))$ für alle $(u, v) \in E$

Wir speichern also zusätzlich zur Kante $(u, v)$ auch den Wert $w((u, v))$

Zum Beispiel könnte man die Knoten als Städte betrachten und die Kanten als Verbindungen zwischen den Städten, dann könnte das Gewicht eine Aussage über die Entfernung der Knoten treffen