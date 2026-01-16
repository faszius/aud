---
tags:
  - foliensatz/08
  - cleaned
---

Beim Halteproblem suchen wir ein Programm $H$, sodass  $$H = \begin{cases}1 & \text{ falls $P(P)$ anhält} \\ 0 & \text{ sonst}\end{cases}$$
Also ein Programm $H$, dass genau dann $1$ ausgibt, wenn das Programm $P(P)$ anhält.

Dabei lässt sich schnell erkennen, dass es kein Programm $H$ gibt, dass das Halteproblem löst.

Wir schauen uns dafür das Programm $H^*$ mit $$H^*(P) = \begin{cases}\text{hält an} & \text{falls $H(P) = 0$} \\ \text{hält nicht an} & \text{sonst}\end{cases}$$an, also ein Programm, dass genau dann anhält, wenn das Halteprogramm sagt, dass dessen Eingabe nicht anhält, und genau dann nicht anhält, wenn das Halteprogramm sagt, dass die Eingabe anhält.

Dann erhalten wir folgenden Widerspruch:
$$H(H^*) = 1 \Leftrightarrow_{\text{Definition $H$}} H^*(H^*) \text{ hält an} \Leftrightarrow_\text{Definition $H^*$} H(H^*) = 0$$
