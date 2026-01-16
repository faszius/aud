---
tags:
  - foliensatz/03
  - foliensatz/04
  - MoC
  - "#cleaned"
Related:
  - "[[Binäre Bäume]]"
  - "[[Binäre Suchbäume]]"
  - "[[Rot-Schwarz-Bäume]]"
  - "[[AVL-Bäume]]"
  - "[[Binäre Max-Heaps]]"
  - "[[B-Bäume]]"
---

## Bäume Durch [[Verkettete Listen]]

![[aud_folien_03_basic_data_structures.pdf#page=41|aud_folien_03_basic_data_structures, page 41]]

Jeder Knoten enthält:
`key` 
	Wert
`child[]`
	Array von Zeigern auf Kinder

Manchmal auch nützlich:
`parent`
	Zeiger auf Elternkoten

Baum-Bedingung: Baum ist leer oder ...
es gibt einen Knoten `r` ("Wurzel"), sodass jeder Knoten `v` von der Wurzel aus per eindeutiger Sequenz von `child`-Zeigern erreichbar ist:
`v = r.child[i1].child[i2]. ... .child[im]`

## Eigenschaften Von Bäumen

![[aud_folien_03_basic_data_structures.pdf#page=42|aud_folien_03_basic_data_structures, page 42]]

Bäume sind "azyklisch"

Für nicht-leeren Baum gibt es genau $\#Knoten-1$ viele Einträge $\neq$ `nil` über alle Listen `child[]`

## Darstellung Als Ungerichteter Graph

![[aud_folien_03_basic_data_structures.pdf#page=43|aud_folien_03_basic_data_structures, page 43]]

Achtung: in beiden Darstellungen ist die Reihenfolge in `child[]` quasi durch die Anordnung der Knoten dargestellt

![[aud_folien_03_basic_data_structures.pdf#page=44|aud_folien_03_basic_data_structures, page 44]]

Bedeutet: diese beiden Bäume sind verschieden!

## Begrifflichkeiten

![[aud_folien_03_basic_data_structures.pdf#page=45|aud_folien_03_basic_data_structures, page 45]]

![[aud_folien_03_basic_data_structures.pdf#page=46|aud_folien_03_basic_data_structures, page 46]]

Bei einem [[Binäre Bäume|Binärbaum]] hat jeder Knoten maximal zwei Kinder, `left = child[0]` und `right = child[1]`