---
tags:
  - foliensatz/02/a
  - cleaned
---

## Idee Insertion Sort: Karten Umsortieren

![[aud_folien_02a_sorting.pdf#page=9|aud_folien_02a_sorting, page 9]]

Idee: gehe von links nach rechts durch und sortiere aktuelle Karte richtig nach links ein

## Algorithmus: Insertion Sort

![[aud_folien_02a_sorting.pdf#page=10|aud_folien_02a_sorting, page 10]]

### Zeilenweise Erklärung

Z1: Für jedes Element vom zweiten bis zum letzten (von links nach rechts):
	Z2: Setze `key` auf den Wert des jetzigen Elements
	Z3: Setze `j` auf den Index des vorigen Wertes
	Z4: Solange das Element `j` größer als `key` ist:
		Z5: Kopiere Element `j` eins nach rechts
		Z6: Setze `j` auf `j-1` (also betrachte das Element vor `j`)
	Z7: Überschreibe das Element nach `j` (also `j+1`) durch `key`

Gehe alle Elemente vom zweiten bis zum letzten durch, und sortiere sie nach links ein. Das passiert, indem alle Elemente vor dem jetzigen Element so lange nach rechts kopiert werden, bis es keine vorigen Elemente mehr gibt oder das vorige Element kleiner als das jetzige ist.

## Beispiel

Zu sortierendes Array: 
`A = | 12 | 53 | 17 | 87 |`

**1. Durchlauf:**
```
A = | 12 | 53 | 17 | 87 |
key = 53
j = 0
```
`A[j]` $\ngtr$ `key` bzw. $12 \ngtr 53$
Also wird die Schleife abgebrochen

**2. Durchlauf:**
```
A = | 12 | 53 | 17 | 87 |
key = 17
j = 1
```
`key` wurde auf das nächste Element gesetzt
`j` wurde um eins erhöht

`A[j]` $>$ `key` bzw. $53 > 17$
Also wird 53 eins nach links kopiert:
```
A = | 12 | 53 | 53 | 87 |
key = 17
j = 0
```
`j` wurde um eins verringert

`A[j]` $\ngtr$ `key` bzw. $12 \ngtr 17$
Also wird `key` an Stelle `j+1` kopiert:
```
A = | 12 | 17 | 53 | 87 |
key = 17
j = 0
```

**3. Durchlauf:**
```
A = | 12 | 17 | 53 | 87 |
key = 87
j = 2
```
`A[j]` $\ngtr$ `key` bzw. $53 \ngtr 87$
Also wird die Schleife abgebrochen

**Ende:**
Also sieht das Array am Ende so aus:
`A = | 12 | 17 | 53 | 87 |`

## Terminierung Insertion Sort

Jede Ausführung der `WHILE`-Schleife erniedrigt `j<n` in jeder Iteration um 1 und bricht ab, wenn `j<0` $\rightarrow$ terminiert also immer
`FOR`-Schleife wird nur endlich oft durchlaufen

## Korrektheit Insertion Sort

Beweis der Korrektheit mittels [[Schleifeninvariante]]

#TODO: Erklärung Schleifeninvariante

**Schleifeninvariante der `FOR`-Schleife**
Bei jedem Eintritt für Zählerwert `i` (und nach letzter Ausführung) entsprechen die aktuellen Einträge in `A[0]`, ..., `A[i-1]` den sortierten ursprünglichen Eingabewerten `a[0]`, ..., `a[i-1]`. Ferner gilt `A[i] = a[i]`, ..., `A[n-1] = a[n-1]`.

>Wir unterscheiden zwischen dem sortierten Array `A` und dem ursprünglichen, unsortiertem Array `a`. Vor dem `i`-ten Schleifendurchlauf sind die Elemente `A[0]` bis `A[i-1]` die sortierte Version von `a[0]` bis `a[i-1]`, und die Elemente `A[i]` bis `A[n-1]` (also der Rest des Arrays) sind unverändert (also genau das gleiche wie `a[i]` bis `a[n-1]`).

**Korrektheit der Schleifeninvariante per Induktion:**
Induktionsbasis: Beim ersten Eintritt ist `A[0] = a[0]` und "sortiert". Zudem gilt noch `A[1] = a[1]`, ..., `A[n-1] = a[n-1]`.

>Für den ersten Durchlauf gilt die Schleifeninvariante. Dann ist nämlich `i=1` und `A[0]` bis `A[0]` ist die sortierte Version von `a[0]` bis `a[0]` (da das nur das erste Element ist). Und da die Schleife noch nicht gelaufen ist, gilt natürlich auch `A[0] = a[0]`, ..., `A[n-1] = a[n-1]`.

**Induktionsschritt von i auf i+1:**
Vor der `i`-ten Ausführung galt die Schleifeninvariante nach Voraussetzung. Insbesondere war `A[0]`, ..., `A[i-1]` die sortierte Version von `a[0]`, ..., `a[i-1]` und `A[i] = a[i]`, ..., `A[n-1] = a[n-1]`.
Durch die `WHILE`-Schleife wurde `A[i] = a[i]` nach links einsortiert und größere Elemente von `A[0]`, ..., `A[i-1]` um jeweils eine Position nach rechts verschoben. Elemente `A[i+1]`, ..., `A[n-1]` wurden nicht geändert. Also gilt die Invariante auch für `i`.

>Wir wissen jetzt, dass die Schleifeninvariante vor dem ersten Durchlauf gilt. Nun wollen wir uns angucken, was in der Schleife passiert, und ob die Schleifeninvariante auch nach dem Durchlauf der Schleife gilt.

**Korrektheit des Algorithmus' aus Korrektheit der Schleifeninvariante:**
Aus der Schleifeninvariante folgt für die letzte Ausführung (bzw. vor dem theoretischen Eintritt der Schleife für `i=n`):
`A[0]`, ..., `A[n-1]` ist die sortierte Version von `a[0]`, ..., `a[n-1]` und somit ist das Array sortiert.

## [[Laufzeitanalyse]] Insertion Sort

![[aud_folien_02ab_sorting.pdf#page=26|aud_folien_02ab_sorting, page 26]]

Wir analysieren, wie oft jede Zeile *maximal* ausgeführt wird (wir betrachten also den schlimmsten Fall!)
Jede Zeile $i$ hat Aufwand $ci$, eine Zeile $i$ braucht also beispielsweise $ci$ Prozessortakte, um ausgeführt zu werden

![[aud_folien_02ab_sorting.pdf#page=27|aud_folien_02ab_sorting, page 27]]

Zeile 1 wird $n$ Mal überprüft/ausgeführt ($(n-1)+1$, da am Ende noch eine Überprüfung der Schleifenbedingung bei `i=A.length` stattfindet)

Zeilen 2 und 3 werden $n-1$ Mal ausgeführt, da die Schleife $n-1$ Mal ausgeführt wird

Zeilen 4, 5 und 6 werden im schlimmsten Fall so oft ausgeführt, bis `j=-1` (da das eine der Abbruchbedingungen für die Schleife ist), also jeweils `i` Mal. Da `i` in der `FOR`-Schleife von $1$ bis $n-1$ erhöht wird, werden Zeilen 4, 5 und 6 jeweils $\sum_{i=1}^{n-1}i$ Mal ausgeführt. Mit der Gaußschen Summenformel ergibt das $$\sum_{i=1}^{n-1}i=\frac{n(n-1)}{2}$$
Da Zeile 4 jeweils einmal mehr überprüft wird (um für `j=-1` zu überprüfen, ob die Schleifenbedingung noch erfüllt ist), erhalten wir für Zeile 4 eine Laufzeit von $Z5 + n-1$.

Zeile 7 wird dann wie Zeilen 2 und 3 $n-1$ Mal ausgeführt

![[aud_folien_02ab_sorting.pdf#page=28|aud_folien_02ab_sorting, page 28]]

Somit erhalten wir eine maximale Gesamtlaufzeit von $$T(n) = c1 \cdot n + (c2 + c3 + c4 + c7) \cdot (n-1) + (c4 + c5 + c6) \cdot \frac{n(n-1)}{2}$$($+ c4 \cdot (n-1)$ scheint an dieser Stelle ausgelassen worden zu sein)

Die Frage ist jetzt, wie teuer eine Anweisung ist, welche Werte können wir also für $c1$ bis $c6$ einsetzen? Üblicherweise nehmen wir an, dass elementare Operationen in einem Schritt möglich sind. Wir können für unsere $ci$ also $1$ einsetzen, und erhalten $$T(n) = n + 4(n-1) + 3 \cdot \frac{n(n-1)}{2}$$

### Asymptotische Vereinfachung

![[aud_folien_02ab_sorting.pdf#page=30|aud_folien_02ab_sorting, page 30]]

Den Term, den wir erhalten haben, können wir noch weiter vereinfachen. Wenn wir uns Laufzeiten angucken, interessiert uns immer nur der "dominante" Term. 
Vergleichen wir in diesem Fall den Graphen von unserem Term $T(n)$ und den Graphen der vereinfachten Version $D(n) = 3 \cdot \frac{n(n-1)}{2}$, sehen wir, dass der Graph von $T(n)$ am Ende fast gleich schnell wächst wie der von $D(n)$. Dementsprechend reicht es, die Laufzeit mit $D(n)$, also mit dem dominanten Term, zu beschreiben.

![[aud_folien_02ab_sorting.pdf#page=31|aud_folien_02ab_sorting, page 31]]

Wenn wir noch weiter gehen, können wir $D(n)$ weiter vereinfachen, indem wir die $3$ weglassen, da die Konstante zum einen stark vom Berechnungsmodell abhängt und sich "schnell" durch Fortschritte in der Rechenleistung ändern

### Laufzeit in $\Theta$-Notation

![[aud_folien_02ab_sorting.pdf#page=35|aud_folien_02ab_sorting, page 35]]

Für $T(n) = n + 4 \cdot (n-1) + 3 \cdot \frac{n(n-1)}{2}$ gilt $T(n) \in \Theta(n^2)$. Das können wir beweisen, indem wir als untere Schranke $c_1 = \frac{3}{2}$ und $n_0 = 2$ wählen:
$$\begin{align*}
T(n) & \geq 5 \cdot (n-1) && + \frac{3}{2} \cdot n^2 && - \frac{3}{2} \cdot n \\
& \geq \frac{7}{n} \cdot n-5 && + \frac{3}{2} \cdot n^2 && \\
& \geq && \frac{3}{2} \cdot n^2
\end{align*}$$
für $n \geq 2$

Für die obere Schranke wählen wir $c_2 = 7$ und das bereits fixierte $n_0 = 2$:
$$\begin{align*}
T(n) & \leq n + && 4 \cdot n && + 2 \cdot n(n-1) \\
& \leq && 5 \cdot n && + 2 \cdot n^2 \\
& \leq && 5 \cdot n^2 && + 2 \cdot n^2 \\
& \leq && 7 \cdot n^2
\end{align*}$$
für $n \geq 2$


