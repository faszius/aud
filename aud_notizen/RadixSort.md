---
tags:
  - foliensatz/02/e
  - cleaned
---

## Ansatz

Schlüssel sind $d$-stellige Werte in einem Zahlensystem zur Basis $D$

![[aud_folien_02de_sorting.pdf#page=25|aud_folien_02de_sorting, page 25]]

"Buckets" erlauben Einfügen und dann Entnehmen (in eingefügter Reihenfolge) in konstanter Zeit

## Vorgehen

### Erste Iteration

Gehe Array von links nach rechts durch und füge Werte entsprechend kleinstwertigster Ziffer in Bucket ein

![[aud_folien_02de_sorting.pdf#page=26|aud_folien_02de_sorting, page 26]]

Gehe Buckets von links nach rechts durch, entnimm Werte und füge Werte an nächster Stelle im Array ein:

![[aud_folien_02de_sorting.pdf#page=27|aud_folien_02de_sorting, page 27]]

### Zweite Iteration

![[aud_folien_02de_sorting.pdf#page=28|aud_folien_02de_sorting, page 28]]

![[aud_folien_02de_sorting.pdf#page=29|aud_folien_02de_sorting, page 29]]

### Dritte Iteration

![[aud_folien_02de_sorting.pdf#page=30|aud_folien_02de_sorting, page 30]]

![[aud_folien_02de_sorting.pdf#page=31|aud_folien_02de_sorting, page 31]]

## Algorithmus

![[aud_folien_02de_sorting.pdf#page=32|aud_folien_02de_sorting, page 32]]

### Zeilenweise Erklärung `radixSort`

1. Von der minderwertigsten bis zur höchstwertigsten Stelle
	1. Für jede Zahl, tue sie in den Bucket der zur Ziffer an dieser Stelle passt
	2. Setze den Index <font color="aquamarine">a</font> zum Schreiben des neuen Arrays <font color="lime">A</font> auf 0
	3. Von dem kleinstwertigsten bis zum höchstwertigsten Bucket 
		1. Vom ersten bis zum letzten Element des Buckets
			1. Setze <font color="lime">A</font>\[<font color="aquamarine">a</font>\] auf das Element des Buckets
			2. Erhöhe **<font color="aquamarine">a</font> um eins
		2. Lösche den Inhalt des Buckets
2. Gebe <font color="lime">A</font> wieder

Hierbei gilt dass $d$ die Länge der längsten Zahl ist
Und $D$ die Basis der Zahlen/der Zifferbereich ist

### Zeilenweise Erklärung `putBucket`

- A ist das Array von allen Zahlen
- B ist das Array von Buckets (die wiederum auch als Arrays dargestellt werden)
- i ist der Index der Ziffer, die wir uns gerade angucken (z.B. erste Ziffer, zweite Ziffer, etc...)
- j ist der Index der Zahl aus A die wir uns gerade angucken

1. Setze z auf die Ziffer i der Zahl j
2. Setze b auf die Länge des Buckets für z
3. Setze Element b des Buckets z auf die Zahl j
4. Vergrößere Bucket z um eins

## Korrektheit

### Schleifeninvariante

Nach i-ter Iteration ist Array gemäß letzten i Ziffern sortiert

### Induktionsanfang $i=1$

Gilt nach erster Iteration, weil nach letzter Ziffer sortiert wird

### Induktionsschritt $i \rightarrow i+1$

 Fall 1:

Wenn (i+1)-te Ziffer zweier beliebiger Werte verschieden, dann wird Wert mit kleinerer (i+1)-ten Ziffer weiter vorne einsortiert, zuerst wieder ausgelesen und steht somit auch im Array vorher

Fall 2:

Wenn (i+1)-te Ziffer gleich, dann steht nach Induktionsvoraussetzung der auf den letzten i Ziffern kleinere Wert weiter links, wird zuerst einsortiert und auch zuerst wieder ausgelesen

## Laufzeit

![[aud_folien_02de_sorting.pdf#page=36|aud_folien_02de_sorting, page 36]]

Gesamtlaufzeit von $\mathcal{O}(d \cdot (n + D))$

### Interpretation

Die Größe des Ziffernbereichs $D$ wird oft als konstant angesehen: 
Laufzeit $\mathcal{O}(dn)$

Wenn auch $d$ als konstant angesehen wird (also die Länge der längsten Zahl): 
Laufzeit $\mathcal{O}(n)$

Aber: eindeutige Schlüssel für $n$ Elemente benötigen $d = \Theta(\log_D n)$ Ziffern, sodass die Laufzeit doch von der Länge des Arrays abhängt:
Laufzeit $\mathcal{O}(n \cdot \log n)$

