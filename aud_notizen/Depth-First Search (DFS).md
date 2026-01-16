---
tags:
  - foliensatz/06
  - cleaned
aliases:
  - Depth-First-Search
  - Tiefensuche
  - Depth-First Search
  - DFS
Related: []
---

## Idee

Besuche zuerst alle noch nicht besuchten Nachfolgeknoten 
("Laufe so weit weg wie möglich vom aktuellen Knoten")

![[aud_folien_06_graphen_algorithmen.pdf#page=34|aud_folien_06_graphen_algorithmen, page 34]]

## Algorithmus

Laufzeit $\mathcal{O}(|V| + |E|)$

![[aud_folien_06_graphen_algorithmen.pdf#page=35|aud_folien_06_graphen_algorithmen, page 35]]

### Zeilenweise Erklärung

DFS:
Z1-2: Setze alle Knoten weiß und die Zeit auf 0
Z3: Gehe die Menge aller Knoten durch. Wurde ein Knoten noch nicht erfasst, besuche ihn (rufe DFS-VISIT auf den Knoten auf)

(meistens ist angegeben, in welcher Reihenfolge die Knoten durchgegangen werden - oft in alphabetischer oder numerischer Reihenfolge)

DFS-VISIT:
Z1-3: Erhöhe die Zeit um 1 und speichere sie als Entdeckungszeit des besuchten Knotens, setze dessen Farbe auf Grau
Z4: Für jeden adjazenten, unbearbeiteten Knoten:
	Z5-7: Falls unbearbeitet, setze seinen Vorgänger auf den jetzigen Knoten und besuche ihn
Z8: Setze die eigene Farbe auch schwarz
Z9: Erhöhe die Zeit um 1
Z10: Setze die Abschlusszeit des jetzigen Knotens

## Beispiel

Am Anfang ist `time=0` und keine der Knoten hat eine Entdeckungszeit, Abschlusszeit oder Vorgänger
Wir fangen mit dem ersten Knoten an

![[aud_folien_06_graphen_algorithmen.pdf#page=36|aud_folien_06_graphen_algorithmen, page 36]]

Die Entdeckungszeit des ersten Knotens wird auf 1 gesetzt.
Wir packen den ersten Nachbarn des Knotens auf den Stack und springen zu dem.

![[aud_folien_06_graphen_algorithmen.pdf#page=37|aud_folien_06_graphen_algorithmen, page 37]]

Die Entdeckungszeit des zweiten Knotens wird auf 2 gesetzt und der Vorgänger wird auf den ersten Knoten gesetzt.
Wir packen wieder den ersten Nachbarn auf den Stack und springen zu dem.

![[aud_folien_06_graphen_algorithmen.pdf#page=38|aud_folien_06_graphen_algorithmen, page 38]]

![[aud_folien_06_graphen_algorithmen.pdf#page=39|aud_folien_06_graphen_algorithmen, page 39]]

Die 2 hat keine Nachbarn, die noch nicht auf dem Stack sind (bzw. grau markiert wurden). Die 2 ist also abgeschlossen und bekommt die Abschlusszeit 4. Wir legen sie vom Stack ab und springen zurück.

![[aud_folien_06_graphen_algorithmen.pdf#page=40|aud_folien_06_graphen_algorithmen, page 40]]

![[aud_folien_06_graphen_algorithmen.pdf#page=41|aud_folien_06_graphen_algorithmen, page 41]]

![[aud_folien_06_graphen_algorithmen.pdf#page=42|aud_folien_06_graphen_algorithmen, page 42]]

![[aud_folien_06_graphen_algorithmen.pdf#page=43|aud_folien_06_graphen_algorithmen, page 43]]

![[aud_folien_06_graphen_algorithmen.pdf#page=44|aud_folien_06_graphen_algorithmen, page 44]]

![[aud_folien_06_graphen_algorithmen.pdf#page=45|aud_folien_06_graphen_algorithmen, page 45]]

![[aud_folien_06_graphen_algorithmen.pdf#page=46|aud_folien_06_graphen_algorithmen, page 46]]

Am Ende sind alle Knoten der einen Komponente abgearbeitet. Es bleibt nur noch ein vereinzelter Knoten.

![[aud_folien_06_graphen_algorithmen.pdf#page=47|aud_folien_06_graphen_algorithmen, page 47]]

Der wird dann auch noch abgearbeitet.

![[aud_folien_06_graphen_algorithmen.pdf#page=48|aud_folien_06_graphen_algorithmen, page 48]]

## DFS-Wald

Ein DFS-Wald ist die Menge an DFS-Bäumen die nach der DFS-Suche auf einem Graphen entsteht

Er gibt nicht unbedingt den kürzesten Weg wieder

![[aud_folien_06_graphen_algorithmen.pdf#page=49|aud_folien_06_graphen_algorithmen, page 49]]

### Kanten Im DFS-Wald

Wir zeichnen die restlichen Kanten aus dem ursprünglichen Graphen $G$ auch in den DFS-Wald $G_\text{pred}$ ein

Baumkanten: alle Kanten aus $G_\text{pred}$ 
Vorwärtskanten: alle Kanten in $G$ zu Nachkommen in $G_\text{pred}$, die keine Baumkante sind
Rückwärtskanten: alle Kanten in $G$ zu Vorfahren in $G_{pred}$, die keine Baumkante sind (inklusive Schleifen, also Kanten, die von einem Knoten zurück zum gleichen Knoten zeigen)
Kreuzkanten: alle anderen Kanten in $G$

![[aud_folien_06_graphen_algorithmen.pdf#page=50|aud_folien_06_graphen_algorithmen, page 50]]

### Kantenart Erkennen

Sei `(u, v)` die gerade betrachtete Kante im DFS-Algorithmus. Dann ist `(u, v)` ... 
... eine Baumkante, wenn `v.color==WHITE`
... eine Rückwärtskante, wenn `v.color==GRAY`
... eine Vorwärtskante, wenn `v.color==BLACK` und `u.disc < v.disc`
... eine Kreuzkante, wenn `v.color==BLACK` und `v.disc < u.disc`

![[aud_folien_06_graphen_algorithmen.pdf#page=51|aud_folien_06_graphen_algorithmen, page 51]]

![[aud_folien_06_graphen_algorithmen.pdf#page=52|aud_folien_06_graphen_algorithmen, page 52]]

![[aud_folien_06_graphen_algorithmen.pdf#page=53|aud_folien_06_graphen_algorithmen, page 53]]

### Kantenarten in Ungerichteten Graphen

In einem ungerichteten Graphen $G$ entstehen durch DFS nur Baum- und Rückwärtskanten

![[aud_folien_06_graphen_algorithmen.pdf#page=55|aud_folien_06_graphen_algorithmen, page 55]]

![[aud_folien_06_graphen_algorithmen.pdf#page=56|aud_folien_06_graphen_algorithmen, page 56]]

