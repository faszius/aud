---
tags:
  - foliensatz/07
  - cleaned
aliases:
  - Hill Climbing
---

## Hill-Climbing-Algorithmus

![[aud_folien_07_advanced_designs.pdf#page=84|aud_folien_07_advanced_designs, page 84]]

Erklärung: wie wählen eine (zufällige) initiale Lösung. Dann ändern wir sie leicht ab, und gucken, ob die neue Lösung besser ist. Wenn das der Fall ist, arbeiten wir mit ihr weiter. Der Gedankengang ist, dass man irgendwann zur idealen Lösung kommt, wenn stets den "besseren" Lösungen folgt.

Am Beispiel von [[Traveling Salesperson Problem (TSP)|TSP]]:
`initSol`: wähle beliebige Tour, z.B. per [[Greedy]]-Algorithmus
`perturb`: wähle zwei Knoten `u`, `v` zufällig und vertausche sie in der Tour
`quality`: (negatives) Gewicht der aktuellen Tour

### Hill-Climbing-Algorithmus Für TSP

![[aud_folien_07_advanced_designs.pdf#page=85|aud_folien_07_advanced_designs, page 85]]