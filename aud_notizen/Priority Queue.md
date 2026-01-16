---
tags:
  - foliensatz/04
  - cleaned
Related:
  - "[[Binäre Max-Heaps]]"
---
Lassen sich mithilfe von [[Binäre Max-Heaps|Binären Max-Heaps]] implementieren

`new(Q)`
	Erzeugt neue (leere) Priority Queue namens `Q`
`isEmpty(Q)`
	Gibt an, ob Queue `Q` leer
`max(Q)`
	Gibt größtes "Element" aus Queue `Q` zurück
	(bzw. Fehlermeldung wenn Queue leer)
`extract-max(Q)`
	Gibt größtes "Element" aus Queue `Q` zurück und löscht es aus Queue
	(Bzw. Fehlermeldung wenn Queue leer)
`insert(Q, k)`
	Fügt Wert `k` zur Queue `Q` hinzu
