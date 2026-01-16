---
tags:
  - foliensatz/04
  - cleaned
aliases:
  - B-Baum
---

## B-Baum

Ein B-Baum (vom Grad $t$) ist ein Baum, bei dem
1. Jeder Knoten (außer der Wurzel) zwischen $t-1$ und $2t-1$ Werte `key[0]`, `key[1]`, ... hat und die Wurzel zwischen $1$ und $2t-1$
2. Die Werte innerhalb eines Knoten aufsteigend geordnet sind
3. Die Blätter alle die gleiche Höhe haben
4. Jeder innere Knoten mit $m$ Werten $m+1$ Kinder hat, sodass für alle Werte $k_j$ aus dem $j$-ten Kind gilt:
   $k_0 \leq$ `key[0]` $\leq k_1 \leq$   `key[1]` $\leq \ldots \leq k_{m-1} \leq$ `key[m-1]` $\leq k_m$

![[aud_folien_04_advanced_data_structures.pdf#page=113|aud_folien_04_advanced_data_structures, page 113]]

## Darstellung

![[aud_folien_04_advanced_data_structures.pdf#page=114|aud_folien_04_advanced_data_structures, page 114]]

`x.m` 
	Anzahl Werte eines Knoten `x`
`x.key[0]`, ..., `x.key[x.m-1]`
	(geordnete) Werte in Knoten `x`
`x.child[0]`, ..., `x.child[x.m]`
	Zeiger auf Kinder in Knoten `x`

## Höhe B-Baum

Wir haben mindestens 1 Wert in der Wurzel
Und mindestens 2 Knoten in Tiefe 1 mit jeweils $t$ Kindern
Mindestens $2^t$ Knoten in nächster Tiefe mit jeweils mindestens $t$ Kindern
Mindestens $2t^2$ Knoten in nächster Tiefe mit jeweils mindestens $t$ Kindern
Mindestens $2t^3$ Knoten in nächster Tiefe mit jeweils mindestens $t$ Kindern, usw.

Und in jedem Knoten außer der Wurzel mindestens $t-1$ Werte

Also erhalten wir folgende Anzahl Werte im B-Baum im Vergleich zu Höhe $h$:
$$n \geq 1 + (t-1) \cdot \sum_{i=1}^h2t^{i-1} = 1 + 2(t-1) \cdot \frac{t^h-1}{t-1} = 2t^h-1 \Rightarrow \log_t \frac{n+1}{2} \geq h$$

Ein B-Baum vom Grad $t$ mit $n$ Werten hat also eine maximale Höhe $h \leq \log_t \frac{n+1}{2}$
Also ist der B-Baum für größere Werte $t$ "flacher" als ein vollständiger Binärbaum

## Suche

Um einen Wert zu suchen, fangen wir wieder in der Wurzel an. Dann gehen wir die Werte der Wurzel durch, bis wir einen größerem Wert finden. Wir steigen in das linke Kind dieses Wertes und fangen dort wieder von vorne an. Das geht so lange, bis wir auf den gesuchten Wert stoßen.

![[aud_folien_04_advanced_data_structures.pdf#page=118|aud_folien_04_advanced_data_structures, page 118]]

## Baumkunde

![[aud_folien_04_advanced_data_structures.pdf#page=119|aud_folien_04_advanced_data_structures, page 119]]

## Einfügen

### Idee

Wir durchsuchen den Baum von oben nach unten nach einem Blatt in dem der Wert reinpasst. Wenn das Blatt weniger als $2t-1$ Werte hat, können wir einfügen. Ansonsten müssen wir den Baum erst umsortieren, weil das Blatt nach dem Einfügen sonst mehr als die erlaubte Anzahl Werte hätte.

![[aud_folien_04_advanced_data_structures.pdf#page=121|aud_folien_04_advanced_data_structures, page 121]]

#### Splitten

Wir betrachten beispielhaft einen Baum mit einem Grad $t = 2$.

Wenn das Blatt bereits $2t-1$ Werte hat, dann
1. teile das Blatt in zwei Blätter mit je $t-1$ Werten und füge den mittleren Wert im Elternknoten ein
2. Füge den neuen Wert ein
Wenn dadurch der Elternknoten mehr als $2t-1$ Werte hat, verfahre rekursiv nach oben

![[aud_folien_04_advanced_data_structures.pdf#page=122|aud_folien_04_advanced_data_structures, page 122]]

##### An Der Wurzel Splitten

Der Split an der Wurzel erzeugt eine neue Wurzel, und die Höhe des Baumes wächst um 1

![[aud_folien_04_advanced_data_structures.pdf#page=123|aud_folien_04_advanced_data_structures, page 123]]

### Suchen, Dann Splitten vs. Suchen Und Splitten

Wenn wir erst suchen, und dann splitten, werden teure Disk-Operationen zweimal ausgeführt, einmal beim Absteigen und einmal beim Aufsteigen
Das können wir verhindern, indem wir beim Suchen schon splitten (wir laufen also nur einmal herab)

![[aud_folien_04_advanced_data_structures.pdf#page=124|aud_folien_04_advanced_data_structures, page 124]]

## Vorgehensweise

Wir gehen von oben nach unten durch den Baum und suchen ein Blatt, in das der Wert kann. Besuchen wir dabei einen Knoten, der schon $2t-1$ Werte hat, splitten wir ihn, um zu verhindern, dass wir potentiell wieder den ganzen Baum nach oben traversieren müssen

![[aud_folien_04_advanced_data_structures.pdf#page=125|aud_folien_04_advanced_data_structures, page 125]]

## Löschen

### Im Blatt

#### Volles Blatt

Wenn das Blatt in dem der zu löschende Wert ist noch mehr als $t-1$ Werte hat, kann man den Wert einfach entfernen

![[aud_folien_04_advanced_data_structures.pdf#page=126|aud_folien_04_advanced_data_structures, page 126]]

#### "Zu leeres" Blatt

Hat das Blatt, in dem der zu löschende Wert ist genau $t-1$ Werte, dann kann man den Wert nicht einfach entfernen, da er dann zu wenige Werte hätte.

##### Rotieren

Wenn der linke oder rechte Geschwisterknoten mindestens $t$ Werte hat, können wir einen Wert von dem Geschwisterknoten "klauen", indem wir ihn in das Blatt rotieren

![[aud_folien_04_advanced_data_structures.pdf#page=127|aud_folien_04_advanced_data_structures, page 127]]

##### Verschmelzen

Wenn der Geschwisterknoten des Blatts nicht mindestens $t-1$ Werte hat, dann können wir den Geschwisterknoten mit dem Blatt und mit einem Wert aus dem Elternknoten verschmelzen
Eventuell hat jetzt aber der Elternknoten zu wenig Werte

![[aud_folien_04_advanced_data_structures.pdf#page=128|aud_folien_04_advanced_data_structures, page 128]]

### Innerer Knoten

#### Verschieben

Wenn einer der beiden Kinder mehr als $t-1$ Werte hat, dann kopiere den größten Wert (vom linken Kind) bzw. den kleinsten Wert (vom rechten Kind) nach oben

![[aud_folien_04_advanced_data_structures.pdf#page=130|aud_folien_04_advanced_data_structures, page 130]]

#### Verschmelzen

Wenn beide Kinder jeweils $t-1$ Werte haben, dann verschmelze die beiden und lösche den Wert
Eventuell hat der Elternknoten nun zu wenig Werte

![[aud_folien_04_advanced_data_structures.pdf#page=130|aud_folien_04_advanced_data_structures, page 130]]

### Löschen Und Splitten

B-Baum-Löschen läuft auch nur einmal hinab
Stelle dazu sicher, dass das zu besuchende Kind mindestens $t$ Werte hat

![[aud_folien_04_advanced_data_structures.pdf#page=131|aud_folien_04_advanced_data_structures, page 131]]

### Allgemeines Verschmelzen

Wenn das zu besuchende Kind und der rechte und linke Geschwisterknoten nur $t-1$ Werte haben
Wenn der Elternknoten vorher mindestens $t$ Werte hat, dann ist keine Änderung oberhalb nötig

![[aud_folien_04_advanced_data_structures.pdf#page=132|aud_folien_04_advanced_data_structures, page 132]]

### Allgemeines Rotieren/Verschieben

Wenn das zu besuchende Kind nur $t-1$ Werte hat, aber ein Geschwisterknoten mehr als $t-1$ Werte
Keine Änderung oberhalb nötig

![[aud_folien_04_advanced_data_structures.pdf#page=133|aud_folien_04_advanced_data_structures, page 133]]

### Vorgehensweise

Wir traversieren den Baum von oben nach unten, bis wir den zu löschenden Wert finden.
Dabei überprüfen wir, dass die Wurzel mehr als einen Wert und alle anderen besuchten Knoten mehr als $t-1$ Werte haben, damit wir am Ende problemlos löschen können

![[aud_folien_04_advanced_data_structures.pdf#page=134|aud_folien_04_advanced_data_structures, page 134]]

## Laufzeiten

| Operation | Laufzeit           |
| --------- | ------------------ |
| Einfügen  | $\Theta(\log_t n)$ |
| Löschen   | $\Theta(\log_t n)$ |
| Suchen    | $\Theta(\log_t n)$ |

Achtung: die $\mathcal{O}$-Notation versteckt den (konstanten) Faktor $t$ für die Suche innerhalb eines Knotens;
$t \cdot \log_t n = t \cdot \frac{\log_2 n}{\log_2 t}$ ist in der Regel größer als $\log_2 n$, also in der Regel nur vorteilhaft, wenn Daten blockweise eingelesen werden