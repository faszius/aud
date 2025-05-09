---
tags:
  - foliensatz/02/c
  - "#cleaned"
---

## Idee Merge Sort (Divide & Conquer)

Teile Liste in Hälften, sortiere (rekursiv Hälften), sortiere wieder zusammen

![[aud_folien_02bc_sorting.pdf#page=33|aud_folien_02bc_sorting, page 33]]

## Algorithmus: Merge Sort

![[aud_folien_02bc_sorting.pdf#page=34|aud_folien_02bc_sorting, page 34]]

![[aud_folien_02bc_sorting.pdf#page=36|aud_folien_02bc_sorting, page 36]]

### Erklärung mergeSort

Bekomme ein Array mit einer gegebenen linken und rechten Schranke. 
Umschließen die Schranken mehr als ein Element, definiere neue Schranken, die das Array in zwei teilen (setze die Mitte im ungerade Fall eins niedriger). Dann erfolgt ein rekursiver Aufruf mit beiden "Hälften" des Arrays, wonach die beiden Ergebnisse dann zusammengeführt werden.
Umschließen die Schranken nicht mehr als ein Element, mache nichts.

### Zeilenweise Erklärung `merge`

Z1: Setze <font color="yellow">p</font> auf den Index des ersten Element des linken Teilarrays und <font color="lightgreen">q</font> auf den Index des ersten Element des rechten Teilarrays
Z2: Für alle Elemente der beiden Listen
	Z3: Falls das rechte Teilarray schon abgearbeitet wurde 
	oder 
	das linke Teilarray noch aktiv ist und das linke Element (Element <font color="yellow">p</font>) kleiner gleich dem rechten (Element <font color="lightgreen">q</font>) ist
		Z4: Kopiere das linke Element (Element <font color="yellow">p</font>) in das neue Array 
		Z5: Bewege den linken Zeiger eins nach rechts (Erhöhe <font color="yellow">p</font> um 1)
	Z6: Ansonsten 
	(das rechte Teilarray wurde nicht abgearbeitet und 
	(links ist nicht aktiv oder das linke Element (Element <font color="yellow">p</font>) ist nicht kleiner gleich dem rechten (Element <font color="lightgreen">q</font>)))
		Z7: Kopiere das rechte Element (Element <font color="lightgreen">q</font>) in das neue Array 
		Z8: Bewege den rechten Zeiger eins nach rechts (Erhöhe <font color="lightgreen">q</font> um 1)
Z9: Kopiere das neue Array ins alte

## Beispiel

Am Anfang wollen wir folgendes Array sortieren:
`A = | 17 | 87 | 53 | 12 |`

### `mergeSort` 1

```
  l    m    m+1  r
| 17 | 87 | 53 | 12 |
```
Beim allerersten Aufruf von `mergeSort` ist `left` (mit `l` gekennzeichnet) ganz links und `right` (mit `r` gekennzeichnet) ganz rechts. Dann berechnen wir die Mitte (`mid`, mit `m` gekennzeichnet) und rufen `mergeSort` auf das Teilarray von `l` bis `m` auf:

#### `mergeSort` 1.1

```
  m    m+1
  l    r
| 17 | 87 | 53 | 12 |
```
Wir rufen wieder `mergeSort` auf das Teilarray von `l` bis `m` auf:

##### `mergeSort` 1.1.1

```
  l
  r
| 17 | 87 | 53 | 12 |
```
Dieses Mal enthält unser Array nur noch ein Element. Wir machen also nichts und springen zurück zu `mergeSort` 1.1, wodurch als nächstes `mergeSort` von `m+1` bis `r` aufgerufen wird:

##### `mergeSort` 1.1.2

```
       l
       r
| 17 | 87 | 53 | 12 |
```
Das Array enthält wieder nur ein Element. Wir springen wieder zurück zu `mergeSort` 1.1, wodurch jetzt `merge` von `l` bis `r` aufgerufen wird:

##### `merge`

```
  l    r
  m    m+1
  p    q 
| 17 | 87 | 53 | 12 |
```
`B = `
`p` wird auf `l` gesetzt und `q` auf `m+1`. Unser sortiertes Array `B` ist am Anfang noch leer.

Da beide Teilarrays noch nicht abgearbeitet wurden, vergleichen wir Element `p` mit Element `q`: $17 < 87$. Da $17$ kleiner ist, schreiben wir die $17$ in unser neues Array und erhöhen `p` um eins:
```
  l    r
  m    m+1
       pq 
| 17 | 87 | 53 | 12 |
```
`B = | 17 |`

Da jetzt `p` größer als `m` ist, haben wir das linke Teilarray durchgearbeitet. Wir schreiben also als nächstes Element `q` in `B` und erhöhen `q` um eins:
```
  l    r
  m    m+1
       p    q 
| 17 | 87 | 53 | 12 |
```
`B = | 17 | 87 |`

Jetzt haben wir auch das rechte Teilarray durchgearbeitet, da `q` größer als `r` ist. Dann schreiben wir `B` an die richtige Stelle in unser Array `A` (wodurch sich zufälligerweise nichts ändert, weil die beiden Elemente schon sortiert waren):

`A = | 17 | 87 | 53 | 12 |`

Jetzt ist die linke Hälfte des Arrays sortiert. Wir springen also zurück zu `mergeSort` 1, wodurch als nächstes `mergeSort` von `m+1` bis `r` aufgerufen wird:

### `mergeSort` 1.2

```
            m    m+1
            l    r
| 17 | 87 | 53 | 12 |
```
Wir rufen wieder `mergeSort` auf das Teilarray von `l` bis `m` auf:

#### `mergeSort` 1.2.1

```
            l
            r
| 17 | 87 | 53 | 12 |
```
Dieses Mal enthält unser Array nur noch ein Element. Wir machen also nichts und springen zurück zu `mergeSort` 1.2, wodurch als nächstes `mergeSort` von `m+1` bis `r` aufgerufen wird:

#### `mergeSort` 1.2.2

```
                 l
                 r
| 17 | 87 | 53 | 12 |
```
Das Array enthält wieder nur ein Element. Wir springen wieder zurück zu `mergeSort` 1.2, wodurch jetzt `merge` von `l` bis `r` aufgerufen wird:

#### `merge`

```
            l    r
            m    m+1
            p    q 
| 17 | 87 | 53 | 12 |
```
`B = `
`p` wird auf `l` gesetzt und `q` auf `m+1`. Unser sortiertes Array `B` ist am Anfang noch leer.

Da beide Teilarrays noch nicht abgearbeitet wurden, vergleichen wir Element `p` mit Element `q`: $53 > 12$. Da $12$ kleiner ist, schreiben wir die $12$ in unser neues Array und erhöhen `q` um eins:
```
            l    r
            m    m+1
            p         q 
| 17 | 87 | 53 | 12 |
```
`B = | 12 |`

Da jetzt `q` größer als `r` ist, haben wir das rechte Teilarray durchgearbeitet. Wir schreiben also als nächstes Element `p` in `B` und erhöhen `p` um eins:
```
            l    r
            m    m+1
                 p    q 
| 17 | 87 | 53 | 12 |
```
`B = | 12 | 53 |`

Jetzt haben wir auch das linke Teilarray durchgearbeitet, da `p` größer als `l` ist. Dann schreiben wir `B` an die richtige Stelle in unser Array `A`:

`A = | 17 | 87 | 12 | 53 |`

Jetzt sind jeweils die linke und die rechte Hälfte des Arrays sortiert. Wir springen zurück zu `mergeSort` 1, wodurch jetzt `merge` von `l` bis `r` aufgerufen wird:

### `merge`

```
  l    m    m+1  r
  p         q
| 17 | 87 | 12 | 53 |
```
`B =`
`p` wird auf `l` gesetzt und `q` auf `m+1`. Unser sortiertes Array `B` ist am Anfang noch leer.

Da beide Teilarrays noch nicht abgearbeitet wurden, vergleichen wir Element `p` mit Element `q`: $17 > 12$. Da $12$ kleiner ist, schreiben wir die $12$ in unser neues Array und erhöhen `q` um eins:
```
  l    m    m+1  r
  p              q
| 17 | 87 | 12 | 53 |
```
`B = | 12 |`

Beide Teilarrays sind noch aktiv. Also vergleichen wir wieder Element `p` mit Element `q`: $53 > 17$. Da $17$ kleiner ist, schreiben wir die $17$ in unser neues Array und erhöhen `p` um eins:
```
  l    m    m+1  r
       p         q
| 17 | 87 | 12 | 53 |
```
`B = | 12 | 17 |`

Beide Teilarrays sind noch aktiv. Also vergleichen wir wieder Element `p` mit Element `q`: $87 > 153. Da $53$ kleiner ist, schreiben wir die $53$ in unser neues Array und erhöhen `q` um eins:
```
  l    m    m+1  r
       p              q
| 17 | 87 | 12 | 53 |
```
`B = | 12 | 17 | 53 |`

Jetzt ist das rechte Teilarray abgearbeitet. Wir schreiben also das Element an der Stelle `p` in `B` und erhöhen `p` um eins:
```
  l    m    m+1  r
            p         q
| 17 | 87 | 53 | 12 |
```
`B = | 12 | 17 | 53 | 87 |`

Jetzt sind beide Teilarrays abgearbeitet. Wir springen zurück zu `mergeSort` 1 und das Programm terminiert.

## Korrektheit

Wir beweisen die Korrektheit von Merge wieder mithilfe einer [[Schleifeninvariante]], deren Korrektheit wir per Induktion über `i` beweisen

### Schleifeninvariante

Schleifeninvariante (für die Schleife in Zeile 2): 
Bei jedem Eintritt (bzw. nach Ende) gilt `i=p-left+q-(mid+1)`, `p<=mid+1`, `q<=right+1`. 
Zudem ist `B[0...i-1]` sortiert und besteht aus `A[left...p-1]`, `A[mid+1...q-1]`.
Ferner gilt: `B[i-1] <=A[p], A[q]`.

Damit die Schleifeninvariante Sinn ergibt und gilt, machen wir auch noch folgende Annahmen: `B[-1] = `$- \infty$ , `A[p] = `$+ \infty$ für `p >= mid` und `A[q] = `$+ \infty$ für `q>right`

> Der erste Teil der Schleifeninvariante sagt aus, dass `i` genau den Wert hat, wie viele Elemente schon einsortiert wurden, dass `i` nie größer als die Anzahl der einzusortierenden Elemente sein wird.
> Der zweite Teil der Schleifeninvariante sagt aus, dass `B` die Elemente in sortierter Reihenfolge beinhaltet, die bis jetzt einsortiert wurden.
> Der dritte Teil der Schleifeninvariante sagt aus, dass das letzte Element von `B` stets kleiner als die beiden Elemente sein wird, auf die `p` bzw. `q` gerade zeigen (was wichtig ist, um zu zeigen, dass `B` tatsächlich sortiert ist).
> Um den dritten Teil der Schleifeninvariante zu zeigen, müssen wir davon ausgehen, dass `B[-1] = `$- \infty$ (da `B[-1]` keine echtes Element ist, dürfen wir diese Annahme treffen), und dass `A[p]` für alle `p >= mid` und `A[q]` für alle `q >= r` den Wert $+ \infty$ haben. Da der Algorithmus `p` und `q` beim Einsortieren genau so behandelt., als hätten sie den Wert $+ \infty$, wenn `p >= mid` bzw. `q >= r`, ist das auch eine gültige Annahme.

### Korrektheit Der Schleifeninvariante per Induktion

#### Basisfall

Wir betrachten den Basisfall `i=0` (`p=left`, `q=mid+1`). 
In diesem Fall gilt die Schleifeninvariante, da  `i = 0 = p-left+q-(mid+1) = left-left + (mid+1)-(mid+1) = 0 + 0 = 0`. 
Außerdem ist `B[0...-1]` sortiert und besteht aus `A[left...left-1]` `A[mid+1...mid+1-1]`, da alle genannten Teilarrays keine Elemente enthalten.
Zudem gilt `B[-1] <= A[left]` und `B[-1] <= A[mid+1]` (gilt auch nur dank unserer Annahmen).

#### Induktionsschritt Von `i` Auf `i+1`

Wir nehmen an, dass die Invariante vor der `i`-ten Iteration gilt.
Die Iteration setzt dann `B[i]` auf den kleineren bzw. einzigen Wert (falls ein Teilarray schon abgearbeitet wurde) von `A[p]`, `A[q]`.
Nach Voraussetzung ist `B[i-1] <= A[p], A[q]` (da das eine der Aussagen der Schleifeninvariante ist), sodass dann auch `B[i-1] <= B[i]` ist. Also ist `B[0...i]` nach der Iteration auch sortiert ist.

> Bei jedem Eintritt (bzw. nach Ende) gilt `i=p-left+q-(mid+1)`, `p<=mid+1`, `q<=right+1`. 
> <font color="aqua">Zudem ist B[0...i-1] sortiert</font> und besteht aus `A[left...p-1]`, `A[mid+1...q-1]`.
> Ferner gilt: `B[i-1] <=A[p], A[q]`.

Da die Teil-Arrays vorsortiert sind, gilt nach Zeile 4 bzw. 7 (also vor Erhöhen von `p` bzw. `q`): `B[i] = min{A[p], A[q]} <= A[p], A[p+1], A[q], A[q+1]`, sodass auch `B[i] <= A[p], A[q]` gilt.

> Bei jedem Eintritt (bzw. nach Ende) gilt `i=p-left+q-(mid+1)`, `p<=mid+1`, `q<=right+1`. 
> Zudem ist `B[0...i-1]` sortiert und besteht aus `A[left...p-1]`, `A[mid+1...q-1]`.
> <font color="aqua">Ferner gilt: B[i-1] &lt;=A[p], A[q].</font>

Danach wird der Zähler des kopierten Werts (also entweder `p` oder `q`) erhöht, weswegen `B[0...i]` dann auch aus `A[left...p-1]`, `A[mid+1...q-1]` besteht.

> Bei jedem Eintritt (bzw. nach Ende) gilt `i=p-left+q-(mid+1)`, `p<=mid+1`, `q<=right+1`. 
> Zudem ist `B[0...i-1]` sortiert und <font color="aqua">besteht aus A[left...p-1], A[mid+1...q-1]</font>.
> Ferner gilt: `B[i-1] <=A[p], A[q]`.

Wenn `p>=mid+1` bzw. `q>=right+1` (eine der Teilarrays also abgearbeitet wurde) wird das Teilarray nicht mehr gewählt, der dazugehörige Zählerwert also auch nicht mehr erhöht, sodass `p<=mid+1` und `q<=right+1` gilt.

> Bei jedem Eintritt (bzw. nach Ende) gilt <font color="aqua">i=p-left+q-(mid+1), p&lt;=mid+1, q&lt;=right+1</font>. 
> Zudem ist `B[0...i-1]` sortiert und besteht aus `A[left...p-1], A[mid+1...q-1]`.
> Ferner gilt: `B[i-1] <=A[p], A[q]`.

#### Terminierung

Nach Ende der `FOR`-Schleife hat `i` den Wert `i=right-left+1`. Aus `i=p-left+q-(mid+1)`, `p<=mid+1` und `q<=right+1` (siehe Schleifeninvariante) folgt dass `q=right+1` und `p=mid+1`.
Also erhalten wir mit der Schleifeninvariante die Aussage, dass `B[0...right-left]` aus `A[left...mid], A[mid+1...right]` besteht und sortiert ist, was genau das ist, was unser Algorithmus tun soll.

## [[Laufzeitanalyse|Laufzeit]]abschätzung

Wir wollen jetzt wissen, was die Laufzeit von Merge Sort ist. Vereinfacht lässt sie sich mithilfe folgender Gleichung darstellen:
$$T(n) \leq 2 \cdot T\left(\frac{n}{2}\right) + c + dn$$
(für $n \geq 2$)

$2 \cdot T\left(\frac{n}{2}\right)$ erhalten wir daher, dass wir unser Array in zwei teilen, und den Algorithmus jeweils wieder auf jedes der beiden Teilarray aufrufen. Bedeutet wir haben zwei Mal $T$, aber nur mit einem halb so großen $n$, also $T\left(\frac{n}{2}\right)$.
$c$ ist der konstante Aufwand, den wir zum Beispiel in der `IF`-Abfrage und dem berechnen von `floor` haben.
$dn$ ist der Aufwand von `merge` (in diesem Fall $\mathcal{O}(n)$).
Für $T(1)$ erhalten wir $T(1) \leq c$, weil der Algorithmus dann einfach nichts tut bzw. in konstanter Zeit abbricht.

### Rekursion "manuell iterieren"

Wie sieht es also aus, wenn wir die Gleichung nehmen und aufdröseln? Was für einen Wert bekommen wir dann für $2 \cdot T\left(\frac{n}{2}\right)$?
Dann erhalten wir Folgendes:
$$\begin{align}
T(n) & \leq 2 \cdot T\left(\frac{n}{2}\right) + cn \\
& \leq 2 \cdot \left( 2 \cdot T\left(\frac{n}{4} \right) + \frac{cn}{2} \right) + cn \\
& \leq 2 \cdot \left( 2 \cdot \left( 2 \cdot T\left(\frac{n}{8} \right) + \frac{cn}{4} \right) + \frac{cn}{2} \right) + cn \\
& \; \; \vdots \\
& \leq 2 \cdot \left( 2 \cdot \left( 2 \ldots \left( 2 \cdot c + 2 \right) \ldots + \frac{cn}{4} \right) + \frac{cn}{2} \right) + cn
\end{align}$$
Die Gleichung wurde $\log_2 n$-mal unterteilt (da $\log_2$ uns ja sagt, wie oft wir etwas durch $2$ teilen können). 
Da $T(1) \leq c$ und wir $\log_2 n$ mal unser Array durch zwei teilen, erhalten wir am Ende $2^{\log_2 n}$ Arrays der Länge $1$ und aus $2 \cdot T\left( \frac{n}{2} \right)$ wird $2^{\log_2 n} \cdot c$.
$cn + \frac{cn}{2} + \frac{cn}{4} + \ldots$ können wir auf $\log_2 n \cdot cn$ aufrunden. 
Am Ende erhalten wir also $T(n) \leq 2^{\log_2 n} \cdot c + \log_2 n \cdot cn = \mathcal{O}(n \log n)$.

Dieses Vorgehen, um die Laufzeit rekursiver [[Algorithmen]] zu bestimmen, lässt sich auch verallgemeinern, wodurch man auf das [[Mastertheorem]] kommt.