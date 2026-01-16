---
tags:
  - foliensatz/06
  - cleaned
aliases:
  - Spannbaum
  - MST
  - Minimaler Spannbaum
  - Spannbäume
  - Minimale Spannbäume
Related:
  - "[[Algorithmus von Kruskal]]"
  - "[[Algorithmus von Prim]]"
  - "[[Kruskal und Prim für gerichtete Graphen]]"
---

## Minimaler Spannbaum (MST)

Für einen zusammenhängenden, ungerichteten, gewichteten Graphen $G = (V, E)$ mit Gewichten $w$ ist der Subgraph $T = (V, E_T)$ von $G$ ein Spannbaum ("spanning tree"), wenn $T$ azyklisch ist und alle Knoten verbindet.
Der Spannbaum ist minimal, wenn
$$w(T) = \sum_{\{u, v\} \in E_T} w(\{u, v\})$$
minimal für alle Spannbäume von $G$ ist, also die Summe der Gewichte der Kanten minimal ist.

![[aud_folien_06_graphen_algorithmen.pdf#page=81|aud_folien_06_graphen_algorithmen, page 81]]

## Gewichtsvergleich

Der rechte Spannbaum ist minimal, da jeder Spannbaum, der die Kante mit Gewicht 7 oder 11 enthält, ein größeres Gesamtgewicht hat

Gewicht vom linken Spannbaum $T$: 
$w(T) = 2+3+7+11=23$

Gewicht vom rechten Spannbaum $T'$:
$w(T') = 4+2+3+1=10$

![[aud_folien_06_graphen_algorithmen.pdf#page=82|aud_folien_06_graphen_algorithmen, page 82]]

## Anwendung: Broadcast in Netzwerken

Ein Broadcast verteilt eine Nachricht an alle Switches
Man möchte einen "Broadcast Storm" verhindern, in dem die Nachricht stets zyklisch weiterverteilt werden würde
Das Spanning Tree Protocol (IEEE 802.1D) wählt die "Root Bridge" als Wurzel des Spannbaums und wählt das Gewicht der Kanten/Verbindung in Abhängigkeit von Geschwindigkeit und Entfernung von Root Bridge

## Allgemeiner MST-Algorithmus: Idee

![[aud_folien_06_graphen_algorithmen.pdf#page=84|aud_folien_06_graphen_algorithmen, page 84]]

Wir versuchen mit jedem Durchlauf der while-Schleife einen "sicheren" Knoten für unseren minimalen Spannbaum zu finden (also einer, der die Bedingung des minimalen Spannbaums nicht kaputt macht) und fügen ihn zu unserem Spannbaum hinzu. Das machen wir so lange, bis wir einen Spannbaum haben.

## Terminologie

- Ein Schnitt $(S, V-S)$ partitioniert die Knoten des Graphen in zwei Mengen
- $\{u, v\}$ überbrückt den Schnitt $(S, V-S)$ wenn $u \in S$ und $v \in V-S$
- Ein Schnitt $(S, V-S)$ respektiert $A \subseteq E$, wenn keine Kante $\{u, v\} \in A$ den Schnitt überbrückt
- $\{u, v\}$ ist eine leichte Kante für $(S, V-S)$ wenn $w(\{u, v\})$ minimal für alle den Schnitt überbrückenden Kanten ist

![[aud_folien_06_graphen_algorithmen.pdf#page=86|aud_folien_06_graphen_algorithmen, page 86]]

## Leicht = Sicher

Sei $A$ eine Teilmenge eines MST, $(S, V-S)$ ein Schnitt, der $A$ respektiert, und $\{u, v\}$ eine leichte Kante, die den Schnitt überbrückt. Dann ist $\{u, v\}$ sicher für $A$.

### Beweis

Sei $T$ ein MST, der $A$ enthält. Wenn $\{u, v\}$ in $T$, sind wir fertig.

Wenn $\{u, v\}$ nicht in $T$ ist, dann konstruieren wir einen MST $U$, der $A \cup \{\{u, v\}\}$ enthält, folglich ist $\{u, v\}$ trotzdem sicher für $A$.

Der MST $T$ muss eine andere überbrückende Kante $\{x, y\}$ für den Pfad von $u$ nach $v$ enthalten, damit alle Knoten erreichbar sind.
Da der Schnitt $A$ respektiert, ist diese Kante $\{x, y\}$ nicht in $A$ enthalten.

Setze $U = (T - \{x, y\}) \cup \{u, v\}$

$U$ ist ein Spannbaum, da jeder Knoten erreichbar ist: wir nehmen statt "Brücke" $\{x, y\}$ den Pfad $x$ nach $u$, dann $\{u, v\}$, dann $v$ nach $y$.

$U$ ist dann minimal, da für die leichte Kante $\{u, v\}$ gilt, dass $w(\{u, v\}) \leq w(\{x, y\})$ und $w(U) = w(T) - w(\{x, y\}) + w(\{u, v\}) \leq w(T)$

![[aud_folien_06_graphen_algorithmen.pdf#page=90|aud_folien_06_graphen_algorithmen, page 90]]

## Algorithmendesign

"Leicht = sicher" legt eine Greedy-Strategie für eine konkrete Implementierung nage

Der [[Algorithmus von Kruskal]] lässt parallel mehrere Unterbäume eines MST wachsen
Der [[Algorithmus von Prim]] konstruiert einen MST Knoten für Knoten

(beide Algorithmen funktionieren auch für negative Kantengewichte)