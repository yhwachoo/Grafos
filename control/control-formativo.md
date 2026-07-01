# Control Formativo — Teoría de Autómatas

**Ramo:** Grafos y Lenguajes Formales · **Unidad 3** · UTEM
**Carácter:** formativo (sin nota) · **Duración sugerida:** 45 min
**Objetivo:** autoevaluar el dominio de los temas que entran en la **Prueba 3**.

> **Alcance oficial (según lo informado por el profesor):** la Prueba 3 cubre
> **todo lo visto entre la 2ª prueba y el fin del semestre**: **AFD, AFND,
> AFND-ε, Autómatas de Pila, Máquinas de Turing (1 cinta) y Máquinas de Turing
> (multicinta)**. Este control tiene exactamente **un ítem por tema**, en el
> mismo orden, como "ensayo" de la prueba real. Gramáticas y expresiones
> regulares (Módulos 1 y 5) **no** entran.

> Instrucciones: resuelve cada ítem registrando **todo** el procedimiento
> (tablas, ε-clausuras, trazas). Corrige con `pauta-control.md`.

---

## Ítem 1 — AFD

Diseña un **AFD** sobre `Σ = {a, b}` que acepte las palabras que **contienen la
subcadena `bab`**. Entrega quíntupla `(Q, Σ, δ, q0, F)`, tabla de transición y
diagrama de estados.

Luego, **minimiza** el siguiente AFD (`q0` inicial, `F = {q1, q2}`). Muestra las
particiones `Π₀, Π₁, …` hasta estabilizar.

| δ | a | b |
|---|---|---|
| q0 | q1 | q2 |
| q1 | q1 | q3 |
| q2 | q3 | q2 |
| q3 | q3 | q3 |

---

## Ítem 2 — AFND

Para `Σ = {0, 1}`, diseña **directamente** un **AFND** (δ en conjuntos) que
acepte las palabras que **terminan en `00`**. Da la quíntupla y el diagrama.

Luego, **convierte ese mismo AFND a AFD** por construcción de subconjuntos.
Entrega la tabla, marca los finales, y verifica con `100` (debe **aceptar**) y
`1001` (debe **rechazar**).

---

## Ítem 3 — AFND-ε

Dado el siguiente AFND-ε (`q0` inicial, `F = {q2}`):

```
δ(q0, ε) = {q1}    δ(q0, a) = {q0}
δ(q1, b) = {q2}    δ(q2, ε) = {q1}
```

a) Calcula la **ε-clausura** de cada estado.
b) Construye el **AFD equivalente** por construcción de subconjuntos (usando las
ε-clausuras). Entrega la tabla completa e indica los estados finales.

---

## Ítem 4 — Autómata de Pila

Diseña un **autómata de pila** que valide `L = {aⁿbⁿ / n > 0}`. Entrega la tabla
de transición con `Γ = {X, Z}`, explica el criterio de aceptación, y traza la
palabra `aabb`.

---

## Ítem 5 — Máquina de Turing (1 cinta)

Describe (estados y movimientos) una **MT de 1 cinta** que calcule
`f(n, m) = n + m` en sistema unitario. Entrada de ejemplo: `||+|||` (2 + 3).

---

## Ítem 6 — Máquina de Turing (multicinta)

Describe una **MT con 2 cintas** que **decida si `n = m`**: la cinta 1 trae `n`
marcas y la cinta 2 trae `m` marcas (ambas separadas del resto por blancos).
Explica qué hacen los dos cabezales en cada paso y cuál es el criterio de
aceptación.

---

### Autodiagnóstico

| Ítem | Tema | ¿Correcto? |
|---|---|---|
| 1 | AFD (diseño + minimización) | ☐ |
| 2 | AFND (diseño directo + subconjuntos) | ☐ |
| 3 | AFND-ε (ε-clausura + subconjuntos) | ☐ |
| 4 | Autómata de Pila | ☐ |
| 5 | Máquina de Turing (1 cinta) | ☐ |
| 6 | Máquina de Turing (multicinta) | ☐ |

Si fallaste **2 o más ítems**, vuelve al módulo correspondiente
(`material-estudio/02` para AFD/AFND/AFND-ε, `03` para autómatas de pila,
`04` para máquinas de Turing) antes de la prueba sumativa.
