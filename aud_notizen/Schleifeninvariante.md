---
tags:
  - cleaned
---

Eine Schleifeninvariante ist eine Aussage über eine Schleife, die *vor* jedem Eintritt in die Schleife wahr sein muss. Sie bezieht sich dabei fast immer auf den Zählerwert `i` vor Eintritt in die Schleife:
"Vor dem `i`-ten Durchlauf der for-Schleife gilt \[Aussage die `i` beinhaltet\]"

Im Idealfall ist die Schleifeninvariante so formuliert, dass wir nach dem aller letzten Durchlauf für `i=n-1`, bzw. vor dem *theoretischen* $n$-ten Durchlauf der Schleife (der jedoch nie praktisch stattfindet), wenn wir `i=n` in die Schleifeninvariante einsetzen, die Aussage erhalten, dass unser Algorithmus das tut, was er machen soll - also zum Beispiel dass alle Elemente von `A[0]` bis `A[n-1]` sortiert sind oder das `min` das Minimum aller Elemente von `A[0]` bis `A[n-1]` ist.
Analoges gilt für Algorithmen, die `i` runter- statt hochzählen, nur dass man dann ein anderes `i` einsetzen muss.

## Beispiele

Beispiele für so eine Schleifeninvariante könnten sein:

Für einen Algorithmus, der den kleinsten Wert in einem Array finden soll:
```
len = length(A) 
min = A[0]
for i = 1 to len − 1 do
	if A[i] < min then 
		min = A[i] 
return min
```
"Vor dem i-ten Durchlauf der for-Schleife ist min das Minimum der Elemente in `A[0], ..., A[i − 1]`"
Setzen wir $i=n$ in die Aussage ein, erhalten wir:
"Vor dem i-ten Durchlauf der for-Schleife ist min das Minimum der Elemente in `A[0], ..., A[n − 1]`", was genau das ist, was unser Algorithmus machen soll

Für einen Algorithmus, der die Summe aller Werte in einem Array finden soll:
```
len = length(A)
sum = A[0]
for i = 1 to len − 1 do
	sum = sum + A[i]
return sum
```
"Vor dem i-ten Durchlauf der for-Schleife ist sum die Summe der Elemente in `A[0], ..., A[i − 1]`"
Setzen wir $i=n$ in die Aussage ein, erhalten wir:
"Vor dem i-ten Durchlauf der for-Schleife ist sum die Summe der Elemente in `A[0], ..., A[n − 1]`"

## Korrektheitsbeweis

Haben wir eine Aussage über unsere Schleife gefunden, die für `i=n` sagt, dass unser Algorithmus das macht, was er machen soll, müssen wir nur noch beweisen, dass die Aussage tatsächlich stimmt. Das machen wir per Induktion, diese besteht aus dem Basisfall, dem Induktionsschritt und in diesem Fall der Terminierung.
Im Basisfall beweisen wir, dass die Aussage vor dem ersten Durchlauf gilt.
Im Induktionsschritt gehen wir davon aus, dass die Aussage für `i` gilt. Dann gehen wir den Algorithmus Schritt für Schritt durch und beweisen, dass die Aussage danach auch für `i=i+1` gilt (bzw. `i=i-1`, wenn der Algorithmus runterzählt).
Und zu guter Letzt gucken wir uns bei der Terminierung an, was für eine Aussage wir nach dem letzten Durchlauf erhalten.