---
tags:
  - foliensatz/07
  - cleaned
aliases:
  - FFT
  - Fast Fourier Transformation
  - Fast-Fourier-Transformation
  - Fast Fourier
  - Fast-Fourier
  - Fourier Transformation
  - Fourier-Transformation
---

## Idee Der Fourier-Transformation

Die Idee hinter der Fourier-Transformation ist, dass wir ein Problem in der Darstellung X haben und eine Lösung in der Darstellung X haben wollen.
Unter Umständen ist es dann schneller, das Problem in ein Problem in Darstellung Y umzuwandeln, daraus eine Lösung in Darstellung Y zu berechnen und die Lösung in eine Lösung in Darstellung X umzuwandeln.

Nehmen wir an, das Problem in Darstellung X hat eine Komplexität $T = \Omega(n^2)$, die Umwandlung von X zu Y sowie von Y zu X (FFT und inverse FFT) finden in $\mathcal{O}(n \log n)$ Schritten per [[Divide & Conquer]] statt, und dass das Problem in Darstellung Y auf einmal nur noch eine Komplexität von $\mathcal{O}(n)$ hat. In diesem Fall würde sich eine Fourier-Transformation lohnen.

![[aud_folien_07_advanced_designs.pdf#page=4|aud_folien_07a_advanced_designs, page 4]]

## Fourier-Transformation

Zum Beispiel kann die Fourier-Transformation benutzt werden, um die [[Polynome|Polynom]]-Multiplikation zu verschnellern, indem wir die Polynome in Punkt/Wert-Darstellung umwandeln.
Die Umwandlung braucht per FFT $\Theta(n \log n)$ Schritte, die Berechnung in Punkt/Wert-Darstellung nur $\Theta(n)$ Schritte und die Umwandlung der Lösung per IFFT wieder nur $\Theta(n \log n)$ Schritte, sodass wir eine Gesamtzeit von $\Theta(n \log n)$ statt $\Theta(n^2)$ Schritten haben.

## Diskrete Fourier-Transformation Berechnen

Das Problem bei der Umrechnung von Koeffizienten-Darstellung zu Punkt/Wert-Darstellung ist, dass die Auswertung des Polynoms für jedes der $2n-1$ Punkt/Wert-Paare die wir benötigen $\Theta(n)$ Schritte benötigt.
Der Gesamtaufwand für alle $2n-1$ Punkte wäre also $\Theta(n^2)$!
Die Lösung ist, spezielle Werte $x_j$ zu verwenden, sodass die Punkt/Wert-Paare schneller per [[Divide & Conquer]] berechenbar sind

Wir schreiben $p(x)$ in folgender Form (für gerade $n$):
$p(x) = p_{\text{even}}(x^2) + x \cdot p_{\text{odd}}(x^2)$
wobei
$p_{\text{even}}(x) = p_0 + p_2x + \ldots + p_{n-2}x^{(n-2)/2}$
$p_{\text{odd}}(x) = p_1 + p_3x + \ldots + p_{n-1}x^{(n-2)/2}$

$p_{\text{even}}$ und $p_{\text{odd}}$ sind also Polynome von ca. halbem Grad - aber es sind leider immer noch $2n-1$ Punkte $x_j$ nötig.
Wir haben also noch nicht (ganz) ein Problem halber Größe, um Divide & Conquer anzuwenden

Jetzt können wir aber Werte $x_j$ verwenden, sodass $x^2_j = x^2_{j+n}$ für alle $j = 0, 1, \ldots, n-1$ (aber immer noch $x_j \neq x_{j+n}$)
Dann müssen $p_{\text{even}}, p_{\text{odd}}$ vom Grad $\frac{n-2}{2} = \frac{n}{2}-1$ nur an $n$ Stellen $x_0^2, x_1^2, \ldots, x_{n-1}^2$ ausgewertet werden
Problemgröße halbiert $\Rightarrow$ Divide & Conquer anwendbar

## FFT - Algorithmen

Zuerst definieren wir einen Wrapper, der für rekursive Aufrufe die aktuelle primitive [[m-te Primitive Einheitswurzeln|Einheitswurzel]] hinzufügt:

![[aud_folien_07_advanced_designs.pdf#page=16|aud_folien_07_advanced_designs, page 16]]

Zur Vereinfachung bestimmen wir $2n$ (statt $2n-1$) Punkt-Werte-Paare, sodass jeweils $n$ Einträge im Array `p[]` und jeweils doppelt so viele Punkt-Werte-Paare berechnet werden
Wir benötigen, dass $n$ eine Zweierpotenz ist, das erreichen wir notfalls, indem wir $n$ maximal verdoppeln und die zusätzlichen Einträge im Array `p[]` auf 0 setzen

(Der Übergang $n \rightarrow 2n$ wird später in der asymptotischen Laufzeit nicht ins Gewicht fallen)

![[aud_folien_07_advanced_designs.pdf#page=17|aud_folien_07_advanced_designs, page 17]]

Zeilenweise Erklärung:

Z1: Erstelle jeweils ein Array (mit Länge $n/2$) für die geraden und ungeraden Koeffizienten des [[Polynome|Polynoms]]
Z2: Erstelle ein Array für die $y$-Werte des Polynoms (der Länge $2n$), sowie ein Array für die geraden und ungeraden Werte (jeweils Länge $n$)
Z3: Erstelle ein Array der Länge $2n$ für die $x$-Werte des Polynoms, setze den ersten Eintrag auf $1$
Z4: Gehe alle Punkt-Wert-Paare durch und setze $\texttt{x[j]} = w \cdot \texttt{x[j-1]}$ (also $\texttt{x[j]} = w^j$), wobei $w$ die gegebene $2n$-te primitive [[m-te Primitive Einheitswurzeln|Einheitswurzel]] ist

Z5: Falls $n=1$ handelt es sich um ein konstantes Polynom. Dann ist die Berechnung einfacher:
	Z6: Den $x$-Wert des ersten Punkt-Wert-Paares setzen wir auf 1, den $y$-Wert des ersten Punkts auf die Konstante des Polynoms
	Z7: Den $x$-Wert des zweiten Punkt-Wert-Paares setzen wir auf den nächsten $x$-Wert, den $y$-Wert wieder auf die Konstante des Polynoms
Z8: Ansonsten:
	Z9: Für alle $\texttt{j}$ von $0$ bis $(n-2)/2$:
		Z10: Speichere den Koeffizienten an der Stelle $2j$ im Array mit den geraden Koeffizienten und den Koeffizienten an der Stelle $2j+1$ im Array mit den ungerade Koeffizienten
	Z11:  Berechne mithilfe eines rekursiven Aufrufs die Werte für die Koeffizienten an den geraden Stellen (wobei $\omega^2$ als primitive Einheitswurzel durchgegeben wird)
	Z12: Berechne mithilfe eines rekursiven Aufrufs die Werte für die Koeffizienten an den ungeraden Stellen (wobei wieder $\omega^2$ als primitive Einheitswurzel durchgegeben wird)
	Z13: Für alle $\texttt{j}$ von $0$ bis $(n-2)/2$:
		Z14: Setze den $x$-Wert an der Stelle $j$ auf den Anfangs berechneten $x$-Wert $\texttt{x[j]}$
		Z15: Setze den $y$-Wert an der Stelle $j$ auf 
		den $y$-Wert des Punkt-Wert-Arrays der geraden Koeffizienten an der Stelle $j \mod n$ (da es nur halb so lang ist) 
		plus den $y$-Wert des Punkt-Wert-Arrays der ungeraden Koeffizienten an der Stelle $j \mod n$ 
		mal den Wert $\texttt{x[j]}$
Z16: Gebe das Punkt-Wert-Array wieder

### Beispiel

Am Anfang haben wir ein Array $\texttt{p[]}$ an Koeffizienten, den Grad des Polynoms und die $2n$-te primitive Einheitswurzel $\omega_8$ gegeben.
Zuerst berechnen wir mithilfe von $\omega_8$ 8 verschiedene $x$-Werte und speichern sie in $\texttt{x[]}$.
Dann berechnen wir mithilfe eines rekursiven Aufrufs die Punkt-Wert-Paare für die Koeffizienten an den geraden Stellen. Als primitive Einheitswurzel geben wir $\omega_8^2$ weiter. 
Da dann immer noch zwei Koeffizienten übrig bleiben, wird $\texttt{FFT}$ noch ein zweites Mal verschachtelt rekursiv aufgerufen, dieses mal mit der primitiven Einheitswurzel $\omega_8^4$. 
Da hier nur noch ein Koeffizient übrig bleibt, tritt der Rekursionsanker ein. Es werden zwei Punkt-Wert-Paare wiedergegeben - einmal (1, 5) und einmal $(\omega_8^4, 5)$, da $\omega_8^4$ die durchgereichte Einheitswurzel für den Koeffizienten $5$ war.

![[aud_folien_07_advanced_designs.pdf#page=18|aud_folien_07_advanced_designs, page 18]]

Der Wert des zweiten Koeffizienten im ersten rekursiven Aufruf wird dann als Koeffizient an einer ungeraden Stelle berechnet. Dementsprechend werden die Punkt-Wert-Paare $(1, -1)$ und $(\omega_8^4, -1)$ wiedergegeben, da $\omega_8^4$ die durchgereichte Einheitswurzel war und $-1$ der Koeffizient war.

![[aud_folien_07_advanced_designs.pdf#page=19|aud_folien_07_advanced_designs, page 19]]

Die Punkt-Wert-Paare für die beiden Koeffizienten werden dann genutzt, um Punkt-Wert-Paare für das $\texttt{pVal[]}$-Array zu berechnen. Diese werden dann wiedergegeben und sind für den ersten Aufruf der Methode die $\texttt{pEvenVal[]}$-Werte

![[aud_folien_07_advanced_designs.pdf#page=20|aud_folien_07_advanced_designs, page 20]]

Ebenso wird im ersten Aufruf der Methode mit den Werten für $\texttt{pOddVal[]}$ verfahren. Die Werte aus $\texttt{pEvenVal}$ und $\texttt{pOddVal}$ werden dann wieder benutzt, um $\texttt{pVal}$ zu füllen, welches dann als endgültiges Punkt-Wert-Array wiedergegeben wird:

![[aud_folien_07_advanced_designs.pdf#page=21|aud_folien_07_advanced_designs, page 21]]

### Laufzeit

Da wir einen rekursiven Aufruf mit halbierten $n$ haben, erhalten wir eine Laufzeit $\Theta(n \log n)$

![[aud_folien_07_advanced_designs.pdf#page=22|aud_folien_07_advanced_designs, page 22]]

## Inverse DFT Berechnen

Gegeben die $2n$ Punkt-Wert-Paare, können wir die Koeffizienten durch eine inverse Matrix $V$ berechnen:

![[aud_folien_07_advanced_designs.pdf#page=24|aud_folien_07_advanced_designs, page 24]]

![[aud_folien_07_advanced_designs.pdf#page=25|aud_folien_07_advanced_designs, page 25]]

![[aud_folien_07_advanced_designs.pdf#page=26|aud_folien_07_advanced_designs, page 26]]

Erklärung:
Dieses Mal haben wir für ein $k$ ein $2^k$ langes Array an Punkt-Wert-Paaren gegeben und wollen daraus die Koeffizientendarstellung bestimmen.

In der Wrapper-Funktion wird in Zeile 1 $\texttt{IFFT}$ aufgerufen, um aus den Punkt-Wert-Paaren die Koeffizienten zu bestimmen. Dann werden alle Koeffizienten durchgegangen und durch $n$ geteilt, bevor das Array wiedergegeben wird.

Zeilenweise Erklärung der $\texttt{IFFT}$-Funktion:
Z1: Erstelle drei Arrays der Länge $n$ für die Koeffizienten, für die Punkt-Wert-Paare der Koeffizienten an den geraden Stellen und die Koeffizienten der ungeraden Werte
Z2: Erstelle ein Array der Länge $n$ für die $x$-Werte und setze den ersten Eintrag auf $1$
Z3: Berechne alle $x$-Werte (wie in FFT mit $\texttt{x[j]} = w^j$)
Z4: Wenn $\texttt{n==1}$ handelt es sich um ein konstantes Polynom:
	Z5: und wir können den ersten Koeffizienten auf den $y$-Wert des Polynoms setzen
Z6: Ansonsten:
	Z7: Erstelle zwei Arrays der Länge $n/2$, eins für die Koeffizienten an den geraden Stellen und eins für die Koeffizienten an den ungeraden Stellen
	Z8: Für alle $j$ von $j=0$ zu $j=(n-2)/2$
		Z9: Speichere die Werte an geraden Stellen in $\texttt{rEvenVal}$ und die Werte an ungeraden Stellen in $\texttt{rOddVal}$
	Z10: Berechne mithilfe eines rekursiven Aufrufs die Koeffizienten für die Werte an den geraden Stellen
	Z11: Berechne mithilfe eines rekursiven Aufrufs die Koeffizienten für die Werte an den ungeraden Stellen
	Z12: Für alle $j$ von $j=0$ bis $j=n-1$:
		Z13: Berechne den Koeffizienten an der Stelle $j$ als $\texttt{rEven[j mod n/2] + rOdd[j mod n/2]/x[j]}$
Z14: Gebe das Array der Koeffizienten wieder

### Beispiel

Am Anfang haben wir ein Array an Punkt-Wert-Paaren gegeben, sowie den Grad $n=4$ des Polynoms und die $n$-te primitive [[m-te Primitive Einheitswurzeln|Einheitswurzel]] $\omega_4$.
Wir speichern in $\texttt{x[]}$ die $x$-Werte des Polynoms und versuchen dann mithilfe eines rekursiven Aufrufs die Koeffizienten der Werte an den geraden Stellen zu berechnen.
Da das Punkt-Wert-Array im rekursiven Aufruf immer noch mehr als einen Wert hat, wird die Methode nochmal verschachtelt rekursiv aufgerufen.
Dieses Mal hat das Punkt-Wert-Array nur einen Wert, und der Aufruf gibt $7$ wieder, da das der $y$-Wert an der Stelle ist.

![[aud_folien_07_advanced_designs.pdf#page=27|aud_folien_07_advanced_designs, page 27]]

Im rekursiven Aufruf wird der Koeffizient des zweiten Paars dann als Koeffizient an einer ungeraden Stelle berechnet, und wir erhalten $1$:

![[aud_folien_07_advanced_designs.pdf#page=28|aud_folien_07_advanced_designs, page 28]]

Aus den Ergebnissen der rekursiven Aufrufe berechnen wir dann das Array der Koeffizienten, welches wir wiedergeben:

![[aud_folien_07_advanced_designs.pdf#page=29|aud_folien_07_advanced_designs, page 29]]

Ebenso verfahren wir mit den restlichen Werten:

![[aud_folien_07_advanced_designs.pdf#page=30|aud_folien_07_advanced_designs, page 30]]

![[aud_folien_07_advanced_designs.pdf#page=31|aud_folien_07_advanced_designs, page 31]]

![[aud_folien_07_advanced_designs.pdf#page=32|aud_folien_07_advanced_designs, page 32]]

Und nachdem wir alle Werte erhalten haben, können wir das endgültige Array der Koeffizienten berechnen:

![[aud_folien_07_advanced_designs.pdf#page=33|aud_folien_07_advanced_designs, page 33]]

