---
tags:
  - foliensatz/04
  - cleaned
aliases:
  - AVL-Baum
  - AVL
---

## AVL-Bäume

![[aud_folien_04_advanced_data_structures.pdf#page=46|aud_folien_04_advanced_data_structures, page 46]]

Balance in Knoten $x$:
$B(x) = \text{Höhe}(\text{rechter Teilbaum}) - \text{Höhe}(\text{linker Teilbaum})$

Ein AVL-Baum ist ein [[Binäre Suchbäume|binärer Suchbaum]], sodass für die Balance $B(x)$ in jedem Knoten $x$ gilt: $B(x) \in \{-1, 0, +1\}$.

## Beispiel

![[aud_folien_04_advanced_data_structures.pdf#page=47|aud_folien_04_advanced_data_structures, page 47]]

## Höhe AVL-Baum

Ein AVL-Baum mit $n$ Knoten hat maximale Höhe $h \leq 1,441 \cdot \log_2 n$

![[aud_folien_04_advanced_data_structures.pdf#page=48|aud_folien_04_advanced_data_structures, page 48]]

![[aud_folien_04_advanced_data_structures.pdf#page=49|aud_folien_04_advanced_data_structures, page 49]]

Beweisidee:
Sei $n_h$ die minimale Anzahl von Knoten in einem AVL-Baum der Höhe $h$
Dann: $n_0 = 1$, $n_1 = 2$, $n_2 = 4$
Allgemein: $n_h = 1 + n_{h-1} + n_{h-2}$
Folglich: $n_h = F_{h+2}-1$

Schauen wir uns die Fibonacci-Zahlen an, erhalten wir 
$h \approx 1,441 \cdot \log_2 n$

## Einfügen

![[aud_folien_04_advanced_data_structures.pdf#page=58|aud_folien_04_advanced_data_structures, page 58]]

Einfügen funktioniert wie im binären Suchbaum (mit Sentinel), danach rebalancieren
Fälle für umgekehrte Schwergewichtigkeit natürlich gespiegelt behandeln

### Fälle

Um den Baum wieder zu balancieren, bedienen wir uns der [[Rotation]]

![[aud_folien_04_advanced_data_structures.pdf#page=60|aud_folien_04_advanced_data_structures, page 60]]

![[aud_folien_04_advanced_data_structures.pdf#page=64|aud_folien_04_advanced_data_structures, page 64]]

![[aud_folien_04_advanced_data_structures.pdf#page=65|aud_folien_04_advanced_data_structures, page 65]]

![[aud_folien_04_advanced_data_structures.pdf#page=66|aud_folien_04_advanced_data_structures, page 66]]

### [[Laufzeitanalyse|Laufzeit]]

![[aud_folien_04_advanced_data_structures.pdf#page=67|aud_folien_04_advanced_data_structures, page 67]]

Gesamtlaufzeit $\mathcal{O}(h) = \mathcal{O}(\log n)$

## Löschen

Wie im [[Binäre Suchbäume|binären Suchbaum]], nur das Rebalancierung evtl. bis hinauf in die Wurzel notwendig ist

## Laufzeiten

| Operation | Laufzeit         |
| --------- | ---------------- |
| Suchen    | $\Theta(\log n)$ |
| Einfügen  | $\Theta(\log n)$ |
| Löschen   | $\Theta(\log n)$ |

AVL-Bäume haben bessere (theoretische) Konstanten als [[Rot-Schwarz-Bäume]], je nach Daten und Operationen aber in der Praxis nur unwesentlich schneller