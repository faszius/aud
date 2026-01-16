---
tags:
  - foliensatz/04
  - cleaned
aliases:
  - Rot-Schwarz-Baum
  - RSB
---

## Rot-Schwarz-Bäume

![[aud_folien_04_advanced_data_structures.pdf#page=7|aud_folien_04_advanced_data_structures, page 7]]

Ein Rot-Schwarz-Baum ist ein [[Binäre Suchbäume|binärer Suchbaum]], sodass gilt:
1. Jeder Knoten hat die Farbe rot oder schwarz
2. Die Wurzel ist schwarz (sofern der Baum nicht leer ist)
3. Wenn ein Knoten rot ist, sind seine Kinder schwarz ("Nicht-Rot-Rot"-Regel)
4. Für jeden Knoten hat jeder Pfad im Teilbaum zu einem Blatt oder Halbblatt die gleiche Anzahl von schwarzen Knoten ("gleiche Anzahl schwarz")

![[aud_folien_04_advanced_data_structures.pdf#page=8|aud_folien_04_advanced_data_structures, page 8]]

Daraus folgt: Halbblätter in Rot-Schwarz-Bäumen sind schwarz

## "Schwarzhöhe" Eines Knoten

![[aud_folien_04_advanced_data_structures.pdf#page=9|aud_folien_04_advanced_data_structures, page 9]]

Die Schwarzhöhe eines Knoten `x` ist die (eindeutige) Anzahl von schwarzen Knoten auf dem Weg zu einem Blatt oder Halbblatt im Teilbaum des Knoten, wobei $\text{SH}(nil) = 0$

## Höhe Eines Rot-Schwarz-Baums

Ein Rot-Schwarz-Baum mit $n$ Knoten hat maximale Höhe $h \leq 2 \cdot \log_2 (n+1)$.

### Intuition

Intuition:
1. In jedem Unterteilbaum gibt es die gleiche Anzahl schwarzer Knoten auf jedem Pfad
2. Es gibt maximal zusätzlich die gleiche Anzahl roter Knoten auf diesem Pfad
3. Daher einigermaßen ausbalanciert und Höhe $\mathcal{O}(\log n)$

### Formaler Beweis

Ein Teilbaum in Knoten $x$ hat mindestens $2^{\text{SH}(x)}-1$ Knoten:
Ein leerer Baum hat $n = 0$ Knoten und mind. $2^{\text{SH}(x)}-1 = 2^0-1 = 0$ Knoten.
Teilbäume haben Schwarzhöhe $\text{SH}(x)$ oder $\text{SH}(x)-1$, je nachdem ob `x` rot oder schwarz.
Also jeweils mind. $2^{\text{SH}(x)-1}-1$ Knoten in Teilbäumen.
Insgesamt mindestens $(2^{\text{SH}(x)-1}-1)+(2^{\text{SH}(x)-1}-1)+1 = 2^{\text{SH}(x)}-1$ Knoten im Teilbaum von `x`.

Sei also $h$ die Höhe des Baumes mit Wurzel `r` und $n$ Knoten
Dann $\text{SH}(r) \geq h/2$, da maximal die Hälfte der Knoten auf dem längsten Pfad rot ist.
Dann $n \geq 2^{h/2}-1$ bzw. $\log_2(n+1) \geq h/2$.

## Implementierung Mittels Sentinel

![[aud_folien_04_advanced_data_structures.pdf#page=14|aud_folien_04_advanced_data_structures, page 14]]

Wir packen einen schwarzen Sentinel über die Wurzel: 
`T.root.parent = T.sent`, Elternknoten und Kinder des Sentinel sind der Sentinel selbst. Somit ist z.B. `x.parent.parent.left` immer wohldefiniert.

## Rotation

![[Rotation]]

## Einfügen

![[aud_folien_04_advanced_data_structures.pdf#page=21|aud_folien_04_advanced_data_structures, page 21]]

Funktioniert wie beim binären [[Binäre Suchbäume|Suchbaum]] (mit Sentinel).
Am Ende wird die Farbe des neuen Knotens auf rot gesetzt, dann wird die RSB-Bedingung wieder hergestellt

### Aufräumen

![[aud_folien_04_advanced_data_structures.pdf#page=22|aud_folien_04_advanced_data_structures, page 22]]

Wir setzen den Zeiger `z` auf den eingefügten roten Knoten und räumen so lange auf, wie der Elternknoten von `z` rot ist. Dabei unterscheiden wir zwischen drei Fällen:

Zeile 4: Fall 1
Zeile 9: Fall 2
Zeile 10: Fall 2.1
Zeile 13: Fall 2.2

![[aud_zusammenfassung_sose_24_rsb_cleanup_insert.pdf]]

#### [[Schleifeninvariante]]

Schleifeninvariante:
1. `z.color==red`
2. Wenn `z.parent` Wurzel, dann `z.parent.color==black`
3. Wenn der aktuelle Baum kein Rot-Schwarz-Baum ist, dann weil `z` als Wurzel die Farbe rot hat, oder weil "Nicht-Rot-Rot"-Regel für `z`, `z.parent` verletzt ist

Gilt zu Beginn, da
1. neuer Knoten `z` zunächst auf rot gesetzt wird
2. Wurzel im Baum zu Beginn schwarz ist,
3. "Schwarzhöhen"-Regel und "Rot-oder-Schwarz"-Regel von neuem roten Knoten `z` nicht verletzt wird, und alle anderen Knoten "Nicht-Rot-Rot"-Regel erfüllen

Im Fall 1:
1. z_new wird wieder rot (Zeile 7/8)
2. Farbe von z_new.parent ändert sich nicht
3. Schwarzhöhenregel bleibt erhalten und nur z_new wird rot

Im Fall 2:
1. z_new wird wieder rot, da `z.parent.color==red` in WHILE-Schleife
2. Farbe von z_new.parent wegen Z13 schwarz
3. SH-Regel erhalten und neues rotes z_new wird Kind eines schwarzen Knotens

#### Terminierung

Wenn `WHILE`-Schleife terminiert, dann weil `z.parent.color==black`. Dies ist spätestens bei der Wurzel der Fall.

#### [[Laufzeitanalyse|Laufzeit]]

Entweder `z` geht zwei nach oben (Z8) oder `WHILE`-Schleife terminiert (Z13).
Also maximal $\mathcal{O}(h)$ viele Iterationen mit jeweils konstanter Laufzeit, also Laufzeit $\mathcal{O}(h) = \mathcal{O}(\log n)$

## Löschen

Löschen funktioniert auch prinzipiell wie in einem normalen [[Binäre Suchbäume|binären Suchbaum]]. Wird der gelöschte Knoten durch einen anderen Knoten ersetzt, übernimmt der ersetzende Knoten die Farbe des gelöschten Knotens.
Beim Löschen müssen wir jedoch noch zusätzliche Zeiger setzen und Werte speichern, um nach dem Löschen die Rot-Schwarz-Baum-Bedingung wieder herzustellen:

### Fälle

`z` ist Blatt:
	`z` wird normal gelöscht
	Falls `z` schwarz war und nicht die Wurzel war: `dsh` speichert Seite mit zu großer Schwarzhöhe, `a` wird auf Elternknoten von `z` gesetzt, `fixup` wird am Ende aufgerufen
`z` ist Halbblatt:
	`z` wird normal gelöscht
	Keine weitere Aktion notwendig, da das schwarze Halbblatt durch dessen rotes Kind ersetzt wird, welches dann schwarz gefärbt wird. Wir haben also keinen schwarzen Knoten entfernt.
`z` hat zwei Kinder:
	`z` wird normal gelöscht
	Wenn `y` ein rechtes Kind war: `a` wird auf `y` gesetzt, `dsh=left`
	Wenn `y` ein linkes Kind war: `a` wird auf den ursprünglichen Elternknoten von `y` gesetzt, `dsh=right`
	Falls `y` schwarz war wird dann `fixup` aufgerufen
``

### Aufräumen

Nachdem wir jetzt beim Löschen den Zeiger `a` und den Wert `dsh` gesetzt haben, können wir anfangen den Baum wieder aufzuräumen. Um besser zwischen den Fällen unterscheiden zu können, benennen wir die Knoten um `a` herum auch, und erhalten die Knoten `b`, `c`, `d` und `x`.
Je nachdem, ob `dsh=left` oder `dsh=right`, erfolgt die Benennung der Knoten anders:

![[aud_zusammenfassung_sose_24_rsb_fixup_deletion_dsh_beispiele.png]]

Fall I: `a` schwarz. `b` rot
Fall IIa: `a` rot, `b` schwarz, `c`, `d` nicht rot
Fall IIb: `a` schwarz, `b` schwarz, `c`, `d` nicht rot
Fall III: `a` beliebig, `b` schwarz, `c` rot, `d` nicht rot
Fall IV: `a` beliebig, `b` schwarz, `c` beliebig, `d` rot

Die Beispiele in den Folien sind alle für den Fall `dsh=right`. Bei `dsh=left` muss man sich die Aktionen und den Baum spiegelverkehrt vorstellen.
Nach Fall IIa oder IV bricht der Algorithmus ab.

#### Fälle

![[aud_folien_04_advanced_data_structures.pdf#page=37|aud_folien_04_advanced_data_structures, page 37]]

![[aud_folien_04_advanced_data_structures.pdf#page=38|aud_folien_04_advanced_data_structures, page 38]]

![[aud_folien_04_advanced_data_structures.pdf#page=39|aud_folien_04_advanced_data_structures, page 39]]

![[aud_folien_04_advanced_data_structures.pdf#page=40|aud_folien_04_advanced_data_structures, page 40]]

![[aud_folien_04_advanced_data_structures.pdf#page=41|aud_folien_04_advanced_data_structures, page 41]]

### Beispiel

![[aud_zusammenfassung_sose_24_rsb_fixup_deletion.pdf#page=1]]

![[aud_zusammenfassung_sose_24_rsb_fixup_deletion.pdf#page=2]]

### [[Laufzeitanalyse|Laufzeit]]

`y` suchen hat wie bei einem [[Binäre Suchbäume|binären Suchbaum]] Laufzeit $\mathcal{O}(h) = \mathcal{O}(\log n)$
`fixup` geht nur in Fall IIb in Rekursion, dann aber ein Level höher
(In Fall I wird `a` zwar ein Level tiefer rotiert, aber dann bricht Rekursion nach Fällen IIa, III oder IV danach ab)
In jeder Rekursion konstante Laufzeit, also Gesamtlaufzeit $\mathcal{O}(h) = \mathcal{O}(\log n)$

### Algorithmen

Achtung: wird/wurde nicht in Vorlesung explizit vorgestellt (siehe Folien)

![[aud_folien_04_advanced_data_structures.pdf#page=138|aud_folien_04_advanced_data_structures, page 138]]

![[aud_folien_04_advanced_data_structures.pdf#page=139|aud_folien_04_advanced_data_structures, page 139]]

![[aud_folien_04_advanced_data_structures.pdf#page=140|aud_folien_04_advanced_data_structures, page 140]]

![[aud_folien_04_advanced_data_structures.pdf#page=141|aud_folien_04_advanced_data_structures, page 141]]

## Worst-Case-Laufzeiten

| Operation | Laufzeit         |
| --------- | ---------------- |
| Suchen    | $\Theta(\log n)$ |
| Einfügen  | $\Theta(\log n)$ |
| Löschen   | $\Theta(\log n)$ |
