---
tags:
  - foliensatz/02/d
  - cleaned
---

## Untere Schranke

![[aud_folien_02cd_sorting_v2.pdf#page=56|aud_folien_02cd_sorting_v2, page 56]]

Theorem: Jeder (korrekte) vergleichsbasierte Sortieralgorithmus muss mindestens $\Omega(n \log n)$ viele Vergleiche machen

## Eingabemenge

Wir betrachten ein Ausgangs-Array `A` mit `A[i] = i` und jede Permutation $\pi(A)$ davon für alle $\pi$. Insgesamt erhalten wir $n!$ viele mögliche Eingabe-Arrays

Jedes Eingabe-Array erfordert eine andere Ausgabe $I = \pi^{-1}$

## Mögliche Ausgaben

![[aud_folien_02cd_sorting_v2.pdf#page=58|aud_folien_02cd_sorting_v2, page 58]]

Wir nehmen an, der Algorithmus macht $m$ Vergleiche. Dann gibt es maximal $2^m$ mögliche Antwortsequenzen Ja/Nein. Abgesehen von $n$ ist das die einzige Information, die wir über `A` haben. Aufgrund der Determiniertheit führen gleiche Antwortsequenzen (selbst für verschiedene Arrays) zu gleicher Ausgabe (also gleiche Vertauschungen), sodass der Algorithmus höchstens $2^m$ verschiedene Ausgaben `I` zurückgibt.

## Ein- Und Ausgabeverhältnis

![[aud_folien_02cd_sorting_v2.pdf#page=59|aud_folien_02cd_sorting_v2, page 59]]

Wenn $2^m \lt n!$, dann gibt es verschiedene Arrays $\pi(A)$ und $\rho(A)$ für die der Algorithmus gleiches `I` ausgibt, und somit eine der beiden Ausgaben falsch sein muss:  $\texttt{I} = \pi^{-1}$ oder $\texttt{I} = \rho^{-1}$  

## Schranke Ausrechnen

Es muss also $2^m \geq n!$ gelten bzw. $m \geq \log(n!)$
Mit der Stirling-Approximation ($n! \geq \left(\frac{n}{2}\right)^n$) erhalten wir $m = \Omega(n \cdot \log(n))$ 

Theorem: Jeder (korrekte) vergleichsbasierte Sortieralgorithmus muss mindestens $\Omega(n \cdot \log n)$ viele Vergleiche machen