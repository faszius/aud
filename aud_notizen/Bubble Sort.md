---
tags:
  - cleaned
---

## Algorithmus Bubble Sort

```
bubbleSort(A)
1 n=length(A)
2 for i=n−1 downto 1 do
3    for j=1 to i do
4       if A[j−1] > A[j] then
5          tmp=A[j]
6          A[j]=A[j−1]
7          A[j−1]=tmp
8 return A
```

### Zeilenweise Erklärung

Z1: Wir speichern uns die Länge des Arrays in einer Variable `n`
Z2: Mit jedem Durchlauf ignorieren wir ein weiteres Element am Ende des Arrays
	Z3: Vom ersten bis zum letzten Element (des Teilarrays das wir uns angucken)
		Z4: Wenn das Element, dass wir uns gerade angucken, größer ist als das nächste
		Z5: Speichere `A[j]` (also das nächste Element) zwischen
		Z6: Überschreibe `A[j]` mit `A[j-1]` (überschreibe das nächste Element mit unserem Element)
		Z7: Schreibe das gespeicherte `A[j]` an `A[j-1]` (schreibe das nächste Element an die jetzige Stelle)
Z8: Gebe das sortierte Array A wieder

> Im Endeffekt werden in Z5-Z7 einfach nur `A[j]` und `A[j-1]`, also das jetzige und das nächste Element getauscht

Gehe alle nebeneinanderliegenden Elemente von vorne bis hinten durch und tausche sie, falls das vordere größer ist. Mit jeder Wiederholung wird das letzte Element ausgelassen. 
Somit wird mit jeder Wiederholung das größte Element wie eine Blase nach hinten bewegt und dann da liegen gelassen.

## Beispiel

Zu sortierendes Array: 
`A = | 17 | 87 | 12 | 53 |`

**1. Durchlauf:**
Beim ersten Durchlauf betrachten wir das gesamte Array:
`[ 17 | 87 | 12 | 53 ]`

Zuerst gucken wir uns die ersten beiden Elemente an:
`[ 17 !> 87 | 12 | 53 ]`
Da $17 \ngtr 87$, werden die beiden Elemente nicht getauscht.

Jetzt gucken wir uns die nächsten beiden Elemente an:
`[ 17 | 87 > 12 | 53 ]`
Da $87 \gt 12$, werden die beiden Elemente getauscht, und wir bekommen
`[ 17 | 12 | 87 | 53 ]`

Jetzt gucken wir uns die nächsten beiden Elemente an:
`[ 17 | 12 | 87 > 53 ]`
Wieder werden die beiden Elemente getauscht:
`[ 17 | 12 | 53 | 87 ]`

Jetzt ist der erste Durchlauf der äußeren Schleife fertig, da wir ein mal alle Elemente von vorne bis hinten durchgegangen sind. Der größte Wert liegt jetzt hinten.

**2. Durchlauf:**
Jetzt ignorieren wir das letzte Element:
`[ 17 | 12 | 53 ] 87 |`

Zuerst gucken wir uns die ersten beiden Elemente an:
`[ 17 > 12 | 53 ] 87 |`
Da $17 \gt 12$, werden die beiden Elemente getauscht:
`[ 12 | 17 | 53 ] 87 |`

Jetzt die nächsten beiden Elemente:
`[ 12 | 17 !> 53 ] 87 |`
Da 17 kleiner ist, werden sie nicht getauscht

Jetzt ist der erste Durchlauf der äußeren Schleife fertig, da wir ein mal alle Elemente von vorne bis hinten durchgegangen sind. Der zweitgrößte Wert liegt jetzt an der vorletzten Stelle.

**3. Durchlauf:**
Jetzt ignorieren wir die letzten beiden Elemente:
`[ 12 | 17 ] 53 | 87 |`

Wir vergleichen die ersten beiden Elemente:
`[ 12 !> 17 ] 53 | 87 |`
Da 12 kleiner ist, bleibt das Array gleich

**Ende:**
Der Algorithmus terminiert, sobald das Teilarray, dass wir uns angucken würden, nur noch 1 Element groß ist, also nach dem 3. Durchlauf.
Also sieht das Array am Ende so aus:
`| 12 | 17 | 53 | 87 |`