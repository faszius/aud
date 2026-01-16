---
tags:
  - foliensatz/06
  - cleaned
aliases:
  - Kruskal
---

## Algorithmus Von Kruskal

![[aud_folien_06_graphen_algorithmen.pdf#page=92|aud_folien_06_graphen_algorithmen, page 92]]

## Zeilenweise Erklärung

Z1: Erzeuge einen neuen, leeren minimalen Spannbaum $A$
Z2: Für jeden Knoten speichern wir, dass er durch $A$ nur mit sich selbst verbunden ist ($\text{set}(v)$ ist die Menge der Knoten, mit denen $v$ durch $A$ verbunden ist)
Z3: Sortiere die Kanten nach Gewicht in aufsteigender Reihenfolge
Z4: Für jede Kante (vom kleinsten bis zum größten Gewicht)
	Z5: Vergleiche $\text{set}$ von beiden Knoten. Sind $\text{set}(u)$ und $\text{set}(v)$ gleich, sind beide Knoten schon im MST $A$ enthalten, und der Durchlauf wird übersprungen. Ansonsten:
		Z6: Füge die Kante zum MST $A$ hinzu
		Z7: Aktualisiere $\text{set}$ beider Teilbäume
Z8: Gebe den minimalen Spannbaum $A$ wieder

## Korrektheit

Jede ausgewählt Kante $\{u, v\}$ mit $\text{set}(u) \neq \text{set}(v)$ ist leicht für Schnitt $(\text{set}(u), V - \text{set(u)})$.
Der Schnitt respektiert $A$.
Somit ist die Kante auch sicher für $A$

## Beispiel

Bei der Initialisierung setzen wir den $\text{set}$-Wert für alle Knoten (steht neben dem jeweiligen Knoten)

![[aud_folien_06_graphen_algorithmen.pdf#page=94|aud_folien_06_graphen_algorithmen, page 94]]

Wir fangen bei der Kante mit dem kleinsten Gewicht an, also bei $-2$. $\text{set}(6)$ und $\text{set}(5)$ sind verschieden, sodass die Kante in den minimalen Spannbaum aufgenommen wird. Da Knoten $6$ durch den minimalen Spannbaum jetzt auch noch mit der $5$ verbunden wird, setzen wir $\text{set}(6) = \{5, 6\}$ (mit Knoten $5$ gehen wir analog vor).

![[aud_folien_06_graphen_algorithmen.pdf#page=95|aud_folien_06_graphen_algorithmen, page 95]]

Als nächstes kommt die Kante mit Gewicht $-1$

![[aud_folien_06_graphen_algorithmen.pdf#page=96|aud_folien_06_graphen_algorithmen, page 96]]

Und danach die Kante mit Gewicht $0$. Da sie die $4$ mit $5$ und $6$ verbindet, wird $\text{set}$ aller drei Knoten erweitert.

![[aud_folien_06_graphen_algorithmen.pdf#page=97|aud_folien_06_graphen_algorithmen, page 97]]

Ähnliches passiert mit der Kante mit Gewicht $4$

![[aud_folien_06_graphen_algorithmen.pdf#page=98|aud_folien_06_graphen_algorithmen, page 98]]

Und die Kante mit Gewicht $5$ führt die beiden Teilbäume dann zusammen

![[aud_folien_06_graphen_algorithmen.pdf#page=99|aud_folien_06_graphen_algorithmen, page 99]]

Jetzt schauen wir uns die Kante mit Gewicht $7$ an. $\text{set}(2)$ und $\text{set}(6)$ sind gleich, da Knoten $2$ und $6$ durch den minimalen Spannbaum mit den gleichen Knoten verbunden sind. Die Kante mit Gewicht $7$ würde also nur einen Kreis erzeugen, was der Definition eines minimalen Spannbaums widerspricht. Also wird die Kante nicht aufgenommen.

![[aud_folien_06_graphen_algorithmen.pdf#page=100|aud_folien_06_graphen_algorithmen, page 100]]

Gleiches mit der Kante mit Gewicht $8$.

![[aud_folien_06_graphen_algorithmen.pdf#page=101|aud_folien_06_graphen_algorithmen, page 101]]

Die Kante mit Gewicht $9$ wird hingegen noch aufgenommen.

![[aud_folien_06_graphen_algorithmen.pdf#page=102|aud_folien_06_graphen_algorithmen, page 102]]

Obwohl jetzt alle Knoten im minimalen Spannbaum sind, geht der Algorithmus trotzdem alle verbleibenden Kanten durch.

![[aud_folien_06_graphen_algorithmen.pdf#page=103|aud_folien_06_graphen_algorithmen, page 103]]

Zum Schluss sind alle Knoten verbunden, und wir haben unseren minimalen Spannbaum

![[aud_folien_06_graphen_algorithmen.pdf#page=104|aud_folien_06_graphen_algorithmen, page 104]]

## Laufzeit

Mit vielen Optimierungen erhalten wir eine Laufzeit von $\mathcal{O}(\vert E \vert \cdot \log \vert E \vert)$
Sonst $\mathcal{O}(\vert E \vert \cdot \log \vert V \vert)$

