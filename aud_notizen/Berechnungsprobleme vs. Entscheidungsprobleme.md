---
tags:
  - foliensatz/08
  - cleaned
---

## Berechnungsprobleme vs. Entscheidungsprobleme

Ein Berechnungsproblem sieht wie folgt aus:
Gegeben ein Problem `P`, suchen wir eine Lösung `S`
Beispiel: berechne die kürzeste Pfade in einem Graphen

Ein Entscheidungsproblem sieht wiederum so aus:
Gegeben ein Problem `P`, fragen wir ob `P` die Eigenschaft `E` hat (wir suchen also eine 0/1-Antwort)
Beispiel: ist ein gerichteter Graph stark zusammenhängend?

Man kann jedes Berechnungs- in ein Entscheidungsproblem überführen, sodass eine Polynomialzeit-Lösung für das Entscheidungsproblem auch eine Polynomialzeit-Lösung für das Berechnungsproblem gibt

## Beispiel: Faktorisieren

Wir haben folgendes Entscheidungsproblem:
Gegeben eine $n$-Bit Zahl $N \geq 2$ und eine Zahl $B$, wollen wir wissen, ob der kleinste Primfaktor von $N$ maximal $B$ ist

![[aud_folien_08_NP.pdf#page=7|aud_folien_08_NP.pdf, page 7]]

![[aud_folien_08_NP.pdf#page=8|aud_folien_08_NP.pdf, page 8]]

Da in jeder Iteration das Suchintervall um die Hälfte reduziert wird, und wir zu Beginn eine Intervalllänge $N$ haben, sind wir also nach $\Theta(\log_2 N) = \Theta(n)$ Iterationen fertig

![[aud_folien_08_NP.pdf#page=9|aud_folien_08_NP.pdf, page 9]]

Der Korrektheitsbeweis sieht dann wie folgt aus:

![[aud_folien_08_NP.pdf#page=10|aud_folien_08_NP.pdf, page 10]]

![[aud_folien_08_NP.pdf#page=11|aud_folien_08_NP.pdf, page 11]]

## Berechnung Durch Entscheidung

Gegeben ein Berechnungsproblem:
Gegeben: Problem `P`
Gesucht: Lösung `S`

Erhalten wir folgendes Entscheidungsproblem:
Gegeben: Problem `P`, String `s`
Gesucht: Ist `s` ein Präfix der Binärdarstellung einer Lösung `S`?

![[aud_folien_08_NP.pdf#page=12|aud_folien_08_NP.pdf, page 12]]

Sofern die Bitlänge der Lösungen polynomiell beschränkt ist und `decide` in Polynomiallaufzeit läuft, läuft `compute` auch in Polynomialzeit

![[aud_folien_08_NP.pdf#page=13|aud_folien_08_NP.pdf, page 13]]

