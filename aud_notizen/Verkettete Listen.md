---
tags:
  - foliensatz/03/abc
  - cleaned
aliases:
  - Verkettete Liste
  - Linked List
---

## Datenstruktur Verkettete Listen

![[aud_folien_03abc_basic_data_structures.pdf#page=20|aud_folien_03abc_basic_data_structures, page 20]]

`head` zeigt auf erstes Element (bzw. ist `nil` für leere Liste)

Jedes Element `x` besteht aus:
`key` - Wert
`prev` - Zeiger auf Vorgänger (bzw. `nil`)
`next` - Zeiger auf Nachfolger (bzw. `nil`)

## Verkettete Listen Durch Arrays

![[aud_folien_03abc_basic_data_structures.pdf#page=21|aud_folien_03abc_basic_data_structures, page 21]]

## Elementare Operationen Auf Verkettete Listen

### `search`

![[aud_folien_03abc_basic_data_structures.pdf#page=22|aud_folien_03abc_basic_data_structures, page 22]]

Laufzeit $\Theta(n)$

### `insert`

![[aud_folien_03abc_basic_data_structures.pdf#page=23|aud_folien_03abc_basic_data_structures, page 23]]

Laufzeit $\Theta(1)$
Achtung: Einfüge-Operation prüft nicht, ob Wert bereits in Liste
Wenn zuerst Suche nach Wert, dann wiederum Laufzeit $\Omega(n)$

### `delete`

![[aud_folien_03abc_basic_data_structures.pdf#page=25|aud_folien_03abc_basic_data_structures, page 25]]

Laufzeit $\Theta(1)$

## Vereinfachung per Wächter/Sentinels

![[aud_folien_03abc_basic_data_structures.pdf#page=26|aud_folien_03abc_basic_data_structures, page 26]]

Ziel: eliminiere die Spezialfälle für Listenanfang/-ende

### Löschen Mit Sentinels

![[aud_folien_03abc_basic_data_structures.pdf#page=27|aud_folien_03abc_basic_data_structures, page 27]]

