---
tags:
  - foliensatz/05
  - cleaned
aliases:
  - Hash Table
---

## Idee

Ist eine (durchschnittliche) Laufzeit von $\Theta(1)$ möglich?

Aus der Hashfunktion eines Elements können wir dessen Index in einem Array berechnen
Die Hashfunktion sollte dabei "gut verteilen"
Mathematisch formuliert: $h(\texttt{x})$ ist uniform und unabhängig im Intervall $[0, \texttt{T.length}-1]$ verteilt
Dann können wir mit konstant vielen Array-Operationen einfügen

![[aud_folien_05_randomized_data_structures.pdf#page=25|aud_folien_05_randomized_data_structures, page 25]]

## Suchen Und Löschen

Mithilfe der Hash-Funktion können wir den Index des Elements `w` berechnen
(Ist `w` in `T[h(w)]`?)
Dann können wir das Element löschen

![[aud_folien_05_randomized_data_structures.pdf#page=26|aud_folien_05_randomized_data_structures, page 26]]

## Kollisionsauflösung

Wenn ein Array-Eintrag schon belegt ist, dann bilde eine [[Verkettete Listen|verkettete Liste]] und füge das neue Element vorne ein

![[aud_folien_05_randomized_data_structures.pdf#page=27|aud_folien_05_randomized_data_structures, page 27]]

## Hash Tables Mit Verketteten Listen

Einfügen benötigt immer noch eine konstante Anzahl Array-/Listen-Operationen
Suchen und Löschen benötigt so viele Schritte, wie die jeweilige Liste lang ist
Wenn die Hashfunktion uniform verteilt, dann hat jede Liste im Erwartungswert $\frac{n}{\texttt{T.length}}$ viele Einträge

![[aud_folien_05_randomized_data_structures.pdf#page=28|aud_folien_05_randomized_data_structures, page 28]]

Wählt man $\texttt{T.length} \approx n$ ergibt sich also eine konstante Laufzeit (im Durchschnitt)

## Gute Hash-Funktionen?

![[aud_folien_05_randomized_data_structures.pdf#page=30|aud_folien_05_randomized_data_structures, page 30]]

![[aud_folien_05_randomized_data_structures.pdf#page=31|aud_folien_05_randomized_data_structures, page 31]]

## Laufzeiten

| Operation | Laufzeit (im Durchschnitt)       |
| --------- | -------------------------------- |
| Einfügen  | $\Theta(1)$ (auch im Worst Case) |
| Löschen   | $\Theta(1)$                      |
| Suchen    | $\Theta(1)$                      |
Speicherbedarf in der Regel größer als $n$, üblicherweise ca. $1,33 \cdot n$