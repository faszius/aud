---
tags:
  - foliensatz/04
  - cleaned
aliases:
  - Heaps
  - Heap
  - Max-Heap
  - Max-Heaps
Related:
  - "[[Priority Queue]]"
---

## Binärer Max-Heap

![[aud_folien_04_advanced_data_structures.pdf#page=92|aud_folien_04_advanced_data_structures, page 92]]

Ein binärer Max-Heap ist ein [[Binäre Bäume|binärer Baum]] (nicht ein [[Binäre Suchbäume|binärer Suchbaum]]!), der
1. Bis auf das unterste Level vollständig gefüllt ist, und im untersten Level von links gefüllt ist und
2. Für alle Knoten `x` $\neq$ `T.root` gilt:
   `x.parent.key` $\geq$ `x.key`

Bei Min-Heaps sind die Werte im Elternknoten jeweils kleiner

## Eigenschaften

Da der Baum (fast) vollständig ist, gilt $h \leq \log n$
Das Maximum des Heaps steht immer in der Wurzel

![[aud_folien_04_advanced_data_structures.pdf#page=93|aud_folien_04_advanced_data_structures, page 93]]

## Heaps Durch Arrays

Heaps lassen sich auch in Arrays darstellen. 
Dafür speichert man die Anzahl der Knoten in `H.size` (ein leerer Heap hat also `H.size==0)` und schreibt die Werte des Heaps Reihe für Reihe von links nach rechts in ein Array.

Den parent, das linke und das rechte Kind eines Elements an der Stelle `j` im Array kann man dann wie folgt bestimmen:
`j.parent` = $\lceil \frac{j}{2} \rceil - 1$
`j.left` = $2(j+1) - 1$
`j.right` = $2(j+1)$

![[aud_folien_04_advanced_data_structures.pdf#page=94|aud_folien_04_advanced_data_structures, page 94]]

## Einfügen

Wir fügen den Wert in der untersten Reihe an der ersten freien Stelle von links rein. Dann tauschen wir den Wert so lange nach oben, bis die Max-Eigenschaft wieder erfüllt ist.

![[aud_folien_04_advanced_data_structures.pdf#page=95|aud_folien_04_advanced_data_structures, page 95]]

### Algorithmus

![[aud_folien_04_advanced_data_structures.pdf#page=96|aud_folien_04_advanced_data_structures, page 96]]

Da der Knoten potentiell bis an die Wurzel bewegt werden muss, haben wir eine Laufzeit von $\mathcal{O}(h)$. Da der Baum ganz ausgefüllt ist, liegt die Höhe in $\log n$, wir erhalten also eine Laufzeit von $\mathcal{O}(\log n)$

## Lösche Maximum

Wenn wir das Maximum löschen, ersetzen wir es durch das "letzte" Blatt. Dann stellen wir die Max-Eigenschaft wieder her, indem wir den Wurzelknoten nach unten gegen das Maximum der beiden Kinder tauschen (`heapify`)

![[aud_folien_04_advanced_data_structures.pdf#page=97|aud_folien_04_advanced_data_structures, page 97]]

### Algorithmen

![[aud_folien_04_advanced_data_structures.pdf#page=98|aud_folien_04_advanced_data_structures, page 98]]

Da `heapify` bis in die letzte Ebene läuft, erhalten wir eine Laufzeit von $\mathcal{O}(h) = \mathcal{O}(\log n)$

## Heap-Konstruktion Aus Array

Um aus einem gegebenen Array einen Heap zu erstellen, können wir einfach das Array durchgehen und auf jedem Element des Arrays `heapify` aufrufen, sodass jedes Element des Arrays korrekt einsortiert wird.
Da jedoch alle Blätter an sich triviale Max-Heaps sind, brauchen wir den Algorithmus nur auf alle Knoten mit Kindern aufrufen, also nur auf die erste Hälfte des Arrays.

![[aud_folien_04_advanced_data_structures.pdf#page=99|aud_folien_04_advanced_data_structures, page 99]]

### Algorithmus

![[aud_folien_04_advanced_data_structures.pdf#page=100|aud_folien_04_advanced_data_structures, page 100]]

Da wir für die Hälfte aller Elemente potentiell die gesamte Tiefe des Baums durchlaufen müssen, erhalten wir eine Laufzeit $\mathcal{O}(n \cdot h) = \mathcal{O}(n \cdot \log n)$

### Beispiel

![[aud_folien_04_advanced_data_structures.pdf#page=101|aud_folien_04_advanced_data_structures, page 101]]

![[aud_folien_04_advanced_data_structures.pdf#page=102|aud_folien_04_advanced_data_structures, page 102]]

![[aud_folien_04_advanced_data_structures.pdf#page=103|aud_folien_04_advanced_data_structures, page 103]]

![[aud_folien_04_advanced_data_structures.pdf#page=104|aud_folien_04_advanced_data_structures, page 104]]

## Heap-Sort

Heap-Sort gibt die Einträge in Array `A` in absteigender Größe aus
Weil wir das Array davor zuerst sortieren müssen, erhalten wir eine Laufzeit $\mathcal{O}(n \cdot h) = \mathcal{O}(n \cdot \log n)$

![[aud_folien_04_advanced_data_structures.pdf#page=105|aud_folien_04_advanced_data_structures, page 105]]

### Beispiel

![[aud_folien_04_advanced_data_structures.pdf#page=106|aud_folien_04_advanced_data_structures, page 106]]

![[aud_folien_04_advanced_data_structures.pdf#page=107|aud_folien_04_advanced_data_structures, page 107]]

![[aud_folien_04_advanced_data_structures.pdf#page=108|aud_folien_04_advanced_data_structures, page 108]]

