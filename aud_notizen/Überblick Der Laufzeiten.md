---
tags:
  - MoC
---

## Überblick Der Laufzeiten

### [[Sorting]]

| Algorithmus        | Laufzeit                | Worst Case              | Best Case               |
| ------------------ | ----------------------- | ----------------------- | ----------------------- |
| [[Insertion Sort]] | $\mathcal{O}(n^2)$      | $\mathcal{O}(n^2)$      | $\mathcal{O}(n)$        |
| [[Bubble Sort]]    | $\mathcal{O}(n^2)$      | $\mathcal{O}(n^2)$      | $\mathcal{O}(n^2)$      |
| [[Merge Sort]]     | $\Theta(n \log n)$      | $\mathcal{O}(n \log n)$ | $\Omega(n \log n)$      |
| [[Quicksort]]      | $\mathcal{O}(n \log n)$ | $\Theta(n^2)$           | $\mathcal{O}(n \log n)$ |

### [[Grundlegende Datenstrukturen]]

| Datenstruktur                           | Operation | Laufzeit Worst Case          |
| --------------------------------------- | --------- | ---------------------------- |
| [[Stacks\|Stack]]                       | Push      | $\Theta(1)$                  |
|                                         | Pop       | $\Theta(1)$                  |
| [[Queues\|Queue]]                       | Enqueue   | $\Theta(1)$                  |
|                                         | Dequeue   | $\Theta(1)$                  |
| [[Verkettete Listen\|Verkettete Liste]] | Einfügen  | $\Theta(1)$                  |
|                                         | Löschen   | $\Theta(1)$ oder $\Omega(n)$ |
|                                         | Suchen    | $\Theta(n)$                  |

### [[Binäre Bäume]]

| Operation                                   | Laufzeit                                              |
| ------------------------------------------- | ----------------------------------------------------- |
| Traversieren (Inorder, Preorder, Postorder) | $\mathcal{O}(n)$                                      |
| Suchen                                      | $\Theta(n)$                                           |
| Einfügen                                    | $\Theta(1)$                                           |
| Transplantation                             | $\Theta(1)$                                           |
| Löschen                                     | $\Theta(h)$ <br>(h ist Höhe des Baums, $h=n$ möglich) |

### [[Binäre Suchbäume]]

| Operation | Laufzeit         |
| --------- | ---------------- |
| Suchen    | $\mathcal{O}(h)$ |
| Einfügen  | $\mathcal{O}(h)$ |
| Löschen   | $\Theta(h)$      |

### [[Rot-Schwarz-Bäume]]

| Operation | Laufzeit         |
| --------- | ---------------- |
| Suchen    | $\Theta(\log n)$ |
| Einfügen  | $\Theta(\log n)$ |
| Löschen   | $\Theta(\log n)$ |

### [[AVL-Bäume]]

| Operation | Laufzeit         |
| --------- | ---------------- |
| Suchen    | $\Theta(\log n)$ |
| Einfügen  | $\Theta(\log n)$ |
| Löschen   | $\Theta(\log n)$ |

AVL-Bäume haben bessere (theoretische) Konstanten als Rot-Schwarz-Bäume, je nach Daten und Operationen aber in der Praxis nur unwesentlich schneller

### [[Splay-Bäume]]

| Operation | Laufzeit         |
| --------- | ---------------- |
| Suchen    | $\mathcal{O}(h)$ |
| Einfügen  | $\mathcal{O}(h)$ |
| Löschen   | $\mathcal{O}(h)$ |

Für $m \geq n$ Operationen auf einem Splay-Baum mit maximal $n$ Knoten ist die Worst-Case-Laufzeit $\mathcal{O}(m \cdot \log_2 n)$, also $\mathcal{O}(\log_2 n)$ pro Operation

### [[B-Bäume]]

| Operation | Laufzeit           |
| --------- | ------------------ |
| Einfügen  | $\Theta(\log_t n)$ |
| Löschen   | $\Theta(\log_t n)$ |
| Suchen    | $\Theta(\log_t n)$ |

