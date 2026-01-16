---
tags:
  - foliensatz/04
  - cleaned
aliases:
  - Splay-Baum
  - Splay Baum
  - Splay Bäume
  - Splay
---

## Idee

Einmal angefragte Werte werden voraussichtlich noch öfter angefragt - bedeutet, wir können sie nach vorne verschieben um zukünftige Anfragen schneller zu machen. Bei Listen sieht das wie folgt aus:

![[aud_folien_04_advanced_data_structures.pdf#page=71|aud_folien_04_advanced_data_structures, page 71]]

## Splay-Operation

Wenn wir einen Wert suchen oder einfügen, "spülen" wir ihn danach an die Wurzel. Das machen wir mithilfe von drei verschiedenen Operationen, die wir so oft passend ausführen, bis der Wert an der Wurzel ist.

![[aud_folien_04_advanced_data_structures.pdf#page=73|aud_folien_04_advanced_data_structures, page 73]]

### Zig-Zag-Operation

Rechts-Links oder Links-Rechts-[[Rotation]]

![[aud_folien_04_advanced_data_structures.pdf#page=74|aud_folien_04_advanced_data_structures, page 74]]

### Zig-Zig-Rotation

Links-Links oder Rechts-Rechts [[Rotation]]

![[aud_folien_04_advanced_data_structures.pdf#page=75|aud_folien_04_advanced_data_structures, page 75]]

### Zig-Operation

Einfache Links- oder Rechts-[[Rotation]]

![[aud_folien_04_advanced_data_structures.pdf#page=76|aud_folien_04_advanced_data_structures, page 76]]

### Algorithmus

![[aud_folien_04_advanced_data_structures.pdf#page=77|aud_folien_04_advanced_data_structures, page 77]]

Bei jeder Iteration wird `z` um mindestens ein Level nach oben rotiert, bedeutet Laufzeit $\mathcal{O}(h)$

Die Algorithmen für `zig` und `zigZag` sind analog

### Beispiel

![[aud_folien_04_advanced_data_structures.pdf#page=78|aud_folien_04_advanced_data_structures, page 78]]

![[aud_folien_04_advanced_data_structures.pdf#page=79|aud_folien_04_advanced_data_structures, page 79]]

![[aud_folien_04_advanced_data_structures.pdf#page=80|aud_folien_04_advanced_data_structures, page 80]]

## Suchen

![[aud_folien_04_advanced_data_structures.pdf#page=81|aud_folien_04_advanced_data_structures, page 81]]

Wie im [[Binäre Suchbäume|binären Suchbaum]], nur dass der gefundene Knoten im Anschluss an die Wurzel bewegt wird.

## Einfügen

Auch wie im [[Binäre Suchbäume|binären Suchbaum]], nur dass der eingefügte Knoten im Anschluss an die Wurzel bewegt wird.

![[aud_folien_04_advanced_data_structures.pdf#page=82|aud_folien_04_advanced_data_structures, page 82]]

![[aud_folien_04_advanced_data_structures.pdf#page=83|aud_folien_04_advanced_data_structures, page 83]]

Die Position zu suchen und den Knoten nach oben zu spülen haben beide jeweils eine Laufzeit $\mathcal{O}(h)$, also hat der gesamte Algorithmus auch eine Laufzeit $\mathcal{O}(h)$.

## Löschen

![[aud_folien_04_advanced_data_structures.pdf#page=85|aud_folien_04_advanced_data_structures, page 85]]

Der zu löschende Knoten wird nach oben gespült und erst dann gelöscht. Dann erhalten wir zwei Teilbäume, die nicht mehr verbunden sind. Ist eine der beiden Teilbäume leer, dann sind wir fertig.

![[aud_folien_04_advanced_data_structures.pdf#page=86|aud_folien_04_advanced_data_structures, page 86]]

Sonst spülen wir den "größten" Knoten im linken Teilbaum `L` per Splay-Operation nach oben und hängen den rechten Teilbaum `R` dann an diesen Knoten dran.

### Beispiel

![[aud_folien_04_advanced_data_structures.pdf#page=87|aud_folien_04_advanced_data_structures, page 87]]

### Laufzeit

![[aud_folien_04_advanced_data_structures.pdf#page=88|aud_folien_04_advanced_data_structures, page 88]]

Wir haben also eine Gesamtlaufzeit $\mathcal{O}(h)$

## Laufzeit

Bei Splay-Bäumen macht sich der Vorteil in der Laufzeit erst bemerkbar, wenn wir die Laufzeit pro Operation über mehrere Operationen hinweg betrachten. Dabei beobachten wir:

Für $m \geq n$ Operationen auf einem Splay-Baum mit maximal $n$ Knoten ist die Worst-Case-Laufzeit $\mathcal{O}(m \cdot \log_2 n)$, also $\mathcal{O}(\log_2 n)$ pro Operation
