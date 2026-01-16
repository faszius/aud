---
tags:
  - foliensatz/07
  - cleaned
aliases:
  - Levenschtein
  - Levenschtein-Distanz
  - Minimum-Edit Distance
  - Minimum-Edit-Distance
  - Minimum Edit-Distance
  - Edit-Distance
  - Edit Distance
---

## Minimum Edit Distance

Die Minimum Edit Distance (Levenschtein-Distanz) misst die Ähnlichkeit von Texten: wie viele (Buchstaben-)Operationen benötigen wir, um einen Text in einen anderen umzuwandeln?
Wir haben dabei drei Operationen:
`ins(S, i, b)`
	fügt an `i`-ter Position den Buchstaben `b` in den String `S` ein
`del(S, i)`
	löscht den Buchstaben an `i`-ter Position in String `S`
`sub(S, i, b)` 
	ersetzt den Buchstaben an `i`-ter Position in String `S` durch `b`

![[aud_folien_07_advanced_designs.pdf#page=55|aud_folien_07_advanced_designs, page 55]]

Eine Herangehensweise wäre, den String `X[1...m]` schrittweise von links nach rechts in den String `Y[1...n]` zu überführen, sodass immer jeweils der Teil `X[1...i]` bereits in den Teil `Y[1...j]` überführt wird.
Das Zeigen der Optimalität dieser Herangehensweise wird an dieser Stelle ausgelassen.

![[aud_folien_07_advanced_designs.pdf#page=56|aud_folien_07_advanced_designs, page 56]]

Sei `D[i][j]` die Distanz, um `X[1...i]` in `Y[1...j]` zu überführen (wobei $i, j >= 1$). Dann erhalten wir für die einzelnen Operationen folgende Kosten:

`copy`
	`D[i][j]` = `D[i-1][j-1]`
`sub`
	`D[i][j]` = `D[i-1][j-1]+1`
`del`
	`D[i][j]` = `D[i-1][j]+1`
`ins`
	`D[i][j]` = `D[i][j-1]+1`

![[aud_folien_07_advanced_designs.pdf#page=57|aud_folien_07_advanced_designs, page 57]]

Da wir die beste Ersetzungsstrategie suchen, ist `D[i][j]` gegeben durch jeweils das Minimum der vier Formeln

![[aud_folien_07_advanced_designs.pdf#page=59|aud_folien_07_advanced_designs, page 59]]

`D[i][j]` sei die Distanz, um `X[1...i]` in `Y[1...j]` zu überführen (mit $i, j \geq 1$)

Die "Randbedingungen" sind dabei:
`D[0][j]=j` - füge `j` Buchstaben `Y[1...j]` zum leeren String `X[1...0]` hinzu
`D[i][0]=i` - lösche `i` Buchstaben `X[1...i]` um den leeren String `Y[1...0]` zu erhalten

## Algorithmus

Der Algorithmus dafür sieht wie folgt aus:

![[aud_folien_07_advanced_designs.pdf#page=61|aud_folien_07_advanced_designs, page 61]]

### Zeilenweise Erklärung

Z1: Erstelle ein $m \times n$ großes Array 
Z2: Setze alle `D[i][0]=i`
Z3: Setze alle `D[0][j]=j`
Z4: Für alle `i` von `i=1` bis `i=m` (wobei `m` die Länge des zu modifizierenden Strings ist):
	Z5: Für alle `j` von `j=1` bis `j=n` (wobei `n` die Länge des zu modifizierenden Strings ist):
		Z6: Falls die beiden Ziffern gleich sind setze `s=0` sonst setze `s=1`
		Z7: Setze `D[i][j]` auf den kleinsten Wert aller möglichen Operationen
Z8: Gebe `D[m][n]` wieder

## Beispiel

Wir haben einen String X="ein Test" der in den String Y="zwei Feste" übersetzt werden soll. Dafür erstellen wir eine Tabelle, die so viele Zeilen enthält wie der String Y lang ist, und so viele Spalten wie der String X lang ist. Die erste Spalte und die erste Zeile werden jeweils mit den Indizes der Spalte/Zeile gefüllt.

![[aud_folien_07_advanced_designs.pdf#page=62|aud_folien_07_advanced_designs, page 62]]

Für das Feld `D[1][1]` bestimmen wir den Wert `s`, setzen ihn ein und gucken dann, welche Formel für die Operationen die kleinste Zahl ergibt und setzen sie in das Feld.

![[aud_folien_07_advanced_designs.pdf#page=63|aud_folien_07_advanced_designs, page 63]]

Das gleiche machen wir mit `D[1][2]`, wir vergleichen jetzt also den ersten Buchstaben von X mit dem zweiten Buchstaben von Y

![[aud_folien_07_advanced_designs.pdf#page=64|aud_folien_07_advanced_designs, page 64]]

![[aud_folien_07_advanced_designs.pdf#page=65|aud_folien_07_advanced_designs, page 65]]

Schließlich haben wir den ersten Buchstaben von `X` mit jedem Buchstaben von `Y` verglichen, und können dazu übergehen, den zweiten Buchstaben zu vergleichen:

![[aud_folien_07_advanced_designs.pdf#page=66|aud_folien_07_advanced_designs, page 66]]

Und irgendwann haben wir alle Buchstaben von `X` mit allen Buchstaben von `Y` verglichen:

![[aud_folien_07_advanced_designs.pdf#page=67|aud_folien_07_advanced_designs, page 67]]

Jetzt können wir von unten rechts anfangen und uns immer nach oben, oben links oder links zum Feld mit dem kleinsten Wert bewegen. So erreichen wir irgendwann den Anfangspunkt oben links. Den Pfad, den wir genommen haben, gibt uns dann an, in welcher Reihenfolge wir welche Operationen durchführen müssen

![[aud_folien_07_advanced_designs.pdf#page=68|aud_folien_07_advanced_designs, page 68]]

Führen wir die Operationen wie angegeben aus, sieht das ganze dann so aus:

![[aud_folien_07_advanced_designs.pdf#page=69|aud_folien_07_advanced_designs, page 69]]