Achtung: die $\mathcal{O}$-Notation versteckt den (konstanten) Faktor $t$ für die Suche innerhalb eines Knotens;
$t \cdot \log_t n = t \cdot \frac{\log_2 n}{\log_2 t}$ ist in der Regel größer als $\log_2 n$, also in der Regel nur vorteilhaft, wenn Daten blockweise eingelesen werden

### [[Skip Lists]]

| Operation | Laufzeit              |
| --------- | --------------------- |
| Einfügen  | $\Theta(\log_{1/p}n)$ |
| Löschen   | $\Theta(\log_{1/p}n)$ |
| Suchen    | $\Theta(\log_{1/p}n)$ |
$p$ ist die Wahrscheinlichkeit, dass ein Element zu der darüberliegenden Skip-List hinzugefügt wird
$\mathcal{O}$-Notation versteckt (konstanten) Faktor $1/p$
Speicherbedarf im Durchschnitt $= n + pn + p^2n + \ldots = n \cdot \sum_{i\geq0}p^i = \frac{n}{1-p}$

### [[Hash Tables]]

| Operation | Laufzeit (im Durchschnitt)       |
| --------- | -------------------------------- |
| Einfügen  | $\Theta(1)$ (auch im Worst Case) |
| Löschen   | $\Theta(1)$                      |
| Suchen    | $\Theta(1)$                      |

Speicherbedarf in der Regel größer als $n$, üblicherweise ca. $1,33 \cdot n$

### [[Bloom-Filter]]

| Operation | Laufzeit    |
| --------- | ----------- |
| Einfügen  | $\Theta(1)$ |
| Suchen    | $\Theta(1)$ |

### [[Graphen]]

| Eigenschaft                    | Speicherbedarf                           |
| ------------------------------ | ---------------------------------------- |
| Darstellung als Adjazenzmatrix | $\Theta(\vert V \vert^2)$                |
| Darstellung als Adjazenzliste  | $\Theta(\vert V \vert + \vert E \vert )$ |

### [[Graphenalgorithmen]]

| Algorithmus                                                      | Laufzeit                                                                                                                                                                                                                                             |
| ---------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[Breadth-First-Search (BFS)]]                                   | $\mathcal{O}(\vert V \vert + \vert E \vert )$                                                                                                                                                                                                        |
| [[Depth-First Search (DFS)]]                                     | $\mathcal{O}(\vert V \vert + \vert E \vert )$                                                                                                                                                                                                        |
| [[Topologisches Sortieren]]                                      | $\mathcal{O}(\vert V \vert + \vert E \vert )$                                                                                                                                                                                                        |
| [[Starke Zusammenhangskomponenten#Algorithmus\|SCC Algorithmus]] | $\mathcal{O}(\vert V \vert + \vert E \vert )$                                                                                                                                                                                                        |
| [[Algorithmus von Kruskal]]                                      | Mit vielen Optimierungen: $\mathcal{O}(\vert E \vert \cdot \log \vert E \vert)$<br>Sonst: $\mathcal{O}(\vert E \vert \cdot \log \vert V \vert)$                                                                                                      |
| [[Algorithmus von Prim]]                                         | Mit vielen Optimierungen: $\mathcal{O}(\vert E \vert + \vert V \vert \cdot \log \vert V \vert)$                                                                                                                                                      |
| [[Bellman-Ford-Algorithmus]]                                     | $\Theta(\vert E \vert \cdot \vert V \vert)$                                                                                                                                                                                                          |
| [[SSSP-Algorithmus für Dags]]                                    | $\Theta(\vert E \vert + \vert V \vert)$                                                                                                                                                                                                              |
| [[Ford-Fulkerson-Algorithmus]]                                   | $\mathcal{O}(\vert E \vert \cdot u \cdot \vert f^* \vert)$ <br>(wobei $f^*$ der maximale Fluss ist und der Fluss um bis zu $1/u$ pro Iteration wächst)<br>$\mathcal{O}(\vert V \vert \cdot \vert E \vert^2)$<br>(mit Verbesserung nach Edmonds-Karp) |
