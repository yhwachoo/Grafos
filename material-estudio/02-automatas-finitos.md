# Módulo 2 — Autómatas finitos

> Basado en la clase U3C2 y el apunte *Autómatas Finitos*.

## 2.1 Idea intuitiva

Un **autómata** es un dispositivo lector que decide si una palabra pertenece o no
a un lenguaje; es un modelo primitivo de computador. Tiene una cantidad **finita**
de estados internos que van cambiando a medida que lee, símbolo a símbolo, un
string de entrada. Al terminar la lectura entrega una respuesta lógica:
**aceptada** (✓) o **rechazada** (✗).

Se describe con un **diagrama de estados (DE)**:

- El **estado inicial** se marca con una flecha sin origen.
- Los **estados finales** (de aceptación) se dibujan con **doble círculo**.
- Una transición `δ(eᵢ, a) = eⱼ` se dibuja como un arco de `eᵢ` a `eⱼ` rotulado `a`.

## 2.2 Definición formal

Un **Autómata Finito Determinista (AFD)** es un quíntuple:

```
M = (Q, Σ, δ, q0, F)
```

- **Q:** conjunto finito de estados.
- **Σ:** alfabeto de entrada.
- **δ:** función de transición de estados.
- **q0:** estado inicial, `q0 ∈ Q`.
- **F:** conjunto de estados finales, `F ⊆ Q`.

El apunte usa la notación equivalente `M = ⟨E, A, δ, e0, F⟩`.

### Determinista vs no determinista

| | δ | Interpretación |
|---|---|---|
| **AFD** | `δ: Q × Σ → Q` | Para cada estado y símbolo, **a lo sumo una** transición. |
| **AFND** | `δ: Q × Σ → P(Q)` | Puede haber **0, 1 o varias** transiciones (conjunto de destinos). |
| **AFND-ε** | idem + `δ(q, ε)` | Además permite **saltos espontáneos** sin leer símbolo. |

`P(Q)` es el conjunto potencia (todos los subconjuntos de Q).

## 2.3 Función de transición para cadenas: δ*

`δ` opera sobre *un símbolo*; su extensión `δ*: Q × Σ* → Q` opera sobre *una
cadena* y devuelve el estado alcanzado tras leerla:

```
δ*(q, ε)  = q
δ*(q, xa) = δ(δ*(q, x), a)     con x ∈ Σ*, a ∈ Σ
```

**Lenguaje aceptado:**
```
L(M) = {ω ∈ Σ* / δ*(q0, ω) ∈ F}
```
Los lenguajes aceptados por autómatas finitos se llaman **lenguajes regulares**.

## 2.4 Tabla de transición

Forma tabular de `δ`. Filas = estados (se marca `→` el inicial y `*` los finales),
columnas = símbolos.

**Ejemplo.** `L = {ω = abᵐaⁿ / m par, n > 0}`:

| δ | a | b |
|---|---|---|
| → q0 | q1 | q4 |
| q1 | q3 | q2 |
| q2 | q4 | q1 |
| q3 | q4 | q4 |
| * q4 | q4 | q4 |

`q4` es un **estado colector de basura** (o "trampa"): absorbe toda entrada que ya
no puede formar una palabra válida.

## 2.5 Autómatas básicos (patrones que conviene memorizar)

Con `Σ = {a}` y contando ocurrencias de `a`:

| Autómata | Lenguaje |
|---|---|
| `aⁿ, n ≥ 0` | acepta ε; un lazo `a` en el estado inicial-final |
| `aⁿ, n > 0` | un estado final distinto tras la primera `a` |
| `aⁿ, n par` | 2 estados alternando; final el de índice par |
| `aⁿ, n impar` | 2 estados alternando; final el impar |
| `aⁿ, n múltiplo de k` | ciclo de `k` estados; final `q0` |

**Diseño con condiciones de paridad combinadas** (producto cartesiano). Para
`L = {ω / #a impar y #b par}` se usan 4 estados `(#a mod 2, #b mod 2)`; leer `a`
cambia la paridad de a, leer `b` la de b; final = `(1, 0)`.

## 2.6 Equivalencia AFND → AFD (construcción de subconjuntos)

**Teorema.** Para todo AFND existe un AFD que acepta el mismo lenguaje.

Dado `M_ND = (E_ND, A, δ_ND, e0, F_ND)`, el AFD correspondiente
`M_D = (E_D, A, δ_D, [e0], F_D)` se construye así:

