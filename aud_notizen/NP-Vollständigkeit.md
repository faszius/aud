---
tags:
  - foliensatz/08
  - cleaned
aliases:
  - NPC
---

## Ziel: Identifiziere Schwierigsten Probleme in NP

NPC = die Klasse aller NP-vollständigen Probleme

![[aud_folien_08_NP.pdf#page=26|aud_folien_08_NP.pdf, page 26]]

a) $\text{NPC} \subseteq \text{NP}$
b) Wenn $\text{P} \neq \text{NP}$, dann definitiv $\text{NPC} \subsetneq \text{P}$

## Reduktionen

Reduktionen sind Problemtransformationen

![[aud_folien_08_NP.pdf#page=27|aud_folien_08_NP.pdf, page 27]]

Das Prinzip können wir auch auf NP-Entscheidungsprobleme übertragen:

![[aud_folien_08_NP.pdf#page=28|aud_folien_08_NP.pdf, page 28]]

NP-vollständige Probleme sind dann Alle Entscheidungsprobleme $L_C$ aus NP, die mindestens so schwierig wie jedes andere Problem $L_A$ aus NP sind: $L_A \leq L_C$ für alle $L_A \in \text{NP}$

![[aud_folien_08_NP.pdf#page=29|aud_folien_08_NP.pdf, page 29]]

### Beispiel: Hamiltonscher Zyklus $\leq$ TSP

![[aud_folien_08_NP.pdf#page=30|aud_folien_08_NP.pdf, page 30]]

![[aud_folien_08_NP.pdf#page=31|aud_folien_08_NP.pdf, page 31]]

![[aud_folien_08_NP.pdf#page=32|aud_folien_08_NP.pdf, page 32]]

## SAT

![[aud_folien_08_NP.pdf#page=33|aud_folien_08_NP.pdf, page 33]]

### SAT Ist NP-hart

![[aud_folien_08_NP.pdf#page=34|aud_folien_08_NP.pdf, page 34]]

![[aud_folien_08_NP.pdf#page=35|aud_folien_08_NP.pdf, page 35]]

![[aud_folien_08_NP.pdf#page=36|aud_folien_08_NP.pdf, page 36]]

![[aud_folien_08_NP.pdf#page=37|aud_folien_08_NP.pdf, page 37]]

### SAT $\leq$ 3SAT

![[aud_folien_08_NP.pdf#page=38|aud_folien_08_NP.pdf, page 38]]

![[aud_folien_08_NP.pdf#page=39|aud_folien_08_NP.pdf, page 39]]

## 3-Färbbarkeit Von Graphen

![[aud_folien_08_NP.pdf#page=40|aud_folien_08_NP.pdf, page 40]]

### 3SAT $\leq$ 3COLORING

![[aud_folien_08_NP.pdf#page=41|aud_folien_08_NP.pdf, page 41]]

![[aud_folien_08_NP.pdf#page=42|aud_folien_08_NP.pdf, page 42]]

![[aud_folien_08_NP.pdf#page=43|aud_folien_08_NP.pdf, page 43]]

![[aud_folien_08_NP.pdf#page=44|aud_folien_08_NP.pdf, page 44]]

## Eine Auswahl Aus NPC

![[aud_folien_08_NP.pdf#page=45|aud_folien_08_NP.pdf, page 45]]

## Approximation

![[aud_folien_08_NP.pdf#page=48|aud_folien_08_NP.pdf, page 48]]

![[aud_folien_08_NP.pdf#page=49|aud_folien_08_NP.pdf, page 49]]