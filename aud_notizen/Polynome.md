---
tags:
  - foliensatz/07
  - cleaned
aliases:
  - Koeffizienten-Darstellung
  - Punkt-Wert-Darstellung
  - Punkt/Wert-Darstellung
  - Polynom
---

## Koeffizientendarstellung

### Auswertung

Die Koeffizientendarstellung eines Polynoms ist gegeben durch ein Array `p[]` der Koeffizienten `p[i]`, wobei das Polynom dann wie folgt aufgebaut ist:
$p(x) = p_0 + p_1x + p_2x^2 + \ldots + p_{n-2}x^{n-2} + p_{n-1}x^{n-1}$ mit $p_{n-1} \neq 0$ und $\text{grad}(p(x)) = n-1$

Um an das Polynom an der Stelle $w$ schnell auszuwerten (also um effizient den Wert des Polynoms an der Stelle $x = w$ zu berechnen), können wir die Horner-Methode anwenden:
$p(x) = (((p_{n-1}x+p_{n-2})x+p_{n-3})x + \ldots p_1)x + p_0$
(diese Methode ist besonders schnell, da wir uns die aufwändige Berechnung separater Potenzen für jeden Koeffizienten sparen)

Der Pseudocode für diese Methode hat dann eine Laufzeit von $\Theta(n)$ Schritten, wobei $n$ die Größe des Arrays der Koeffizienten ist

![[aud_folien_07_advanced_designs.pdf#page=5|aud_folien_07a_advanced_designs, page 5]]

### Multiplikation

Um zwei Polynome $p(x)$ und $q(x)$ zu multiplizieren (beide vom Grad $n-1$), kann man wie folgt vorgehen:
$$p(x) \cdot q(x) = \left(\sum_{i=1}^{n-1}p_ix^i \right) \cdot \left(\sum_{i=0}^{n-1}q_ix^i \right) = \sum_{k=0}^{2n-2}\left(\sum_{j=0}^{k}p_j\cdot q_{k-j}\right)x^k$$
Das resultierende Polynom ist dann vom Grad $2n-2$. Dieses Vorgehen nennt man Faltung/"Konvolution" der Koeffizienten.
Der Pseudocode für diese Methode hat dann eine Laufzeit von $\Theta(\sum_{k=0}^{2n-2}k) = \Theta(n^2)$ Schritten, wobei $n$ die Größe des Arrays der Koeffizienten ist. Die Frage ist jetzt - geht das schneller?

![[aud_folien_07_advanced_designs.pdf#page=6|aud_folien_07a_advanced_designs, page 6]]

## Punkt/Wert-Darstellung

Gegeben ein Polynom $p(x)$ in Koeffizientendarstellung, ist die Punkt/Wert-Darstellung des Polynoms ein Array `p[]` der Punkte/Werte `p[i].x`, `p[i].y`

### Eindeutigkeit Der Punkt/Wert-Darstellung

Jedes Polynom $p(x)$ über einen Körper vom Grad $\leq n-1$ lässt sich eindeutig durch $n$ Punkt/Wert-Paare $(x_j, y_j)_{j=0,\ldots,n-1}$ für verschiedene $x_j$ durch $y_j = p(x_j)$ beschreiben.

![[aud_folien_07_advanced_designs.pdf#page=9|aud_folien_07_advanced_designs, page 9]]

### Polynom-Multiplikation

Jetzt wollen wir in Punkt/Wert-Darstellung zwei Polynome miteinander multiplizieren.
Dafür können wir das Produkt $r(x_j)$ einfach als $r(x_j) = p(x_j) \cdot q(x_j)$ für alle $j = 0, 1, \ldots, 2n-2$ definieren - wir multiplizieren also einfach $n$-Mal die gespeicherten $y$-Werte der beiden Polynome (die für die gleichen $x$-Werte definiert sind) und speichern die neuen $y$-Werte. Dadurch bekommt der Pseudocode eine Laufzeit von $\Theta(n)$:

![[aud_folien_07_advanced_designs.pdf#page=11|aud_folien_07_advanced_designs, page 11]]
