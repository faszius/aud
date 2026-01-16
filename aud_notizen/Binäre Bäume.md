---
tags:
  - cleaned
  - foliensatz/03
aliases:
  - Binären Bäumen
  - Binärer Baum
  - Binärbaum
  - Binärbäume
Related:
---

## Traversieren Von Binärbäumen

### Inorder

![[aud_folien_03_basic_data_structures.pdf#page=47|aud_folien_03_basic_data_structures, page 47]]

`inorder(T.root)` ergibt:
9 - 17 - 23 - 23 - 24 - 25

#### Laufzeit

![[aud_folien_03_basic_data_structures.pdf#page=48|aud_folien_03_basic_data_structures, page 48]]

Behauptung: $T(n) = O(n)$

#### Inorder $\nRightarrow$ Baum

![[aud_folien_03_basic_data_structures.pdf#page=49|aud_folien_03_basic_data_structures, page 49]]

Verschiedene Bäume, aber gleiche Inorder-Ausgabe

### Preorder

![[aud_folien_03_basic_data_structures.pdf#page=50|aud_folien_03_basic_data_structures, page 50]]

`preorder(T.root)` ergibt
23 - 17 - 9 - 23 - 24 - 25

#### Preorder $\nRightarrow$ Binärbaum

![[aud_folien_03_basic_data_structures.pdf#page=55|aud_folien_03_basic_data_structures, page 55]]

### Postorder

![[aud_folien_03_basic_data_structures.pdf#page=51|aud_folien_03_basic_data_structures, page 51]]

`postorder(T.root)` ergibt
9 - 23 - 17 - 25 - 24 - 23

### Nutzen

![[aud_folien_03_basic_data_structures.pdf#page=53|aud_folien_03_basic_data_structures, page 53]]

Preorder-Traversieren gut zum Kopieren

![[aud_folien_03_basic_data_structures.pdf#page=54|aud_folien_03_basic_data_structures, page 54]]

Postorder-Traversieren gut zum Löschen

#### Preorder + Inorder + Eindeutige Werte $\Rightarrow$ Binärbaum

![[aud_folien_03_basic_data_structures.pdf#page=56|aud_folien_03_basic_data_structures, page 56]]

- Der erste Wert der Preorder-Traversierung identifiziert die Wurzel
- Somit kann man die Inorder-Traversierung in einen linken und einen rechten Teilbaum aufteilen
- Diese kann man anhand der Preorder- und Inorder-Traversierung wieder in einen linken und rechten Teilbaum aufteilen

## Abstrakter Datentyp Baum

`new(T)`
	Erzeugt neuen Baum namens `T`
`search(T, k)`
	Gibt Element `x` in Baum `T` mit `x.key==k` zurück (bzw. `nil`)
`insert(T, x)`
	Fügt Element `x` in Baum `T` hinzu
`delete(T, x)`
	Löscht `x` aus Baum `T`

Oft weitere Baum-Operationen wie Wurzel, Höhe, Traversieren, ...

## Suchen

![[aud_folien_03_basic_data_structures.pdf#page=60|aud_folien_03_basic_data_structures, page 60]]

Laufzeit $\Theta(n)$, da jeder Knoten maximal ein mal besucht wird, aber im schlechtesten Fall auch jeder Knoten
Vorgehen: Traversiere Baum (wie Preorder, Inorder, etc...) bis Wert gefunden

## Einfügen

![[aud_folien_03_basic_data_structures.pdf#page=61|aud_folien_03_basic_data_structures, page 61]]

Laufzeit $\Theta(1)$
Vorgehen: Packe Wert oben rechts über Baum. Erzeugt linkslastigen Baum!

## Löschen

![[aud_folien_03_basic_data_structures.pdf#page=62|aud_folien_03_basic_data_structures, page 62]]

Idee: ersetze `x` durch (Halb-)Blatt ganz rechts

### Transplantation

![[aud_folien_03_basic_data_structures.pdf#page=63|aud_folien_03_basic_data_structures, page 63]]

Laufzeit $\Theta(1)$
Vorgehen: Hänge `w` anstelle von `y` an den Elternknoten von `y`

### Algorithmus

![[aud_folien_03_basic_data_structures.pdf#page=64|aud_folien_03_basic_data_structures, page 64]]

Laufzeit $\Theta(h)$ (um unteres rechtes Element zu erreichen), wobei $h$ die Höhe ist und $h = n$ möglich ist
Vorgehen: Ersetze `x` durch unteren rechten Wert
