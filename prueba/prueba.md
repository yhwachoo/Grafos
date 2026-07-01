# Prueba Sumativa — Unidad 3: Teoría de Autómatas

**Ramo:** Grafos y Lenguajes Formales · UTEM
**Duración:** 60 minutos · **Puntaje total:** 60 puntos · **Nota 4,0 = 60% (36 pts)**

**Instrucciones**
- Responde con procedimiento completo: tablas, particiones y trazas. Una respuesta
  sin desarrollo no recibe puntaje.
- Notación: `M = (Q, Σ, δ, q0, F)` para AF; `M = (Q, Σ, Γ, δ, q0, Z, F)` para a.a.
- Puedes usar la guía de notación, pero **no** el material de estudio.

---

## Pregunta 1 — Lenguajes y gramáticas (8 pts)

a) **(4 pts)** Describe por comprensión el lenguaje generado por:
```
G = ({0,1}, {S,A}, {S → 0S | 1A,  A → 0A | 1A | ε}, S)
```

b) **(4 pts)** Escribe una **gramática regular** para
`L = {ω ∈ {a,b}* / ω termina en b}`.

---

## Pregunta 2 — Transformación GRE → GR (10 pts)

Encuentra una **gramática regular equivalente** aplicando el algoritmo visto en
clases. Indica qué producciones ya eran regulares.

```
G = ({a,b}, {S,A,B}, {S → aaS | bA | ε,  A → abB | b,  B → ba | ε}, S)
```

---

## Pregunta 3 — AFD vs AFND (12 pts)

Sea `Σ = {a, b}`. Para el lenguaje de las palabras que **contienen la subcadena
`ab`**:

a) **(5 pts)** Diseña un **AFD**: quíntupla, tabla de transición y diagrama.
b) **(5 pts)** Diseña un **AFND** (δ en conjuntos) y su diagrama.
c) **(2 pts)** Traza en tu **AFND** las palabras `bab` (debe **aceptar**) y `ba`
   (debe **rechazar**).

---

## Pregunta 4 — Subconjuntos y minimización (14 pts)

a) **(8 pts)** Convierte a **AFD** el siguiente **AFND** por construcción de
subconjuntos. Marca los finales y descarta los inalcanzables.
```
δ(q0,a) = {q0,q1}   δ(q0,b) = {q0}
δ(q1,a) = {q2}      δ(q1,b) = {q2}
δ(q2,a) = ∅         δ(q2,b) = ∅        q0 inicial,  F = {q2}
```

b) **(6 pts)** **Minimiza** el siguiente AFD (`q0` inicial, `F = {q4}`). Muestra
las particiones `Π₀, Π₁, …`.

| δ | 0 | 1 |
|---|---|---|
| q0 | q1 | q2 |
| q1 | q1 | q3 |
| q2 | q2 | q3 |
| q3 | q4 | q4 |
| q4 | q4 | q4 |

---

## Pregunta 5 — Autómata apilador (8 pts)

Diseña un **autómata apilador** que valide `L = {aⁿb²ⁿ / n > 0}` (el doble de `b`
que de `a`). Entrega la tabla de transición con `Γ = {X, Z}`, explica el criterio
de aceptación y traza la palabra `abb`.

---

## Pregunta 6 — Expresiones regulares (4 pts)

a) **(2 pts)** Describe por comprensión `L((0+1)* 00 (0+1)*)`.
b) **(2 pts)** Escribe una RegEx sobre `{a,b}` para "palabras que contienen **al
   menos una `a` y al menos una `b`**".

---

## Pregunta 7 — Máquina de Turing (4 pts)

Describe (estados y movimientos) una **MT** que calcule el **sucesor**
`f(n) = n + 1` en sistema unitario. Entrada `|ⁿ`, salida `|ⁿ⁺¹`.
Ejemplo: `|||` (3) → `||||` (4).

---

*Fin de la prueba. Revisa tus trazas antes de entregar.*
