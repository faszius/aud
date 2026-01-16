---
tags:
  - foliensatz/05
  - cleaned
aliases:
  - Bloom Filter
---

## Beispiel: Schlechte Passwörter Vermeiden

1. Man kann alle "schlechten" Passwörter in einem Bloom-Filter speichern - der speichert alle Wörter in einer kompakteren Form
2. Dann kann man schnell prüfen, ob ein eingegebenes Passwort im Bloom-Filter ist - dabei können starke Passwörter fälschlicherweise auch als schwach angezeigt werden, aber das ist nicht schlimm

![[aud_folien_05_randomized_data_structures.pdf#page=36|aud_folien_05_randomized_data_structures, page 36]]

![[aud_folien_05_randomized_data_structures.pdf#page=37|aud_folien_05_randomized_data_structures, page 37]]

## Erstellen

Gegeben: 
- $n$ Elemente $x_0, \ldots, x_{n-1}$ beliebiger Komplexität
- $m$ Bits Speicher, üblicherweise in einem Bit-Array
- $k$ "gute" Hash-Funktionen $H_0, \ldots, H_{k-1}$ mit Bildbereich $0, 1, \ldots, m-1$

Empfohlene Wahl: $k = \frac{m}{n} \cdot \ln 2$
Ergibt Fehlerrate von ca. $2^{-k}$
Üblicherweise $k = 5, 6, \ldots, 20$

1. Initialisiere Array voller Nullen
2. Schreibe für jedes Element $x_i$ in jede Bit-Position $H_0(x_i), \ldots, H_{k-1}(x_i)$ eine 1
   (eventuell werden dabei Einträge erneut auf 1 gesetzt)

![[aud_folien_05_randomized_data_structures.pdf#page=40|aud_folien_05_randomized_data_structures, page 40]]

## Suchen

Gib an, dass `y` im Wörterbuch, wenn genau alle $k$ Einträge für `y` in `BF=1` sind, also wenn an jeder Position $H_0(y), \ldots, H_{k-1}(y)$ eine 1 steht

![[aud_folien_05_randomized_data_structures.pdf#page=41|aud_folien_05_randomized_data_structures, page 41]]

## Korrektheit

Wenn `y` im Wörterbuch ist, also `y=X[i]` für ein `i`, dann wurden alle Einträge `H[j](X[i])` in `BF` zuvor gesetzt, also gibt der Algorithmus auch `1` zurück
Es gibt also keine "false negatives"

Wenn `y` nicht im Wörterbuch ist, dann gibt der Algorithmus evtl. trotzdem `1` zurück.
Das passiert, wenn die Einträge von anderen Werten getroffen wurden
Daher "gute" Hash-Funktionen wählen und Größe des Filters nicht zu klein setzen
Wenn BF nur bis zur Hälfte mit 1en gefüllt ist und die Hash-Funktionen uniforme und unabhängige Werte liefern, dann ist der Fehler $\leq 2^{-k}$

## Bloom-Filter: Beispielrechnung

![[aud_folien_05_randomized_data_structures.pdf#page=44|aud_folien_05_randomized_data_structures, page 44]]

