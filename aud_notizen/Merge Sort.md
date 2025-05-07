---
tags:
  - foliensatz/02/c
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

#TODO Korrektheit Beispiel überprüfen

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

#TODO