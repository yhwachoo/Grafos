# Control Formativo — Teoría de Autómatas

**Ramo:** Grafos y Lenguajes Formales · **Unidad 3** · UTEM
**Carácter:** formativo (sin nota) · **Duración sugerida:** 45 min
**Objetivo:** autoevaluar el dominio de **cada tipo de ejercicio** de la unidad.

> Instrucciones: resuelve cada ítem registrando **todo** el procedimiento
> (tablas, particiones, trazas). Corrige con `pauta-control.md`. Cada ítem apunta a
> un **tipo** distinto: si fallas uno, repasa el módulo indicado.

---

## Ítem 1 — Gramáticas (Módulo 1) · Tipo A

Dada `G = ({a,b}, {S,A}, {S → aS | bA, A → bA | b}, S)`:

a) Deriva dos palabras del lenguaje.
b) Describe `L(G)` por comprensión.

---

## Ítem 2 — Transformación GRE → GR (Módulo 1) · Tipo B

Encuentra una **GR equivalente** aplicando el algoritmo visto en clases. Indica
qué producciones ya eran regulares y cuáles debiste descomponer.

```
G = ({a,b,c}, {S,A}, {S → abS | cA | ε, A → aab | c}, S)
```

---

## Ítem 3 — Diseño de AFD (Módulo 2) · Tipo C

Diseña un **AFD** sobre `Σ = {a, b}` que acepte las palabras que **contienen la
subcadena `ba`**. Entrega quíntupla `(Q, Σ, δ, q0, F)`, tabla de transición y
diagrama de estados.

---

## Ítem 4 — AFD vs AFND (Módulo 2) · Tipo D

Para `Σ = {0, 1}`, resuelve **de dos formas** el reconocimiento de las palabras
que **terminan en `00`**:

a) Como **AFD** (tabla + diagrama).
b) Como **AFND** (δ en conjuntos + diagrama).
c) Traza `1000` en tu AFND (debe **aceptar**) y `1001` (debe **rechazar**).

---

## Ítem 5 — Conversión a AFD (Módulo 2) · Tipo E

Convierte a **AFD** el siguiente **AFND** por construcción de subconjuntos.
Entrega la tabla, marca los finales con `*` y tacha los inalcanzables si los hay.

```
δ(q0,0) = {q0,q1}   δ(q0,1) = {q0}
δ(q1,0) = ∅         δ(q1,1) = {q2}
δ(q2,0) = {q2}      δ(q2,1) = {q2}      q0 inicial,  F = {q2}
```

---

## Ítem 6 — Minimización de AFD (Módulo 2) · Tipo F

Minimiza el AFD (`q0` inicial, `F = {q1, q2}`). Muestra las particiones
`Π₀, Π₁, …` hasta estabilizar.

| δ | a | b |
|---|---|---|
| q0 | q1 | q2 |
| q1 | q1 | q3 |
| q2 | q3 | q2 |
| q3 | q3 | q3 |

---

## Ítem 7 — Autómata apilador (Módulo 3) · Tipo G

Diseña un **autómata apilador** que valide `L = {aⁿbⁿ / n > 0}`. Entrega la tabla
de transición con `Γ = {X, Z}` y explica el criterio de aceptación.

---

## Ítem 8 — Máquina de Turing (Módulo 3) · Tipo H

Describe (estados y movimientos) una **MT** que calcule `f(n, m) = n + m` en
sistema unitario. Entrada de ejemplo: `||+|||` (2 + 3).

---

## Ítem 9 — Expresiones regulares (Módulo 4) · Tipo I

a) Describe por comprensión `L(b(a + b)* a)`.
b) Escribe una RegEx para "palabras sobre `{a,b}` con **al menos dos `a`**".

---

### Autodiagnóstico

| Ítem | Tipo | Módulo | ¿Correcto? |
|---|---|---|---|
| 1 | A — gramáticas | 1 | ☐ |
| 2 | B — GRE→GR | 1 | ☐ |
| 3 | C — diseño AFD | 2 | ☐ |
| 4 | D — AFD vs AFND | 2 | ☐ |
| 5 | E — subconjuntos | 2 | ☐ |
| 6 | F — minimización | 2 | ☐ |
| 7 | G — apilador | 3 | ☐ |
| 8 | H — Turing | 3 | ☐ |
| 9 | I — RegEx | 4 | ☐ |

Si fallaste **2 o más ítems de un mismo módulo**, vuelve a ese módulo antes de la
prueba sumativa.
