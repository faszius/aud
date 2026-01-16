---
tags:
  - foliensatz/08
  - cleaned
---

## Komplexitätsklasse P

Wir betrachten folgendes Entscheidungsproblem für die Eigenschaft $E$ als Menge:
$$L_E = \{P \; | \; \text{P hat Eigenschaft E}\}$$
Beispiel: $L_{SC} = \{G \; | \; \text{G ist ein gerichteter, stark zusammenhängender Graph}\}$

Komplexitätsklasse P:
Ein Entscheidungsproblem $L_E$ ist genau dann in der Komplexitätsklasse P, wenn es einen Polynomialzeit-Algorithmus $A_{L_E}$ mit Ausgabe 0/1 gibt, der stets korrekt entscheidet, ob eine Eingabe $P$ die Eigenschaft $E$ hat oder nicht, also $P \in L_E \Leftrightarrow A_{L_E}(P) = 1$ für alle $P$ gilt.

## Komplexitätsklasse NP

Ein Entscheidungsproblem $L_E$ ist genau dann in der Komplexitätsklasse NP, wenn es einen Polynomialzeit-Algorithmus $A_{L_E}$ mit Ausgabe 0/1 gibt, der bei Eingabe eines Zeugen $S_P$ für eine Eingabe $P \in L_E$ bzw. für jede Eingabe eines Zeugen $S_P$ für Eingabe $P \notin L_E$ stets korrekt entscheidet, ob eine Eingabe $P$ die Eigenschaft $E$ hat oder nicht, also 
$P \in L_E \Leftrightarrow \exists S_P : A_{L_E}(P, S_P) = 1$ für alle $P$ gilt

Der Zeuge $S$ soll zeigen, dass ein gegebenes Problem $P$ eine Eigenschaft $E$ hat oder nicht
Technische Einschränkungen sind dabei, dass die Lösungen $S$ von polynomieller Komplexität im Eingabeproblem $P$ sein müssen, meist bedeutet das, dass die Lösungen $S$ eine in der Bitlänge von $P$ polynomielle Bitlänge haben

### Beispiel

Wir definieren 
$L_\text{Fakt} = \{(N, B)\} \; | \; N > 1 \text{ hat Primfaktor } \leq B\}$

Gegenwärtig ist es unklar, wie man in Polynomialzeit ohne Hilfe (und ohne Quantencomputer) entscheidet, ob eine Eingabe $(N, B)$ in $L_\text{Fakt}$ ist oder nicht

Mit Hilfe ist es einfach:
Der Zeuge $S$ zu $P = (N, B)$ ist dann der Faktor $p$ von $N$ mit $1 < p \leq B$

![[aud_folien_08_NP.pdf#page=18|aud_folien_08_NP.pdf, page 18]]

![[aud_folien_08_NP.pdf#page=19|aud_folien_08_NP.pdf, page 19]]

## P vs. NP

Jedes Problem in $P$ ist auch in $NP$: der Algorithmus $A_{L_E}$ entscheidet ohne Hilfe

![[aud_folien_08_NP.pdf#page=21|aud_folien_08_NP.pdf, page 21]]

### Mögliche Welten

![[aud_folien_08_NP.pdf#page=23|aud_folien_08_NP.pdf, page 23]]

