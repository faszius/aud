---
tags:
  - foliensatz/03/abc
  - cleaned
aliases:
  - Queue
---

## Abstrakter Datentyp Queue

`new(Q)`
	Erzeugt neue (leere) Queue namens `Q`
`isEmpty(Q)`
	Gibt an, ob Queue `Q` leer
`dequeue(Q)`
	Gibt vorderstes Element der Queue `Q` zurück und löscht es aus Queue
	(Bzw. Fehlermeldung, wenn Queue leer)
`enqueue(Q, k)`
	Schreibt `k` als neues hinterstes Element auf `Q`
	(Bzw. Fehlermeldung, wenn Queue voll)

## Queues Als Array

![[aud_folien_03abc_basic_data_structures.pdf#page=30|aud_folien_03abc_basic_data_structures, page 30]]

`Q.rear` ist zu Beginn auch rechts, wandert beim Einfügen nach links
`Q.front` ist zu Beginn ganz rechts, wandert dann beim Auswerfen nach links
Problem: selbst wenn maximale Anzahl Elemente, die gleichzeitig in der Queue sind, vorher bekannt ist, kann `Q.rear` die Array-Grenze links erreichen

![[aud_folien_03abc_basic_data_structures.pdf#page=31|aud_folien_03abc_basic_data_structures, page 31]]

`Q.front` ist zu Beginn ganz links, wandert dann nach rechts beim Auswerfen
`Q.rear` ist zu Beginn auch ganz links, wandert beim Einfügen nach rechts
Problem: selbst wenn Array nach rechts beliebig lang, wird der Speicher links von `Q.front` verschwendet

## Queues Als (virtuelles) Zyklisches Array

![[aud_folien_03abc_basic_data_structures.pdf#page=32|aud_folien_03abc_basic_data_structures, page 32]]

`Q.front` und `Q.rear` wandern jeweils zyklisch nach rechts
Der Zeiger im eigentlichen Array muss dann beim Wandern nach rechts von 7 auf 0 springen (und links von 0 auf 7)

![[aud_folien_03abc_basic_data_structures.pdf#page=34|aud_folien_03abc_basic_data_structures, page 34]]

Ist im Beispiel eine leere oder volle Schlange?
Diese Information kann im Boolean `empty` gespeichert werden (alternativ ein Element des Arrays als "Abstandshalter" reservieren)

### Algorithmen

![[aud_folien_03abc_basic_data_structures.pdf#page=35|aud_folien_03abc_basic_data_structures, page 35]]

## Queues Durch Einfach Verkettete Listen

![[aud_folien_03abc_basic_data_structures.pdf#page=36|aud_folien_03abc_basic_data_structures, page 36]]

### Algorithmen

![[aud_folien_03abc_basic_data_structures.pdf#page=37|aud_folien_03abc_basic_data_structures, page 37]]