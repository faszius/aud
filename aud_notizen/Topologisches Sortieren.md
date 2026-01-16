---
tags:
  - foliensatz/06
  - cleaned
Related:
  - "[[Depth-First Search (DFS)]]"
---

## Abstrakte Modellierung

Topologische Sortierung gibt es nur für "dag"s (directed acylic graph, also gerichtete azyklische Graphen)

Die topologische Sortierung eines dag $G = (V, E)$ sind Knoten in linearer Ordnung, sodass für alle Knoten $u, v \in V$ gilt, dass $u$ vor $v$ in der Ordnung kommt, wenn $(u, v) \in E$

![[aud_folien_06_graphen_algorithmen.pdf#page=62|aud_folien_06_graphen_algorithmen, page 62]]

Die Sortierung ist nicht eindeutig, zum Beispiel sind hier 2 und 3 vertauschbar

## Topologisches Sortieren Mittels DFS

![[aud_folien_06_graphen_algorithmen.pdf#page=63|aud_folien_06_graphen_algorithmen, page 63]]

Laufzeit $\mathcal{O}(|V| + |E|)$

### Korrektheit

Es genügt zu zeigen, dass jede von DFS inspizierte Kante $(u, v) \in E$ erfüllt: `v.finish < u.finish`, sodass `u` zeitlich nach `v` in Liste eingefügt wird und daher positionell vor `v` in der Liste zu finden ist

![[aud_folien_06_graphen_algorithmen.pdf#page=64|aud_folien_06_graphen_algorithmen, page 64]]

![[aud_folien_06_graphen_algorithmen.pdf#page=65|aud_folien_06_graphen_algorithmen, page 65]]

![[aud_folien_06_graphen_algorithmen.pdf#page=66|aud_folien_06_graphen_algorithmen, page 66]]

