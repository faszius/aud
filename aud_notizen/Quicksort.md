---
tags:
  - foliensatz/02/d
  - cleaned
---

## Idee

Wie in [[Merge Sort]] benutzt Quicksort den Divide & Conquer Ansatz
Quicksort steckt jedoch mehr Arbeit in's Aufteilen, dafür ist das Zusammenfügen kostenlos

![[aud_folien_02cd_sorting_v2.pdf#page=19|aud_folien_02cd_sorting_v2, page 19]]

## Algorithmus: Quicksort

![[aud_folien_02cd_sorting_v2.pdf#page=20|aud_folien_02cd_sorting_v2, page 20]]

### Zeilenweise Erklärung

1. Setze das <font color="aquamarine">pivot</font> Element auf das linke Element
2. Setze <font color="chartreuse">p</font> links und <font color="red">q</font> rechts neben die Eingabe
3. Solange <font color="chartreuse">p</font> kleiner als <font color="red">q</font> ist
	1. Bis Element <font color="chartreuse">p</font> $\geq$ <font color="aquamarine">pivot</font>, erhöhe <font color="chartreuse">p</font> um eins
	2. Bis Element <font color="red">q</font> $\leq$ <font color="aquamarine">pivot</font>, erniedrige <font color="red">q</font> um eins
	3. Wenn <font color="chartreuse">p</font> kleiner als <font color="red">q</font> ist, tausche die beiden Elemente
4. Gebe <font color="red">q</font> wieder

Definiere den linken Wert als den pivot Wert. Gehe nun die Elemente von innen nach außen durch und tausche sie, wenn das linke größer gleich und das rechte kleiner gleich ist. Wenn die Suchindizes sich überkreuzen, sind links von p nur kleinere Werte und rechts von q nur größere. Wird das Array an p oder q geteilt, kann das Array so Stück für Stück sortiert werden.

## Beispiel `quicksort`

Zu sortierendes Array: 
`A = | 17 | 87 | 53 | 12 |`

Beim ersten Aufruf von `quickSort` sind die Indizes `left` und `right` (abgekürzt als `l` und `r`) wie folgt gesetzt:

```
  l              r
| 17 | 87 | 53 | 12 |
```

Jetzt berechnen wir mit `partition` die Stelle, an der wir teilen:

### `partition`

Zuerst setzen wir die Indizes `p` und `q` links und rechts von `l` und `r`. Der `pivot`-Wert wird auf den Wert des ersten Elementes gesetzt:

```
p   l              r    q
  | 17 | 87 | 53 | 12 |

pivot = 17
```

Jetzt wird `p` erhöht, bis es auf ein Element größer gleich 17 zeigt, und `q` erniedrigt, bis es auf ein Element kleiner gleich 17 zeigt:

```
    lp             rq
  | 17 | 87 | 53 | 12 |

pivot = 17
```

Da `p < q` ist, werden die beiden Werte getauscht:

```
    lp             rq
  | 12 | 87 | 53 | 17 |

pivot = 17
```

Jetzt laufen `p` und `q` wieder weiter:

```
    lq   p         r
  | 12 | 87 | 53 | 17 |

pivot = 17
```

Jetzt sind `p` und `q` wieder stehen geblieben, jedoch ist nicht mehr `p < q`. Dementsprechend tauschen wir die beiden Werte nicht, und springen mit `q = 0` in `quicksort` 1 zurück, wo mit `q` wieder `quicksort` aufgerufen wird

### `quicksort` 1

Wir erhalten `left = 0` und `right = 0`. Da die beiden Indizes jedoch ein Array mit nur einem Element beschreiben, terminiert die Methode sofort.

### `quicksort` 2

Wir erhalten `left = 1` und `right = 3`. Unsere Indizes werden also wie folgt gesetzt:

```
       l         r
| 12 | 87 | 53 | 17 |
```

Wir rufen `partition` auf, um unser Array zu teilen

#### `partition`

Am Anfang sind die Werte wie folgt gesetzt:

```
   p   l         r    q
| 12 | 87 | 53 | 17 |

pivot = 87
```

`p` und `q` laufen wieder in das Array rein:

```
       lp        rq    
| 12 | 87 | 53 | 17 |

pivot = 87
```

Und da `p < q`, tauschen wir:

```
       lp        rq    
| 12 | 17 | 53 | 87 |

pivot = 87
```

`p` und `q` suchen jetzt nach dem nächsten Wert:

```
       l    q    rp    
| 12 | 17 | 53 | 87 |

pivot = 87
```

Da nicht mehr `p < q`, wird nicht getauscht. Wir springen mit `q = 2` in `quicksort` zurück, wo jetzt wieder `quicksort` aufgerufen wird.

#### `quicksort` 2.1

Wir erhalten `left = 1` und `right = 2`:

```
       l    r
| 12 | 17 | 53 | 87 |
```

Da das Array mehr als ein Element enthält, teilen wir es mit `partition`:

##### `partition`

```
   p   l    r    q
| 12 | 17 | 53 | 87 |

pivot = 17
```

`p` und `q` laufen in das Array rein:

```
       pq
       l    r    
| 12 | 17 | 53 | 87 |

pivot = 17
```

Da `p` und `q` auf das gleiche Element zeigen, wird nicht getauscht.

Wir springen mit `q = 1` in `quicksort` zurück, wo `quicksort` mit `q` rekursiv aufgerufen wird

##### `quicksort` 2.1.1

Wir erhalten `left = 1` und `right = 1`:

```
       lr       
| 12 | 17 | 53 | 87 |
```

Da wir nur ein Element angucken, springen wir zurück. Dort wird `quicksort` wieder aufgerufen.

##### `quicksort` 2.1.2

Wir erhalten `left = 2` und `right = 2`:

```
            lr       
| 12 | 17 | 53 | 87 |

```

Da wir nur ein Element angucken, springen wir zurück. Dann springen wir gleich wieder zurück, wo `quicksort` noch ein letztes Mal aufgerufen wird

#### `quicksort` 2.2

Wir erhalten `left = 3` und `right = 3`:

```
                 lr       
| 12 | 17 | 53 | 87 |

```

Wir gucken uns wieder nur ein Element an, springen also zurück in `quicksort` 2, ohne etwas zu tun. Dann springen wir wieder in den ursprünglichen Aufruf von `quicksort` zurück, wo das Programm terminiert.

## Quicksort Terminierung

Behauptung: Vor Eintritt in Z4 steht rechts von `p` stets ein Element $\geq$ `pivot`

Gilt zu Beginn (erste Ausführung `WHILE`-Schleife), da `p=left-1` und `A[left]=A[p+1]=pivot`

![[aud_folien_02cd_sorting_v2.pdf#page=29|aud_folien_02cd_sorting_v2, page 29]]

Annahme: `WHILE`-Schleife bereits mindestens einmal ausgeführt
Dann zeigt `p` nach `REPEAT` in voriger `WHILE`-Iteration auf Wert $\geq$ `pivot`

In aktueller Iteration wird `REPEAT` nur erneut erreicht, wenn `p<q` und somit in voriger `WHILE`-Iteration `swap` ausgeführt wurde.

`swap` tauschte `A[p]>=pivot` weiter nach rechts (`p<q`), daraus folgt Behauptung

![[aud_folien_02cd_sorting_v2.pdf#page=30|aud_folien_02cd_sorting_v2, page 30]]

Analog: Vor Eintritt in Z5 steht links von `q` stets ein Element $\leq$ `pivot`

Folglich terminieren beide `REPEAT`s in jeder Iteration der `WHILE`-Schleife

Da in jeder Iteration der `WHILE`-Schleife `p` (bzw. `q`) um mindestens 1 erhöht (bzw. erniedrigt) wird, muss irgendwann `p>=q` sein und die `WHILE`-Schleife terminieren

## Partition Korrektheit

### [[Schleifeninvariante]]

Bei Eintritt in Zeile 4 der `WHILE`-Schleife enthalten `A[left...p]` nur Elemente $\leq$ `pivot` und `A[q...right]` nur $\geq$ `pivot`

zz. `A[left...q] <= pivot`, `A[q+1...right] >= pivot`

Noch zz. `left <= q <= right, nicht-triviale Aufteilung

### Induktionsbasis

Gilt vor erstem Eintritt für "leere" Arrays mit `p=left-1` und `q=right+1`

### Induktionsschritt

Wenn wir wieder in Zeile 4 sind, muss `p<q` (noch) gelten

In voriger Iteration:
`p` lief in Z4 nur über Werte $\lt$ `pivot`, `q` in Z5 nur über Werte $\gt$ `pivot`, bis schließlich `A[p] >= pivot` und `A[q] <= pivot`

Folgender `swap` tauscht wegen `p < q` beide Werte, Behauptung folgt

### Letzte Iteration

Bei Eintritt `A[left...p] <= pivot`, `A[q...right] >= pivot` wegen Invariante, `p` läuft in Z4 nur über Werte $\lt$ `pivot`, `q` in 5 nur über Werte $\gt$ `pivot`, bis schließlich `A[p] >= pivot` und `A[q] <= pivot`

Dann gilt `A[left...p-1] <= pivot`, `A[q+1...right] >= pivot` nach `REPEAT`s

Da Abbruch von `REPEAT`, wenn `A[p] >= pivot` bzw. wenn `A[q] <= pivot`, entweder `q=p` oder `p=q+1`

#### Zz.:

##### `p=q+1`

Im Fall `p=q+1` gilt also `A[left...q] = A[left...p-1] <= pivot` und `A[p...right] = A[q+1...right] >= pivot`

##### `p=q`

Im Fall `p=q` gilt `A[p] = A[q] = pivot` und daher `A[left...p] = A[left...q] <= pivot`, `A[p+1...right] = A[q+1...right] >= pivot`

#### Noch Zz.:

`p=q=right` kann nur passieren, wenn `WHILE`-Schleife nur einmal ausgeführt, sonst würde nächste Iteration von `WHILE` Wert `q` weiter erniedrigen

Andererseits `p=left` nach 1. Iteration von `WHILE`, da `A[left]=pivot`

Wegen `p=left<right` würde `q=right` weitere `WHILE`-Iteration bedeuten

Also definitiv `q<right`

Zusätzlich kann `q<left` nicht passieren, da in allen `WHILE`-Iterationen (auch in letzter, in der `q<=p` wird) vor `REPEAT` links von `q` immer Wert $\leq$  `pivot` steht (vgl. Terminierung), `REPEAT` also nur bis `left` runterzählen kann

## Laufzeit

### Partition Laufzeit

Für jeder Erhöhung/Erniedrigung von `p` bzw. `q` konstant viele Schritte

`p` und `q` haben zu Beginn Abstand $n+2$ und bewegen sich in jeder Iteration aufeinander zu, also $\mathcal{O}(n)$

`p` und `q` bewegen sich in jeder einzelnen `REPEAT`-Iteration maximal 1 aufeinander zu, also $\Omega(n)$ 

Wir haben also eine Gesamtlaufzeit von $\Theta(n)$

### Quicksort Laufzeit

#### Worst-Case

Im schlimmsten Fall spaltet `partition` immer nur ein Element ab
Dann rufen wir $(n-1)$-mal Partition (mit $\Omega(n)$) auf und erhalten eine Gesamtlaufzeit von $\Omega(n^2)$

![[aud_folien_02cd_sorting_v2.pdf#page=41|aud_folien_02cd_sorting_v2, page 41]]

Intuition: nur ein Element abzuspalten ist auch schlechtester Fall und daher
$$\begin{align*}
T(n) & \leq T(n-1) + dn \\
& \leq T(n-2) + d(n-1) + dn \\
& \; \; \vdots \\
& \leq \sum_{i=1}^n di = \mathcal{O}(n^2)
\end{align*}$$

Wir beweisen die Aussage formal per Induktion:

Basisfall: gilt für $n=1$, da $T(1) \leq dn^2$

Induktionsschritt: 
$$\begin{align*}
T(n) & \leq \max_{i=1, \ldots, n-1} (T(n-i) + T(i)) + dn \\
& \leq \max_{i=1, \ldots, n-1} (d(n-1)^2 + di^2) + dn && \text{(maximal für } i=1 \text{)} \\ 
& \leq d(n-1)^2 + d + dn \\
& \leq dn^2 - 2dn + d + d + dn \\
& \leq dn^2
\end{align*}$$
für $n \geq 2$, wobei $i$ der nicht-triviale Partitionsindex ist

#### Best-Case

Im besten Fall Aufteilung in gleich große Arrays wie bei [[Merge Sort]]:
$$T(n) = 2T\left(\frac{n}{2}\right) + \Theta(n) \Rightarrow \text{Laufzeit } \Theta(n \log n)$$
Gilt auch, solange beide Arrays in Größenordnung $\Omega(n)$, z.B. stets 10% der $n$ Elemente links und 90% rechts:
$$T(n) = T(0.1) + T(0.9n) + \Theta(n) \Rightarrow \text{Laufzeit } \Theta(n \log n)$$
![[aud_folien_02cd_sorting_v2.pdf#page=45|aud_folien_02cd_sorting_v2, page 45]]

Bei gleichmäßiger Aufteilung haben wir auf jeder Ebene einen Aufwand von $\mathcal{O}(n)$ $\Rightarrow$ Gesamtaufwand $\mathcal{O}(n \log n)$

#### Average-Case-Laufzeiten?

Wie verhält sich Quicksort im Durchschnitt auf "zufälliger" Eingabe?

Für eine zufällige Permutation $D(n)$ eines fixen Arrays von $n$ Elementen benötigt Quicksort $E_{D(n)}[\text{Anzahl Schritte}] = \mathcal{O}(n \log n)$

Aber was ist eine realistische Verteilung auf Eingaben?

##### Randomized Quicksort

Ansatz: betrachte statt zufälliger Eingabe randomisierte Variante `randomizedQuicksort`

wählt als Pivot-Element immer uniform eines der Elemente (und tauscht es an Anfang des Arrays, um wie zuvor fortzufahren)

![[aud_folien_02cd_sorting_v2.pdf#page=47|aud_folien_02cd_sorting_v2, page 47]]

##### Erwartete Laufzeit

Worst-Case-Laufzeit: $T(n) = \max\{\text{\# Schritte für x}\}$

Erwartete Laufzeit: $T(n) = \max\{E_A[\text{\# Schritte für x}]\}$
Erwartete Anzahl von Schritten (über zufällige Wahl des Algorithmus A) für "schlechteste" Eingabe der Komplexität $n$

Erwartete Laufzeit von Randomized-Quicksort ist $\mathcal{O}(n \log n)$

Intuition:
zufällige Wahl des Pivot-Elementes teilt Array im Durchschnitt mittig, unabhängig davon, wie Array aussieht




