---
tags:
  - foliensatz/03/abc
  - cleaned
aliases:
  - Stack
---

## Abstrakter Datentyp Stack

`new(S)` 
	Erzeugt neuen (leeren) Stack namens `S`
`isEmpty(S)`
	Gibt an, ob Stack `S` leer
`pop(S)`
	Gibt oberstes Element vom Stack `S` zurück und löscht es vom Stack 
	(bzw. Fehlermeldung, wenn Stack leer)
`push(S, k)`
	Schreibt `k` als neues oberstes Element auf Stack `S`
	(bzw. Fehlermeldung, wenn Stack voll)

![[aud_folien_03abc_basic_data_structures.pdf#page=4|aud_folien_03abc_basic_data_structures, page 4]]

## Algebraische Spezifikation Von Stacks

Stack mit Operationen `new`, `isEmpty`, `push`, `pop` muss folgende Regeln erfüllen:

1. Wenn `new(S)`, dann unmittelbar `isEmpty(S)`, dann Ergebnis `true`
2. Wenn `push(S, k)` und keine Fehlermeldung, dann unmittelbar `pop(S)`, ergibt Ergebnis `k`
3. ...

## Verbildlichung

```
Anfangszustand:

|   |
|   |
|   |
|   |
|   |
|   |
|---|

push(2):

|   |
|   |
|   |
|   |
|---|
| 2 |
|---|

push(1):

|   |
|   |
|---|
| 1 |
|---|
| 2 |
|---|

pop:

|   |
|   |
|   |
|   |
|---|
| 2 |
|---|

(Rückgabe von 1)

push(7):

|   |
|   |
|---|
| 7 |
|---|
| 2 |
|---|

push(3):

|---|
| 3 |
|---|
| 7 |
|---|
| 2 |
|---|

push(6):

ERROR - Stack schon voll
```

## Stacks Als Array

![[aud_folien_03abc_basic_data_structures.pdf#page=7|aud_folien_03abc_basic_data_structures, page 7]]

![[aud_folien_03abc_basic_data_structures.pdf#page=8|aud_folien_03abc_basic_data_structures, page 8]]

## Algorithmen

![[aud_folien_03abc_basic_data_structures.pdf#page=9|aud_folien_03abc_basic_data_structures, page 9]]

## Stacks Mit Variabler Größe

Bei Overflow zwei grundlegende Optionen:
- In größeres, zusammenhängendes Array kopieren
- Auf viele Arrays verteilen (wie verkettete Listen)

### Neuen Freien Eintrag Erschaffen

![[aud_folien_03abc_basic_data_structures.pdf#page=11|aud_folien_03abc_basic_data_structures, page 11]]

#### Laufzeit

![[aud_folien_03abc_basic_data_structures.pdf#page=12|aud_folien_03abc_basic_data_structures, page 12]]

Durchschnittlich $\Omega(n)$ Kopier-Operationen pro `push`-Befehl

### Speicher Verdoppeln

![[aud_folien_03abc_basic_data_structures.pdf#page=13|aud_folien_03abc_basic_data_structures, page 13]]

#### Algorithmen

![[aud_folien_03abc_basic_data_structures.pdf#page=14|aud_folien_03abc_basic_data_structures, page 14]]

![[aud_folien_03abc_basic_data_structures.pdf#page=15|aud_folien_03abc_basic_data_structures, page 15]]

#### Analyse Laufzeit

1. $n$ Elemente (unmittelbar nach letzter Vergrößerung)
2. Neue Speichergrenze wird nur erreicht, wenn dann mindestens $n$ viele push-Befehle
3. Umkopieren kostet dann $\mathcal{O}(n)$ Schritte

Im Durchschnitt für jeden der mindestens $n$ Befehle $\Theta(1)$ Umkopierschritte!

## Stacks in Java

![[aud_folien_03abc_basic_data_structures.pdf#page=17|aud_folien_03abc_basic_data_structures, page 17]]

