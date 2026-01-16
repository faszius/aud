---
tags:
  - foliensatz/05
  - cleaned
aliases:
  - Skip List
  - Skip-Listen
  - Skip-Liste
  - Skip-List
---

## Operationen in Sortierter Liste

Zur Wiederholung:

| Operation      | Laufzeit (Worst Case) |
| -------------- | --------------------- |
| Suchen         | $\Omega(n)$           |
| Löschen (Wert) | $\Omega(n)$           |
| Einfügen       | $\Omega(n)$           |
Geht das schneller?

## Idee Von Skip-Listen

Füge "Express-Liste" mit einigen Elementen ein:

![[aud_folien_05_randomized_data_structures.pdf#page=5|aud_folien_05_randomized_data_structures, page 5]]

(Bemerkung: das erste "richtige" Element muss nicht in der Express-Liste sein)

### Suche Mittels Express-Listen

Beginne in Express-Liste:
Element gefunden? 
	-> Element ausgeben
Nächstes Element in Express-Liste kleiner-gleich gesuchtes Element? 
	-> Weiter nach rechts
Nächstes Element in Express-Liste größer als gesuchtes Element?
	-> Nach unten in ursprünglicher Liste und dort weitersuchen

![[aud_folien_05_randomized_data_structures.pdf#page=6|aud_folien_05_randomized_data_structures, page 6]]

### Verbesserung

Express-Liste ist wieder Liste -> Verfahre rekursiv

Beispiel:
Jede Express-Liste hat die Hälfte der Elemente aus der vorigen Liste
Das ergibt $\frac{n}{2} + \frac{n}{4} + \ldots + 2 + 1 \leq n$ zusätzliche Elemente in Express-Listen

![[aud_folien_05_randomized_data_structures.pdf#page=7|aud_folien_05_randomized_data_structures, page 7]]

## Implementierung

`L.head`
	Erstes/oberes Element der Liste
`L.height`
	Höhe der Skiplist (beginnt mit 1)
`x.key`
	Wert
`x.next`
	Nachfolger
`x.prev`
	Vorgänger
`x.down`
	Nachfolger Liste unten
`x.up`
	Nachfolger Liste open
`nil`
	Kein Nachfolger/leeres Element

## Suchalgorithmus

![[aud_folien_05_randomized_data_structures.pdf#page=9|aud_folien_05_randomized_data_structures, page 9]]

## Auswahl Der Elemente Für Express-Listen

Idee: wähle jedes Element aus Liste mit Wahrscheinlichkeit $p$ (z.B. $p = \frac{1}{2}$) für übergeordnete Liste

Aus der Linearität des Erwartungswerts folgt eine durchschnittliche Höhe von $h = \mathcal{O}(\log_{1/p}n)$
In der ersten Expressliste sind $pn$ Elemente, in der zweiten $p^2n$ Elemente etc...

### Linearität Des Erwartungswerts

![[aud_folien_05_randomized_data_structures.pdf#page=11|aud_folien_05_randomized_data_structures, page 11]]
<font size="1pt" color="gray">promi lässt grüßen</font>

## Durchschnittliche Laufzeit Für Suchen

Im schlimmsten Fall wird die Suche erst in der unteren Liste beendet
Im Durchschnitt machen wir nur $\frac{1}{p}$ Schritte auf jeder Ebene, bevor wir eine Ebene runter gehen
Wenn die Skip-Liste die Höhe $h$ hat, brauchen wir also im Durchschnitt $\frac{1}{p} + \frac{1}{p} + \frac{1}{p} + \ldots + \frac{1}{p} = \mathcal{O}(h) = \mathcal{O}(\log n)$ Schritte

### Erwartungswert Geometrisch Verteilter Zufallsvariablen

![[aud_folien_05_randomized_data_structures.pdf#page=14|aud_folien_05_randomized_data_structures, page 14]]

## Löschen

![[aud_folien_05_randomized_data_structures.pdf#page=19|aud_folien_05_randomized_data_structures, page 19]]

Entferne Vorkommen des Elements auf allen Ebenen
Laufzeit $\mathcal{O}(h)$

## Laufzeiten

| Operation | Laufzeit              |
| --------- | --------------------- |
| Einfügen  | $\Theta(\log_{1/p}n)$ |
| Löschen   | $\Theta(\log_{1/p}n)$ |
| Suchen    | $\Theta(\log_{1/p}n)$ |
$p$ ist die Wahrscheinlichkeit, dass ein Element zu der darüberliegenden Skip-List hinzugefügt wird
$\mathcal{O}$-Notation versteckt (konstanten) Faktor $1/p$
Speicherbedarf im Durchschnitt $= n + pn + p^2n + \ldots = n \cdot \sum_{i\geq0}p^i = \frac{n}{1-p}$