1. **Estados:** subconjuntos de `E_ND`. Cada estado del AFD se escribe
   `[e₁, e₂, …, eᵢ]` (un único estado que "recuerda" un conjunto de estados del AFND).
2. **Inicial:** `[e0]` (con ε-clausura si es AFND-ε).
3. **Transición:**
   ```
   δ_D([e₁,…,eᵢ], a) = [conjunto] = ⋃_{p ∈ {e₁,…,eᵢ}} δ_ND(p, a)
   ```
   (con `δ_G(∅, a) = ∅`).
4. **Finales:** todo estado-conjunto que contenga **al menos un** estado final de `M_ND`.

> Se calcula δ_D **solo** para los estados alcanzables desde el inicial y desde los
> que se puede alcanzar un final.

**Ejemplo (del apunte).** AFND `M4_ND` que acepta
`L₄ = {x ∈ {0,1}* / x contiene 00 ó contiene 11}`.

Aplicando la construcción y luego renombrando `[e0]→q0`, `[e0,e3]→q1`, etc., se
obtiene el AFD:

| δ4D | 0 | 1 |
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

con `q0` inicial y `F = {q3, q4, q5, q6, q7, q8}`.

### AFND-ε: recuerda la ε-clausura

Antes de aplicar la construcción de subconjuntos a un AFND-ε, cada conjunto de
estados debe **cerrarse bajo ε**: incluir todos los estados alcanzables por
transiciones ε (sin leer símbolo). La ε-clausura se aplica tanto al estado inicial
como después de cada transición.

## 2.7 Minimización de AFD

Para cada AFD existe un AFD con **cantidad mínima** de estados que acepta el mismo
lenguaje. Algoritmo:

1. Eliminar estados **no alcanzables** desde `q0`.
2. Eliminar estados desde los que **no se alcanza** un final.
3. Partición inicial `Π₀ = {estados no finales, estados finales}`.
4. `K = 0`.
5. Construir `Π_{K+1}`: dividir cada grupo `G` de `Π_K` en subgrupos tales que dos
   estados `s`, `t` quedan juntos **sii** para **todo** símbolo `a` ambos van al
   mismo grupo de `Π_K`.
6. `K = K + 1`.
7. Si `Π_K ≠ Π_{K-1}`, volver a 5; si no, **terminar**.

Cada grupo de la partición final es un estado del AFD mínimo.

**Ejemplo (del apunte).** Minimizando el `M4D` anterior:
`Π₀ = {q0 q1 q2 | q3 q4 q5 q6 q7 q8}`. Refinando se llega a
`Π = {q0 | q1 | q2 | q3 q4 q5 q6 q7 q8}`, es decir 4 estados:
`p0=q0, p1=q1, p2=q2, p3={q3…q8}`, con `F = {p3}`.

Se concluye: `L(M4ND) = L(M4D) = L(M4Dmin) = L₄`.

## 2.8 Variantes del apunte

### Autómata finito como modelo

Una tripla `M_M = ⟨E, A, δ⟩` (sin `e0` ni `F`), útil solo para **modelar** el
funcionamiento de un proceso (ej.: los estados de un grabador:
OFF, ON, PAUSA, AVANCE, RETROCESO, con acciones play/pausa/stop/rew/ff).

### Autómata finito traductor

Un séptuple `M_T = ⟨E, A, δ, e0, F, S, γ⟩` que, además de reconocer, **produce
salida**:

- **S:** alfabeto de salida.
- **γ: E × A → S\*:** función de traducción; en el diagrama la salida `x` se
  anota sobre el arco como `a / x`.

Extensión a cadenas: `γ*(eᵢ, ε) = ε`, `γ*(eᵢ, ωa) = γ*(eᵢ, ω)·γ(δ*(eᵢ, ω), a)`.
La traducción solo está definida si el autómata **acepta** la cadena:
`T(ω) = γ*(e0, ω) ⟺ δ*(e0, ω) ∈ F`.

Ejemplo típico: máquina expendedora que recibe monedas (input) y entrega
cambio + producto (output).

## Autoevaluación del módulo

1. Diseña un AFD sobre `{a,b}` que acepte palabras que terminan en `ab`.
2. Convierte a AFD el AFND: `δ(q0,a)={q0,q1}`, `δ(q0,b)={q0}`, `δ(q1,b)={q2}`, `F={q2}`.
3. Minimiza un AFD que hayas obtenido y verifica que acepta el mismo lenguaje.
4. Explica con tus palabras la diferencia entre `δ` y `δ*`.
