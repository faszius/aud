---
tags:
  - foliensatz/07
  - cleaned
---

## Prinzip Backtracking

Wir suchen eine Lösung $x = (x_1, x_2, \ldots, x_n)$ per "Trial-and-Error", indem wir der Teillösung, die wir momentan haben, so lange Elemente $x_i$ hinzufügen, bis wir entweder eine gesamte Lösung haben, oder wir feststellen, dass von unserem Punkt aus keine Gesamtlösung mehr erreichbar ist, und wir das letzte hinzugefügte Element revidieren

## Beispiel

In diesem 4x4 Sudoku tragen wir so lange Werte ein, bis wir eine Lösung erhalten, oder wir keine Werte mehr eintragen können. Dann gehen wir zurück und ändern den letzten Wert, den wir eingetragen haben

![[aud_folien_07_advanced_designs.pdf#page=37|aud_folien_07_advanced_designs, page 37]]

Zuerst fügen wir die $1$ hinzu:

![[aud_folien_07_advanced_designs.pdf#page=38|aud_folien_07_advanced_designs, page 38]]

Dann können wir jedoch an der nächsten Stelle keine weiteren Werte hinzufügen

![[aud_folien_07_advanced_designs.pdf#page=39|aud_folien_07_advanced_designs, page 39]]

Also gehen wir zurück und ändern den Wert:

![[aud_folien_07_advanced_designs.pdf#page=40|aud_folien_07_advanced_designs, page 40]]

Die nächsten beiden Felder füllen wir dann mit der einzig zulässigen Option:

![[aud_folien_07_advanced_designs.pdf#page=41|aud_folien_07_advanced_designs, page 41]]

Nachdem wir die $3$ im nächsten Feld eintragen, gibt es wieder keine zulässige Option, also gehen wir zurück und ändern den Wert zu einer $1$:

![[aud_folien_07_advanced_designs.pdf#page=42|aud_folien_07_advanced_designs, page 42]]

Die nächsten Werte sind dann alle eindeutig:

![[aud_folien_07_advanced_designs.pdf#page=43|aud_folien_07_advanced_designs, page 43]]

## Backtracking vs. [[Depth-First Search (DFS)|DFS]]

Backtracking kann man als Tiefensuche auf Rekursionsbaum betrachten, wobei aussichtslose Lösungen evtl. frühzeitig abgeschnitten werden

![[aud_folien_07_advanced_designs.pdf#page=44|aud_folien_07_advanced_designs, page 44]]

## Backtracking vs. Brute-Force Search

![[aud_folien_07_advanced_designs.pdf#page=45|aud_folien_07_advanced_designs, page 45]]

Backtracking kann man als „intelligentere“ erschöpfende Suche ansehen, die aussichtslose Lösungen vorher aussortiert, im Gegensatz zu Brute-Force, das alle Möglichkeiten durchgeht, auch wenn es keine möglichen Lösungen sind

## Lösungssuche

![[aud_folien_07_advanced_designs.pdf#page=46|aud_folien_07_advanced_designs, page 46]]

## Beispiel: Regulärer Ausdruck

Wir können Backtracking benutzen, um einen String per Backtracking gegen einen regulären Ausdruck zu überprüfen

![[aud_folien_07_advanced_designs.pdf#page=47|aud_folien_07_advanced_designs, page 47]]

Wir können den String dann per Backtracking mit dem regulären Ausdruck abgleichen, um festzustellen, ob er den String beschreibt. Dabei "raten" wir immer, welcher Teil des regulären Ausdrucks auf das nächste Zeichen zutrifft

![[aud_folien_07_advanced_designs.pdf#page=48|aud_folien_07_advanced_designs, page 48]]

Dabei haben wir jedoch unter Umständen einen exponentiellen Aufwand

![[aud_folien_07_advanced_designs.pdf#page=49|aud_folien_07_advanced_designs, page 49]]