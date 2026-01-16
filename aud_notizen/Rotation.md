---
tags:
  - foliensatz/04
  - cleaned
aliases:
  - rotieren
  - rotiert
---

Die Rotation ist eine Aktion, die in verschiedenen [[Binäre Suchbäume|binären Suchbäumen]] sehr praktisch ist (z.B. Rot-Schwarz-Bäume, AVL-Bäume, Splay-Bäume etc.)

Hier wird sie mit einem Rot-Schwarz-Baum vorgeführt:

![[aud_folien_04_advanced_data_structures.pdf#page=16|aud_folien_04_advanced_data_structures, page 16]]

![[aud_folien_04_advanced_data_structures.pdf#page=17|aud_folien_04_advanced_data_structures, page 17]]

Laufzeit $\Theta(1)$
Bei Rot-Schwarz-Bäumen ist die Rot-Schwarz-Baum-Bedingung nach der Rotation evtl. verletzt!
Jedoch bleibt die Eigenschaft eines binären Suchbaums erhalten.
`rotateRight` ist analog, nur mit `left` und `right` vertauscht