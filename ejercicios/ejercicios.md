# Ejercicios por tipo — Teoría de Autómatas

Ejercicios agrupados por **tipo de habilidad**. Intenta resolverlos sin mirar
`soluciones-ejercicios.md`. Dificultad: 🟢 básico · 🟡 intermedio · 🔴 avanzado.

> **Alcance de la Prueba 3.** Según lo informado por el profesor, la 3ª prueba
> cubre **todo lo visto entre la 2ª prueba y el fin del semestre**: **AFD, AFND,
> AFND-ε, Autómatas de Pila, Máquinas de Turing (1 cinta) y Máquinas de Turing
> (multicinta)** — es decir, los **Tipos C a J** de este documento.
> Los **Tipos A, B e I** (gramáticas, GRE→GR y expresiones regulares — Módulos 1
> y 5) son **material complementario** y **no entran en la Prueba 3**; consérvalos
> solo como cultura general de la unidad.

---

## Tipo A — Lenguajes y gramáticas *(complementario, no evaluado en Prueba 3)*

**A1 🟢** Dado `Σ = {a, b}`, lista 5 palabras de
`L = {ω / ω = aⁿb, n ≥ 0}` y descríbelo en palabras.

**A2 🟢** Escribe una gramática regular (GR) para
`L = {ω ∈ {a,b}* / ω = abⁿa, n ≥ 0}`.

**A3 🟡** Da la gramática (GLC o GR según corresponda) y el árbol de derivación de
`abba` para `L = {ω / ω tiene cantidad par de a's y par de b's}`.

**A4 🟡** Determina el lenguaje generado por
`G = ({a,b}, {S,A}, {S → aS | aA | a, A → bS}, S)`.

---

## Tipo B — Transformación GRE → GR (algoritmo de clase) *(complementario)*

**B1 🟡** Transforma a GR equivalente:
`A → abA | ba | ε`.

**B2 🔴** Encuentra una GR equivalente aplicando el algoritmo visto en clases:

```
G₁ = ({a,b,c}, {S,A,B,C},
      {S → aS | aA | aB | ε,
       A → bB | cC | aS | ε,
       B → aB | bC | cA | ε,
       C → a | b | c | ε}, S)
```

*(¿Cuáles producciones ya son regulares y cuáles hay que descomponer?)*

---

## Tipo C — Diseño de AFD

**C1 🟢** Diseña un AFD sobre `{a, b}` que acepte las palabras que **terminan en
`ab`**. Da quíntupla, tabla y diagrama.

**C2 🟡** Diseña un AFD sobre `{a, b}` que acepte
`L = {ω / #a impar y #b par}` (producto cartesiano de paridades).

**C3 🔴** Sea `Σ = {0, 1}`. Diseña el **AFD mínimo** que acepte las palabras donde
el número de `0`s es **par** Y el número de `1`s es **impar**. Justifica cuántos
estados necesita y qué representa cada uno.

---

## Tipo D — AFD vs AFND (mismo lenguaje, dos enfoques)

**D1 🟡** Diseña un autómata sobre `Σ = {a, b}` que acepte las palabras que
contienen la subcadena **`aa`**, de **dos formas**:
(A) como AFD y (B) como AFND. Para cada uno da la quíntupla, la tabla de transición
y el diagrama. Verifica con la palabra `baa`.

**D2 🔴** Para tu solución de D1(B) (AFND), traza el análisis de hilos de las
palabras `aba` (debe rechazar) y `baab` (debe aceptar).

---

## Tipo E — Conversión AFND / AFND-ε → AFD (subconjuntos)

**E1 🟡** Convierte a AFD el siguiente AFND
(`F = {q2}`):

```
δ(q0, a) = {q0, q1}    δ(q0, b) = {q0}
δ(q1, a) = {q2}        δ(q1, b) = ∅
δ(q2, a) = {q2}        δ(q2, b) = {q2}
```

Entrega la tabla del AFD, indica los estados finales y tacha los inalcanzables.

**E2 🔴** Dado un AFND-ε, explica y aplica cómo se usa la **ε-clausura** en la
construcción de subconjuntos. Usa:

```
δ(q0, ε) = {q1}    δ(q0, a) = {q0}
δ(q1, b) = {q2}    δ(q2, ε) = {q1}
```
con `q0` inicial y `F = {q2}`.

---

## Tipo F — Minimización de AFD

**F1 🔴** Minimiza el AFD (inicial `q0`, `F = {q3,q4,q5,q6,q7,q8}`):

| δ | 0 | 1 |
|---|---|---|
| q0 | q1 | q2 |
| q1 | q3 | q2 |
| q2 | q1 | q4 |
| q3 | q3 | q5 |
| q4 | q6 | q4 |
| q5 | q3 | q7 |
| q6 | q8 | q4 |
| q7 | q8 | q7 |
| q8 | q8 | q7 |

Muestra las particiones `Π₀, Π₁, …` hasta estabilizar.

---

## Tipo G — Autómatas apiladores

**G1 🟡** Diseña la tabla de transición de un a.a. que acepte
`L = {aⁿbⁿ / n > 0}`, con `Γ = {X, Z}`.

**G2 🔴** Diseña un a.a. que valide `L = {aᵐbⁿ / m = n + 1}`.

**G3 🔴** Diseña un a.a. que valide `L = {aᵐbⁿ / m = 2n}`.

---

## Tipo H — Máquinas de Turing (1 cinta)

**H1 🔴** Diseña una MT (1 cinta) que calcule `f(n, m) = n + m` en sistema unitario.
Entrada `3 + 4`: `…BBB|||+||||BBB…`. Describe estados y movimientos.

**H2 🟡** Diseña una MT (1 cinta) que calcule el **predecesor** `f(n) = n − 1`
(para `n > 0`) en sistema unitario. Entrada `||||` (4) → salida `|||` (3).

**H3 🔴** Describe (a nivel de estados y reglas) una MT (1 cinta) **reconocedora**
de `L = {aⁿbⁿcⁿ / n ≥ 1}`. Explica por qué un autómata de pila (Tipo G) **no**
puede reconocer este lenguaje.

---

## Tipo J — Máquinas de Turing (multicinta)

**J1 🔴** Describe la estrategia de una MT **multicinta** (2 cintas) que calcule
`f(n, m) = n · m` en sistema unitario. Entrada `4 * 3`: `…BBB||||*|||BBB…`.
Indica qué contiene cada cinta y qué hace cada "ronda".

**J2 🟡** Describe una MT **multicinta** (2 cintas) que calcule
`f(n, m) = máx(n, m)` en sistema unitario, escribiendo el resultado en una
tercera cinta. ¿Por qué es más simple con varias cintas que con una sola?

---

## Tipo I — Expresiones regulares *(complementario, no evaluado en Prueba 3)*

**I1 🟢** Da 5 palabras y describe por comprensión `L((a + b)* ab)`.

**I2 🟡** Escribe una RegEx para "palabras sobre `{0,1}` que **terminan en `01`**".

**I3 🟡** Traduce a lenguaje (por comprensión) `(a* + b*)*` sobre `{a, b}`.

**I4 🔴** Construye el AFND-ε de Thompson para la RegEx `a(a + b)*`.
