# Guía rápida / Formulario — Teoría de Autómatas

Resumen ejecutivo de toda la unidad. Úsalo como mapa mental y como formulario
de repaso antes de una evaluación.

## 1. Conceptos base

| Concepto | Definición | Ejemplo (Σ = {a, b}) |
|---|---|---|
| **Alfabeto (Σ)** | Conjunto finito de símbolos. | {a, b} |
| **Palabra (ω)** | Secuencia finita de símbolos, `ω ∈ Σ*`. | `abba` |
| **Palabra vacía (ε)** | Palabra de longitud 0. | `\|ε\| = 0` |
| **Longitud** | Número de símbolos, `\|ω\|`. | `\|abba\| = 4` |
| **Lenguaje (L)** | Conjunto de palabras, `L ⊆ Σ*`. | `L = {aⁿ / n>0}` |
| **Σ\*** | Todas las palabras (clausura de Kleene). | ε, a, b, aa, ab, … |
| **Σ⁺** | Palabras de largo ≥ 1. | a, b, aa, … |

Operaciones con lenguajes: unión `L₁ ∪ L₂`, concatenación `L₁L₂`,
potencia `Lⁿ = L·Lⁿ⁻¹` con `L⁰ = {ε}`, clausura `L* = ⋃ᵢ₌₀ Lⁱ`, `L⁺ = ⋃ᵢ₌₁ Lⁱ`.

## 2. Jerarquía de Chomsky (de más restrictiva a menos)

| Tipo | Gramática | Máquina que la reconoce | Producciones |
|---|---|---|---|
| 3 | Regular (GR) | Autómata finito (AFD/AFND) | `A → aB`, `A → a`, `A → ε` |
| 2 | Libre de contexto (GLC) | Autómata apilador (pila) | `A → α`, con `α ∈ (N∪Σ)*` |
| 1 | Sensible al contexto | Autómata linealmente acotado | `αAβ → αγβ` |
| 0 | Sin restricción | Máquina de Turing | `α → β` |

**Idea clave:** cada nivel agrega poder de memoria.
AF = sin memoria auxiliar · Apilador = una pila · Turing = cinta infinita.

## 3. Gramáticas

`G = (Σ, N, P, S)` — Σ terminales (minúsculas), N no terminales (mayúsculas),
P producciones, S símbolo inicial.

- **Regular (GR):** cada producción es `A → aB`, `A → a` o `A → ε`
  (a lo sumo un no terminal, siempre a la derecha).
- **Regular extendida (GRE):** admite `A → wB` o `A → w` con `w` una palabra
  (varios terminales seguidos). Se transforma a GR partiendo las palabras largas
  con no terminales auxiliares.
- **Libre de contexto (GLC):** `X → α`, `X ∈ N`, `α ∈ (N∪Σ)*`. Ej.: `S → aSb | ε`
  genera `aⁿbⁿ`, que **no** es regular.

Árbol de derivación: representa cómo, aplicando producciones, se genera una
palabra terminada (solo símbolos de Σ).

## 4. Autómatas finitos

`M = (Q, Σ, δ, q0, F)` — Q estados, δ transición, q0 inicial, F finales.

| | AFD | AFND | AFND-ε |
|---|---|---|---|
| δ | `Q × Σ → Q` (única) | `Q × Σ → P(Q)` (conjunto) | además transiciones con ε |
| Transiciones por símbolo | exactamente / a lo sumo una | 0, 1 o varias | idem + saltos ε |
| Memoria | solo el estado actual | idem | idem |

**Aceptación:** `ω ∈ L(M) ⟺ δ*(q0, ω) ∈ F` (termina en estado final).
Los lenguajes aceptados por AF se llaman **lenguajes regulares**.

**Equivalencia:** para todo AFND (o AFND-ε) existe un AFD que acepta el mismo
lenguaje ⇒ **AFD ≡ AFND ≡ AFND-ε** en poder expresivo.

### Construcción de subconjuntos (AFND → AFD)

1. Estado inicial del AFD: `[q0]` (con ε-clausura si hay AFND-ε).
2. Para cada estado-conjunto y cada símbolo `a`:
   `δD(C, a) = ⋃_{p∈C} δ(p, a)` (unión de destinos).
3. Se repite hasta no generar estados nuevos.
4. Son finales los estados-conjunto que contengan **al menos** un final del AFND.

### Minimización de AFD

1. Eliminar estados inalcanzables desde q0.
2. Eliminar estados desde los que no se alcanza un final.
3. Partición inicial `Π₀ = {no finales, finales}`.
4. Refinar: dos estados quedan juntos si, para **todo** símbolo, van al mismo grupo.
5. Repetir hasta que la partición no cambie. Cada grupo final = un estado mínimo.

## 5. Autómatas apiladores (reconocen GLC)

`M = (Q, Σ, Γ, δ, q0, Z, F)` — Γ alfabeto de pila, Z símbolo inicial de pila.

Transición: `δ(qᵢ, x, Y) = (qⱼ, γ)` — lee `x` del input, `Y` en el tope, pasa a
`qⱼ` y reemplaza el tope por `γ ∈ Γ*` (`push`, `pop` o dejar igual).

Estrategia típica `aⁿbⁿ`: con cada `a` se hace `push(X)`; con cada `b` se hace
`pop()`; se acepta si la pila queda vacía al terminar.

## 6. Máquinas de Turing

Modelo más potente: cinta infinita de lectura/escritura + cabezal que se mueve
(izq/der). Sistema **unitario**: el número `n` se representa con `n` marcas `|`.
Ej.: `3 + 4` en la cinta ⇒ `…BBB|||+||||BBB…`; la MT borra el `+` y junta las
marcas para dejar `n+m`.

## 7. Expresiones regulares (RegEx)

RegEx elementales: `a` con `L(a)={a}`, `ε` con `L(ε)={ε}`, `ϕ` con `L(ϕ)=ϕ`.

Combinaciones (r, s RegEx):

| RegEx | Lenguaje |
|---|---|
| `rs` | `L(r)·L(s)` (concatenación) |
| `r+s` | `L(r) ∪ L(s)` (unión) |
| `r*` | `L(r)*` (0 o más) |
| `r⁺` | `L(r)⁺` (1 o más) |

**Relación con AFND-ε (construcción de Thompson):** toda RegEx se convierte en un
AFND-ε con **un** estado final sin transiciones de salida, combinando autómatas
básicos por concatenación, unión (`+`) y estrella (`*`).

Teorema de Kleene: los lenguajes descritos por RegEx = lenguajes regulares =
lenguajes aceptados por AF = lenguajes generados por GR.

## 8. Errores frecuentes en evaluaciones

- Confundir "a lo sumo una transición" (AFD) con "puede no haber" (AFND).
- Olvidar la **ε-clausura** al pasar de AFND-ε a AFD.
- En minimización, no eliminar estados inalcanzables **antes** de particionar.
- Marcar como final un estado-conjunto que **no** contiene ningún final del AFND.
- Escribir una GR con producciones tipo `A → Ba` (no terminal a la izquierda del
  terminal): eso ya **no** es regular por la derecha.
- Intentar reconocer `aⁿbⁿ` con un AF (imposible: requiere pila).
