---
tags:
  - foliensatz/02/b
  - cleaned
aliases:
  - Laufzeit
  - Laufzeiten
Related:
  - "[[Landau-Symbole]]"
  - "[[Mastertheorem]]"
---

## Laufzeitanalyse

Frage: Wie viel Schritte macht der Algorithmus in Abhängigkeit von der Eingabekomplexität?

Beispielsweise: wenn ich mit [[Insertion Sort]] $n$ Zahlen sortieren möchte, wie viele Schritte macht Insertion Sort abhängig von $n$? 

![[aud_folien_02ab_sorting.pdf#page=25|aud_folien_02ab_sorting, page 25]]

## Komplexitätsklassen

$n$ ist die Länge der Eingabe

![[aud_folien_02ab_sorting.pdf#page=51|aud_folien_02ab_sorting, page 51]]

## Überblick Der Laufzeiten Bei Sorting

| Algorithmus        | Laufzeit                | Worst Case              | Best Case               |
| ------------------ | ----------------------- | ----------------------- | ----------------------- |
| [[Insertion Sort]] | $\mathcal{O}(n^2)$      | $\mathcal{O}(n^2)$      | $\mathcal{O}(n)$        |
| [[Bubble Sort]]    | $\mathcal{O}(n^2)$      | $\mathcal{O}(n^2)$      | $\mathcal{O}(n^2)$      |
| [[Merge Sort]]     | $\Theta(n \log n)$      | $\mathcal{O}(n \log n)$ | $\Omega(n \log n)$      |
| [[Quicksort]]      | $\mathcal{O}(n \log n)$ | $\Theta(n^2)$           | $\mathcal{O}(n \log n)$ |

## Überblick Der Laufzeiten Bei [[Grundlegende Datenstrukturen|Grundlegenden Datenstrukturen]]

| Datenstruktur                           | Operation | Laufzeit Worst Case          |
| --------------------------------------- | --------- | ---------------------------- |
| [[Stacks\|Stack]]                       | Push      | $\Theta(1)$                  |
|                                         | Pop       | $\Theta(1)$                  |
| [[Queues\|Queue]]                       | Enqueue   | $\Theta(1)$                  |
|                                         | Dequeue   | $\Theta(1)$                  |
| [[Verkettete Listen\|Verkettete Liste]] | Einfügen  | $\Theta(1)$                  |
|                                         | Löschen   | $\Theta(1)$ oder $\Omega(n)$ |
|                                         | Suchen    | $\Theta(n)$                  |
