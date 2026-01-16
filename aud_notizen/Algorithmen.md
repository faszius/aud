---
tags:
  - "#foliensatz/01"
  - "#cleaned"
---

## Verortung Algorithmen

![[aud_folien_01_introduction.pdf#page=3|aud_folien_01_introduction, page 3]]

Algorithmen befinden sich auf einer höheren Abstraktionsebene als Programme

## Definition

Eine aus endlich vielen Schritten bestehende, ausführbare Handlungsvorschrift zur eindeutigen Umwandlung von Eingabe- in Ausgabedaten

## Allgemeine Charakteristika

**Berechenbar**
- Finitheit: Algorithmus hat endliche Beschreibung
- Terminierung: Algorithmus stoppt in endlicher Zeit
- Effektivität: Schritte sind auf Maschine ausführbar

**Bestimmt**
- Determiniertheit: Algorithmus liefert bei gleicher Eingabe gleiche Ausgabe
- Determinismus: Algorithmus durchläuft für gleiche Eingabe immer die gleichen Schritte/Zustände

**Anwendbar**
- Allgemeinheit: Algorithmus für ganze Problemklasse anwendbar
- Korrektheit: Falls Algorithmus terminiert, ist die Ausgabe richtig

### Beispiel: Euklidscher Algorithmus```

```
gcd(a,b) // a,b >= 0 integers 
1  IF b==0 THEN 
2    return a 
3  ELSE //a mod b Divisionsrest 
4    return gcd(b,a mod b)
```

**Finitheit:** Algorithmus hat endliche Beschreibung
Dadurch gegeben, dass der Algorithmus sich als Code darstellen lässt

**Effektivität:** Schritt sind auf Maschine ausführbar
Dadurch gegeben, dass der Code nur geläufige Instruktionen enthält

**Terminierung:** Algorithmus stoppt in endlicher Zeit
Gegeben, da der Divisionsrest stets zwischen 0 und b-1 ist, sodass das zweite Argument in jeder Iteration um mindestens 1 kleiner wird und schließlich der Basisfall b=0 erreicht wird

**Determinismus:** gleiche Eingabe, gleiche Schritte
Dadurch gegeben, dass der Code keinen Zufall enthält/Computer deterministisch sind

**Determiniertheit:** gleiche Eingabe, gleiche Ausgabe
Durch Determinismus gegeben

**Allgemeinheit:** für Problemklasse anwendbar
**Korrektheit:** falls der Algorithmus terminiert, ist die Ausgabe richtig
Folgt aus $\text{gcd}(a, b) = \text{gcd}(b, a \mod b)$ sowie $\text{gcd}(a, 0) = a$

