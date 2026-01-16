---
tags:
  - foliensatz/07
  - cleaned
aliases:
  - Dynamische Programmierung
---

## Prinzip Dynamisches Programmieren

Wir teilen das Problem in (überlappende) Teilprobleme
Die Teilprobleme lösen wir dann rekursiv und verwenden die Zwischenergebnisse dabei wieder ("Memoization")
Am Ende rekonstruieren wir die Gesamtlösung

Achtung: hierbei geht es hauptsächlich um das Auffinden geeigneter Rekursionen!

## Beispiel: Fibonacci-Zahlen

Gegeben den folgenden (typischen) rekursiven Algorithmus zum berechnen einer $n$-elementigen Folge an Fibonacci-Zahlen:

![[aud_folien_07_advanced_designs.pdf#page=52|aud_folien_07_advanced_designs, page 52]]

Der "Berechnungsbaum" sieht dann wie folgt aus:

![[aud_folien_07_advanced_designs.pdf#page=53|aud_folien_07_advanced_designs, page 53]]

Anstelle davon, dass viele Werte mehrfach berechnet werden, können wir stattdessen Werte zwischenspeichern ("Memoization"). Das sieht dann wie folgt aus:

![[aud_folien_07_advanced_designs.pdf#page=54|aud_folien_07_advanced_designs, page 54]]

Wir erhalten immer noch eine lineare Laufzeit $\Theta(n)$.
In Zeile 1 wird überprüft ob der Wert schon berechnet wurde, in dem Fall wird er frühzeitig wiedergegeben.
In Zeile 6 (falls der Wert noch nicht berechnet wurde) wird der berechnete Wert gespeichert.

## Minimum Edit Distance

Ein weiteres Beispiel, an dem sich das Prinzip der dynamischen Programmierung anwenden lässt, ist die [[Minimum Edit Distance]]

