---
tags:
  - foliensatz/04
  - cleaned
---

## [[AVL-Bäume|AVL]] Vs. [[Rot-Schwarz-Bäume]]

![[aud_folien_04_advanced_data_structures.pdf#page=50|aud_folien_04_advanced_data_structures, page 50]]

Bei [[AVL-Bäume|AVL-Bäumenn]] verletzen Einfügen und Löschen in der Regel öfter die Baum-Bedingung, folglich mehr Aufwand zum Rebalancieren

Bei [[Rot-Schwarz-Bäume|Rot-Schwarz-Bäumen]] dauert die Suche evtl. länger

AVL-Bäume sind als geeigneter, wenn mehr Such-Operationen und weniger Einfüge- und Lösch-Operationen 

## AVL $\subset$ Rot-Schwarz

![[aud_folien_04_advanced_data_structures.pdf#page=51|aud_folien_04_advanced_data_structures, page 51]]

Jeder nicht-leere AVL-Baum der Höhe $h$ lässt sich als Rot-Schwarz-Baum mit Schwarzhöhe $\lceil \frac{h+1}{2} \rceil$ darstellen

Allgemeiner: Für gerades $h$ gibt es sogar einen Baum mit roter Wurzel für Schwarzhöhe $h/2$, der alle anderen RS-Baumbedingungen erfüllt

Beweis per Induktion:
Gilt für ein-Knoten-Baum mit schwarzer oder roter Wurzel ($h = 0$)

![[aud_folien_04_advanced_data_structures.pdf#page=52|aud_folien_04_advanced_data_structures, page 52]]

Gilt für Baum mit schwarzer Wurzel $(h = 1)$

![[aud_folien_04_advanced_data_structures.pdf#page=53|aud_folien_04_advanced_data_structures, page 53]]

Induktionsschritt: $h \geq 2$ gerade

Wähle für linken Teilbaum RS-Baum mit schwarzer Wurzel mit $\text{SH} = \lceil \frac{(h-1)+1}{2} = \frac{h}{2} \rceil$

Wähle für rechten Teilbaum RS-Baum mit schwarzer Wurzel mit $\text{SH} = \frac{h}{2}$ für Höhe $h-1$ bzw. mit $\text{SH} = \lceil \frac{(h-2)+1}{2} \rceil = \frac{h}{2}$ für Höhe $h-2$

![[aud_folien_04_advanced_data_structures.pdf#page=54|aud_folien_04_advanced_data_structures, page 54]]

Induktionsschritt: $h \geq 3$ ungerade

Wähle für linken Teilbaum RS-Baum mit roter Wurzel mit $\text{SH} = \frac{h-1}{2}$ 

Wähle für rechten Teilbaum RS-Baum mit roter Wurzel mit $\text{SH} = \frac{h-1}{2}$ für Höhe $h-1$ bzw. mit schwarzer Wurzel mit $\text{SH} = \lceil \frac{h+1-2}{2} \rceil = \frac{h-1}{2}$ für Höhe $h-2$.

## [[AVL-Bäume|AVL]] $\neq$ [[Rot-Schwarz-Bäume|Rot-Schwarz-Baum]]

Für jede Höhe $h \geq 3$ gibt es einen Rot-Schwarz-Bäume|Rot-Schwarz-Baum, der kein AVL-Baum ist

Für größere $h$ verwende zweimal diesen Teilbaum und hänge beide Teilbäume an eine neue (schwarze) Wurzel

![[aud_folien_04_advanced_data_structures.pdf#page=56|aud_folien_04_advanced_data_structures, page 56]]