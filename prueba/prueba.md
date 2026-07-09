# Prueba Sumativa 3 — Unidad 3: Teoría de Autómatas

**Ramo:** Grafos y Lenguajes Formales · UTEM
**Duración:** 60 minutos · **Puntaje total:** 60 puntos · **Nota 4,0 = 60% (36 pts)**

> **Contenidos evaluados** (según lo informado por el profesor: todo lo visto
> entre la 2ª prueba y el fin del semestre): **AFD, AFND, AFND-ε, Autómatas de
> Pila, Máquinas de Turing (1 cinta) y Máquinas de Turing (multicinta)**.
> Cada una de las 6 preguntas corresponde a uno de estos temas, en el mismo orden.

**Instrucciones**
- Responde con procedimiento completo: tablas, ε-clausuras, particiones y trazas.
  Una respuesta sin desarrollo no recibe puntaje.
- Notación: `M = (Q, Σ, δ, q0, F)` para autómatas finitos;
  `M = (Q, Σ, Γ, δ, q0, Z, F)` para autómatas de pila;
  `M = (Q, Σ, Γ, δ, q0, B, F)` para máquinas de Turing.
- Puedes usar la guía de notación, pero **no** el material de estudio.

---

## Pregunta 1 — AFD (10 pts)

Sea `Σ = {a, b}` y `L = {ω ∈ Σ* / ω contiene la subcadena "aab"}`.

a) **(7 pts)** Diseña un **AFD** que reconozca `L`: quíntupla, tabla de
transición y diagrama de estados.
b) **(3 pts)** Justifica si tu AFD es **mínimo** (sin aplicar el algoritmo
completo, argumenta por qué los estados no podrían fusionarse).

---

## Pregunta 2 — AFND (10 pts)

Sea `Σ = {a, b}` y `L = {ω ∈ Σ* / la tercera letra contada desde el final de ω
es 'a'}` (es decir, `|ω| ≥ 3` y el símbolo en la posición `|ω| − 2` es `a`).

a) **(7 pts)** Diseña **directamente** un **AFND** (δ en conjuntos) que
reconozca `L`, aprovechando el no-determinismo para "adivinar" cuál es la
tercera letra desde el final. Da la quíntupla y el diagrama.
b) **(3 pts)** Traza (análisis de hilos) las palabras `aab` (debe **aceptar**)
y `baa` (debe **rechazar**).

---

## Pregunta 3 — AFND-ε (12 pts)

Sea el siguiente AFND-ε (`q0` inicial, `F = {q1, q2}`):

```
δ(q0, ε) = {q1, q2}
δ(q1, a) = {q1}
δ(q2, b) = {q2}
```

a) **(4 pts)** Calcula la **ε-clausura** de cada estado.
b) **(8 pts)** Construye el **AFD equivalente** por construcción de
subconjuntos (usa las ε-clausuras). Entrega la tabla completa, indica los
estados finales y verifica con las palabras `aaa` (debe **aceptar**) y `ab`
(debe **rechazar**).

---

## Pregunta 4 — Autómata de Pila (10 pts)

Sea `Σ = {a, b}` y `L = {aⁿbᵐ / m ≥ n ≥ 0}` (cero o más `a` seguidas de al
menos tantas `b` como `a` hubo).

a) **(6 pts)** Diseña un **autómata de pila** que reconozca `L`. Entrega la
tabla de transición con `Γ = {X, Z}`.
b) **(2 pts)** Explica el criterio de aceptación.
c) **(2 pts)** Traza las palabras `aabbb` (debe **aceptar**, n=2, m=3) y `aab`
(debe **rechazar**, n=2, m=1).

---

## Pregunta 5 — Máquina de Turing, 1 cinta (10 pts)

Sea `L = {aⁿbⁿcⁿ / n ≥ 1}`.

a) **(6 pts)** Describe (estados y reglas de movimiento) una **MT de 1 cinta**
que reconozca `L`, usando símbolos auxiliares para marcar el progreso.
b) **(2 pts)** Explica por qué un **autómata de pila** (Pregunta 4) no puede
reconocer este lenguaje.
c) **(2 pts)** Describe brevemente qué ocurre al procesar `abc` (debe
**aceptar**) y `aabc` (debe **rechazar**).

---

## Pregunta 6 — Máquina de Turing, multicinta (8 pts)

Sea `f(n, m) = n · m`, calculada en sistema unitario con una **MT de 2 cintas**
(cinta 1: entrada `|ⁿ * |ᵐ`; cinta 2: resultado, inicialmente vacía).

a) **(5 pts)** Describe la estrategia: qué contiene cada cinta en cada momento
y qué ocurre en cada "ronda" del cómputo.
b) **(3 pts)** Explica por qué este diseño es más simple con **dos cintas**
que con una sola (¿qué habría que "recordar" con símbolos auxiliares si solo
hubiera una cinta?).

---

*Fin de la prueba. Revisa tus trazas antes de entregar.*
