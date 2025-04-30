---
tags:
  - foliensatz/02/b
  - cleaned
aliases:
  - O-Notation
  - $\Theta$-Notation
  - $\mathcal{O}$-Notation
  - $o$-Notation
  - $\Omega$-Notation
  - $\omega$-Notation
---

## Landau Symbole

### $\Theta$-Notation

Wir betrachten eine Funktion $g$, die eine Eingabekomplexität $n$ nimmt und anhand derer eine Laufzeit $g(n) \in \mathbb{R}_{>0}$ berechnet, also eine reelle Zahl größer als 0.
Wir wollen jetzt eine Gruppe an Funktionen bestimmen, deren Laufzeit "ähnlich" zu der von $g$ ist, bzw. eine Gruppe an Funktionen, die genau so schnell steigen wie $g$. Diese Gruppe an Funktionen ist durch $\Theta(g)$ gegeben:

$$\Theta(g) = \{f : \exists c_1, c_2 \in \mathbb{R}_{>0}, n_0 \in \mathbb{N}, \forall n \geq n_0, 0 \leq c_1 g(n) \leq f(n) \leq c_2 g(n)\}$$

Diese Menge beschreibt alle Funktionen $f$, für die es zwei positive Konstanten $c_1, c_2$ und eine positive ganze Zahl $n_0$ gibt, sodass für alle Eingaben $n$, die größer gleich $n_0$ sind, $f(n)$ zwischen $c_1 g(n)$ und $c_2 g(n)$ liegt, also alle Funktionen $f$, die ab einem bestimmen Punkt von $g$ eingeschlossen werden können.
Man schreibt auch $f \in \Theta(g)$ oder $f = \Theta(g)$.

Das Ganze sieht veranschaulicht dann so aus:

![[aud_folien_02ab_sorting.pdf#page=33|aud_folien_02ab_sorting, page 33]]

### $\mathcal{O}$-Notation

Die $\mathcal{O}$-Notation ist ähnlich zur $\Theta$-Notation. Wir haben wieder eine Funktion $g$, die eine Laufzeit beschreibt, und wollen eine Menge an Funktionen $f$. Jedoch wollen wir dieses Mal nicht eine Menge an Funktionen $f$, die *gleich* schnell wachsen, sondern wir wollen eine Menge an Funktionen $f$, die *schneller* wachsen. Diese Menge ist wie folgt definiert: 

$$\mathcal{O}(g) = \{ \exists c \in \mathbb{R}_{>0}, n_0 \in \mathbb{N}, \forall n \geq n_0, 0 \leq f(n) \leq cg(n)\}$$

Diese Menge beschreibt alle Funktionen $f$, für die es eine positive Konstanten $c$ und eine positive ganze Zahl $n_0$ gibt, sodass für alle Eingaben $n$, die größer gleich $n_0$ sind, $f(n)$ unter $c g(n)$ liegt, also alle Funktionen $f$, die ab einem bestimmen Punkt höchstens so schnell wie $g$ wachsen.

Das Ganze kann dann so aussehen:

![[aud_folien_02ab_sorting.pdf#page=37|aud_folien_02ab_sorting, page 37]]

#### Rechenregeln

- Konstanten: $f(n) = a$ mit $a \in \mathbb{R}_{>0}$ konstant. Dann $f(n) = \mathcal{O}(1)$
- Skalare Multiplikation: $f = \mathcal{O}(g)$ und $a \in \mathbb{R}_{>0}$. Dann $a \cdot f = \mathcal{O}(g)$
- Addition: $f_1 = \mathcal{O}(g_1)$ und $f_2 = \mathcal{O}(g_2)$. Dann $f_1 + f_2 = \mathcal{O}(\max\{g_1, g_2\})$ (punktweise $\max$, also für jede Eingabe)
- Multiplikation: $f_1 = \mathcal{O}(g_1)$ und $f_2 = \mathcal{O}(g_2)$. Dann $f_1 \cdot f_2 = \mathcal{O}(g_1 \cdot g_2)$

### $\Omega$-Notation

Mit der $\Omega$-Notation erhalten wir eine Menge an Funktionen, die *mindestens* so schnell wie $g$ wachsen:

$$\Omega(g) = \{f : \exists c \in \mathbb{R}_{>0} n_0 \in \mathbb{N}, \forall n \geq n_0, 0 \leq cg(n) \leq f(n)\}$$

Die Menge beschreibt alle Funktionen $f$, die ab einem bestimmten Punkt mindestens so schnell wie g wachsen.

![[aud_folien_02ab_sorting.pdf#page=40|aud_folien_02ab_sorting, page 40]]

### $o$-Notation

Mit der $o$-Notation erhalten wir eine Menge an Funktionen, die ab einem bestimmten Punkt *langsamer* (nicht höchstens so schnell!) als $g$ wachsen:

$$o(g) = \{f: \forall c \in \mathbb{R}_{>0}, \exists n_0 \in \mathbb{N}, \forall n \geq n_0, 0 \leq f(n < cg(n))\}$$

### $\omega$-Notation

Mit der $o$-Notation erhalten wir eine Menge an Funktionen, die ab einem bestimmten Punkt *schneller* (nicht mindestens so schnell!) als $g$ wachsen:

$$\omega(g) = \{f: \forall c \in \mathbb{R}_{>0}, \exists n_0 \in \mathbb{N} \geq n_0, 0 < cg(n) \leq f(n)\}$$

### Zusammenhang $\mathcal{O}$, $\Omega$, $\Theta$

Für beliebige $f(n), g(n): \mathbb{N} \rightarrow \mathbb{R}_{>0}$ gilt:
$f(n) = \Theta(g(n))$ genau dann, wenn $f(n) = \mathcal{O}(g(n))$ und $f(n) = \Omega(g(n))$

Beachte: $\Omega(g)$, $\mathcal{O}(g)$ sind nur untere bzw. obere Schranken:
Beispiel: $f(n) = \Theta(n^3)$, also auch:
$f(n) = \mathcal{O}(n^5)$, da $\Theta(n^3) \subseteq \mathcal{O}(n^3) \subseteq \mathcal{O}(n^5)$
$f(n) = \Omega(n)$, da $\Theta(n^3) \subseteq \Omega(n^3) \subseteq \Omega(n)$

### Anwendung $\mathcal{O}$-Notation

$f = \mathcal{O}(g)$ ist die übliche Schreibweise, sollte aber als $f \in \mathcal{O}(g)$ gelesen werden. Es ist allgemein besser, die $\mathcal{O}$-Notation als Mengen aufzufassen und von links nach rechts zu lesen (mit $\in$, $\subseteq$):

$$\begin{align}
5 \cdot n^2 + n^4 & = \mathcal{O}(n^2) + n^4 && = \mathcal{O}(n^4) && = \mathcal{O}(n^5) \\
& \in && \subseteq && \subseteq
\end{align}$$

Es gilt nicht: $\mathcal{O}(n^4) = \mathcal{O}(n^5) \Leftrightarrow \mathcal{O}(n^5) = \mathcal{O}(n^4)$, was mit der Mengenschreibweise klarer wird: $A \subseteq B$ bedeutet nicht unbedingt $B \subseteq A$

Ungleichungen mit $\leq$ sollten nur mit $\mathcal{O}$ verwendet werden,
Ungleichungen mit $\geq$ sollten nur mit $\Omega$ verwendet werden

$5 \cdot n^2 + n^4 \leq 6 \cdot n^4 = \mathcal{O}(n^4)$
ist gültig, jedoch nicht 
$5 \cdot n^2 + n^4 \leq 6 \cdot n^4 = \Omega(n^4)$