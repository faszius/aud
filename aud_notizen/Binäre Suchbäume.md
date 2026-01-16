---
tags:
  - cleaned
  - foliensatz/03
aliases:
  - Binären Suchbäumen
  - Binärer Suchbaum
  - Suchbaum
  - Suchbäume
  - BST
  - Binary Search Tree
Related:
  - "[[Rotation]]"
---

## Binäre Suchbäume

![[aud_folien_03_basic_data_structures.pdf#page=66|aud_folien_03_basic_data_structures, page 66]]

Ein binärer Suchbaum ist ein [[Binäre Bäume|Binärbaum]], sodass für alle Knoten `z`gilt:
Wenn `x` Knoten im linken Teilbaum von `z`, dann `x.key <= z.key`
Wenn `y` Knoten im rechten Teilbaum von `z`, dann `y.key >= z.key`

## Preorder + Eindeutige Werte $\Rightarrow$ Binärer Suchbaum

![[aud_folien_03_basic_data_structures.pdf#page=67|aud_folien_03_basic_data_structures, page 67]]

Der erste Wert der Preorder-Traversierung identifiziert die Wurzel
Anhand dessen, dass der linke Teilbaum nur kleinere Werte enthält, und der rechte nur größere, lassen sich die Werte in einen linken und rechten Teilbaum aufteilen, mit dessen Werten man wieder das gleiche machen kann
Gilt analog für Postorder, nur dass der letzte Wert die Wurzel enthält

## Inorder + Eindeutige Werte $\nRightarrow$ Binärer Suchbaum

![[aud_folien_03_basic_data_structures.pdf#page=68|aud_folien_03_basic_data_structures, page 68]]

Beide Suchbäume haben gleiche Inorder

## Suchen

Dadurch, dass wir jetzt wissen, ob wir das linke oder rechte Kind besuchen müssen, können wir Werte viel schneller finden! $\mathcal{O}(h)$ vs. $\mathcal{O}(n)$

### Rekursiv

![[aud_folien_03_basic_data_structures.pdf#page=69|aud_folien_03_basic_data_structures, page 69]]

Laufzeit $\mathcal{O}(h)$

### Iterativ

![[aud_folien_03_basic_data_structures.pdf#page=70|aud_folien_03_basic_data_structures, page 70]]

## Einfügen

![[aud_folien_03_basic_data_structures.pdf#page=71|aud_folien_03_basic_data_structures, page 71]]

Laufzeit $\mathcal{O}(h)$
Vorgehen: Gehe Baum von oben nach unten durch bis freie Stelle im richtigen Teilbaum gefunden

## Löschen

### Fälle

![[aud_folien_03_basic_data_structures.pdf#page=72|aud_folien_03_basic_data_structures, page 72]]

(ERSTES IF und ZWEITES IF)

![[aud_folien_03_basic_data_structures.pdf#page=73|aud_folien_03_basic_data_structures, page 73]]

(SONST)

![[aud_folien_03_basic_data_structures.pdf#page=74|aud_folien_03_basic_data_structures, page 74]]

(DRITTES IF)

### Algorithmus

![[aud_folien_03_basic_data_structures.pdf#page=76|aud_folien_03_basic_data_structures, page 76]]

Wir betrachten mehrere Fälle:
- ERSTES IF: `z` hat kein linkes Kind. Dann ersetze `z` durch rechten Teilbaum
- ZWEITES IF: `z` hat kein rechtes Kind. Dann ersetze `z` durch linken Teilbaum
	- SONST gehe eins nach rechts und ganz nach links, also suche nächstgrößeren Wert `y` von `z`
		- DRITTES IF: Falls dieser Wert `y` kein Kind von `z` ist (sonst würde Z11 einen Kreisschluss erzeugen!), transplantiere den rechten Teilbaum von `y` an den Parent von `y` und ersetze `z` an der Spitze des rechten Teilbaums von `z` durch `y`
		- Dann hänge `y` an den Elternknoten von `z` und hänge den linken Teilbaum von `z` an `y`

Laufzeit $\Theta(h)$
(Weil wir im schlimmsten Fall, also im 3. IF-Case, potentiell den ganzen Baum runter müssen)

## Höhe [[Laufzeitanalyse|Laufzeit]]

![[aud_folien_03_basic_data_structures.pdf#page=80|aud_folien_03_basic_data_structures, page 80]]

Ein binärer Suchbaum ist besser, wenn viele Such-Operationen <font size="1" color="gray">(es ist ja auch ein <i>Such</i>baum...)</font> 

## Höhe Eines BST

![[aud_folien_03_basic_data_structures.pdf#page=81|aud_folien_03_basic_data_structures, page 81]]

Best-Case (alle Blätter haben gleiche Tiefe):
Laufzeit = $\mathcal{O}(\log_2 n)$

Worst-Case (degeneriert: lineare Liste):
Laufzeit = $\Omega(n)$

## Durchschnittliche Höhe

![[aud_folien_03_basic_data_structures.pdf#page=82|aud_folien_03_basic_data_structures, page 82]]

Die erwartete Höhe `E[h]` des Baumes `T` erzeugt durch `randomlyBuiltTree(D)` für eine Datenmenge `D` mit $n$ Werten ist $E[h] = \Theta(\log_2 n)$

