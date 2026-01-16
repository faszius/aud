---
tags:
  - foliensatz/06
  - cleaned
aliases:
  - BFS
  - Breadth-First-Search
  - Breadth-First Search
  - Breadth First Search
  - Breitensuche
---

## Idee

Zuerst besuchen wir alle unmittelbaren Nachbarn, denn deren Nachbarn usw.

![[aud_folien_06_graphen_algorithmen.pdf#page=18|aud_folien_06_graphen_algorithmen, page 18]]

## Algorithmus

![[aud_folien_06_graphen_algorithmen.pdf#page=20|aud_folien_06_graphen_algorithmen, page 20]]

Laufzeit von $O(|V| + |E|)$

`WHITE` (weiß) bedeutet der Knoten wurde noch nicht besucht
`GRAY` (grau) bedeutet der Knoten ist in der Queue für den nächsten Schritt
`BLACK` (schwarz) bedeutete der Knoten wurde fertig abgearbeitet

### Zeilenweise Erklärung

Z1-2: Setze jeden Knoten außer den Startknoten auf weiß, setze die Entfernung auf $+\infty$ und den Vorgänger auf `NIL`
Z3: Setze den Startknoten auf grau, dessen Entfernung auf 0 und dessen Vorgänger auf `NIL`
Z4: Speichere den Startknoten in der [[Queues|Queue]]
Z6: Solange die Queue nicht leer ist:
	Z7: Betrachte den nächsten Knoten der Queue
	Z8: Für jeden adjazenten Knoten
		Z9: Wurde er noch nicht besucht (ist also weiß), setze ihn auf grau, setze dessen Entfernung auf die Entfernung des jetzigen Knotens + 1, setze den Vorgänger auf den jetzigen Knoten
	Z10: Setze den jetzigen Knoten auf schwarz

## Beispiel

Zuerst wird der Startknoten 1 betrachtet und alle dessen Nachbarn in die Queue getan

![[aud_folien_06_graphen_algorithmen.pdf#page=21|aud_folien_06_graphen_algorithmen, page 21]]

Dann wird das erste Element der Queue abgearbeitet und alle dessen Nachbarn in die Queue getan

![[aud_folien_06_graphen_algorithmen.pdf#page=22|aud_folien_06_graphen_algorithmen, page 22]]

![[aud_folien_06_graphen_algorithmen.pdf#page=23|aud_folien_06_graphen_algorithmen, page 23]]

Bis die Queue schließlich leer ist

![[aud_folien_06_graphen_algorithmen.pdf#page=24|aud_folien_06_graphen_algorithmen, page 24]]

## Laufzeit

![[aud_folien_06_graphen_algorithmen.pdf#page=25|aud_folien_06_graphen_algorithmen, page 25]]

Laufzeit $O(|V| + |E|)$

## Korrektheit

Sei $G = (V, E)$ ein gerichteter oder ungerichteter Graph mit Knoten $\texttt{s} \in V$. Dann gilt nach Terminierung von `BFS(G, s)` für jeden von `s` aus erreichbaren Knoten `v`. dass $\text{shortest}(\texttt{s}, \texttt{v}) = \texttt{v.dist}$.
Für $\texttt{v} \neq \texttt{s}$ ist ein kürzester Pfad durch einen kürzesten Pfad von `s` nach `v.pred` und der Kante $(\texttt{v.pred}, \texttt{v})$ gegeben.

Intuition für Korrektheit `dist`:
Im ersten Schritt werden genau die Knoten besucht, die von `s` aus über eine Kante erreicht werden können; diese Knoten erhalten `dist=1`
Im zweiten Schritt werden nur die Knoten besucht die in zwei oder mehr Schritten von `s` aus erreichbar sind, diese erhalten `dist=2` usw.

Korrektheit kürzester Pfad:
Für `u=v.pred` ist, da `v` von `u` aus per Kante $(\texttt{u}, \texttt{{v}}) \in E$ besucht wurde, der Pfad von `s` nach `u` und dann zu `v` ein Pfad der Länge
$1+\text{shortest}(\texttt{s}, \texttt{u}) = 1 + \texttt{u.dist} = \text{shortest}(\texttt{s}, \texttt{v})$

## Kürzeste Pfade Ausgeben

Laufzeit (ohne BFS) = $\mathcal{O}(|V|)$

![[aud_folien_06_graphen_algorithmen.pdf#page=29|aud_folien_06_graphen_algorithmen, page 29]]

## Abgeleiteter BFS-Baum

![[aud_folien_06_graphen_algorithmen.pdf#page=30|aud_folien_06_graphen_algorithmen, page 30]]

![[aud_folien_06_graphen_algorithmen.pdf#page=31|aud_folien_06_graphen_algorithmen, page 31]]

$G^s_\text{pred}$ ist der BFS-Baum zu $G$, d.h. er enthält alle von $\texttt{s}$ erreichbaren Knoten in $G$ und für jeden Knoten $\texttt{v} \in V_\text{pred}^s$ existiert genau ein Pfad von $\texttt{s}$ in $G^s_\text{pred}$, der auch ein kürzester Pfad von $\texttt{s}$ zu $\texttt{v}$ in $G$ ist

