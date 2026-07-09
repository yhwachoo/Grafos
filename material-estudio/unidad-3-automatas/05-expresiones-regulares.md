# Módulo 5 — Expresiones regulares

> Basado en la clase U3C4 (*Teoría de Autómatas: expresiones regulares*).

## 4.1 Idea intuitiva

Una **expresión regular** (RegEx, por *regular expression*) es una plantilla,
molde o fórmula que describe un **patrón de texto**: un correo, un RUT, un teléfono,
etc. Es un molde lógico: todo texto que **encaja 100%** en el molde pertenece al
lenguaje; el que no encaja se descarta.

## 4.2 Preliminares (operaciones con lenguajes)

Sobre un alfabeto finito `Σ`, con `L ⊆ Σ*`:

```
L₁ ∪ L₂ = {ω ∈ Σ* / ω ∈ L₁ o ω ∈ L₂}          (unión)
L₁ L₂   = {ω₁ω₂ ∈ Σ* / ω₁ ∈ L₁ y ω₂ ∈ L₂}       (concatenación)
Lⁿ = L·Lⁿ⁻¹ ,   L⁰ = {ε}                         (potencia)
L* = ⋃_{i=0}^∞ Lⁱ    (clausura de Kleene)
L⁺ = ⋃_{i=1}^∞ Lⁱ    (clausura positiva)
```

## 4.3 Definición formal

Una RegEx es un **objeto sintáctico** `r` (minúscula) que define un lenguaje
regular `L(r)`. Reglas de construcción:

**RegEx elementales:**

| RegEx | Lenguaje |
|---|---|
| `a` (con `a ∈ Σ`) | `L(a) = {a}` |
| `ε` | `L(ε) = {ε}` |
| `ϕ` | `L(ϕ) = ϕ` (lenguaje vacío) |

**RegEx compuestas** (con `r`, `s` RegEx):

| RegEx | Lenguaje |
|---|---|
| `rs` | `L(rs) = L(r)·L(s)` |
| `r + s` | `L(r+s) = L(r) ∪ L(s)` |
| `r*` | `L(r*) = L(r)*` |
| `r⁺` | `L(r⁺) = L(r)⁺` |
| `rⁱ` | `L(rⁱ) = L(r)ⁱ` |
| `(r)` | `L((r)) = L(r)` |

> **Recuerda:** `*` itera de 0 a ∞ (puede no aparecer nada), `⁺` itera de 1 a ∞.

## 4.4 Ejemplos resueltos paso a paso

**`(a+b)*` sobre `Σ = {a, b}`:**

```
L((a+b)*) = L(a+b)* = (L(a) ∪ L(b))* = ({a} ∪ {b})* = {a,b}*
          = {ε, a, b, aa, ab, bb, aaa, aab, aba, abb, …}
```
Es decir, **todas** las palabras que se pueden formar con `a` y `b`.

**`a(a+b)*ab` sobre `Σ = {a, b}`:**

```
L(a(a+b)*ab) = L(a)·L((a+b)*)·L(ab)
             = {a}·{a,b}*·{a}{b}
             = {aab, aaab, abab, aaaab, aabab, abbab, …}
```
Por comprensión: palabras que **empiezan con `a`** y **terminan en `ab`**.

## 4.5 Ejercicios de traducción RegEx → lenguaje

Encuentra el lenguaje regular asociado (buen entrenamiento):

```
(a* + b)
(a* b*)
(a* + b*)*
a(a + b*)*
(a + b)* aaa (a + b)*
((a + b)* aaa (a + b)*)⁺
```

## 4.6 Relación entre RegEx y AFND-ε (construcción de Thompson)

Pregunta clave: dada una RegEx, ¿cómo construir un AF que valide su lenguaje?
Se hace de forma **modular** con dos restricciones:

1. El autómata tendrá **un solo estado final**.
2. El estado final **no tiene transiciones de salida**.

**RegEx básicas:**

- `r = a` → dos estados `q0 →(a)→ q1`.
- `r = ε` → `q0 →(ε)→ q1`.
- `r = ϕ` → `q0` y `q1` sin conexión (no se acepta nada).

**Composición** (con autómatas `A_r`, `A_s` ya construidos):

- **Concatenación `rs`:** se **conecta** la salida de `A_r` con la entrada de `A_s`
  mediante una transición ε (no se pueden "pegar", pero sí enlazar con ε).
- **Unión `r + s`:** nuevo inicial `q'0` con ε hacia los iniciales de `A_r` y `A_s`;
  nuevo final `q'f` al que ambos finales llegan con ε.
- **Estrella `r*`:** versión ampliada de `A_r` con nuevos `q'0`/`q'f`, un ε de
  `q'0` a `q'f` (para aceptar `ε`) y un ε que reinyecta el final de `A_r` a su
  inicio (para repetir).

## 4.7 Teorema de Kleene

Las siguientes clases de lenguajes **coinciden**:

```
Lenguajes descritos por RegEx
   = Lenguajes regulares
   = Lenguajes aceptados por AFD / AFND / AFND-ε
   = Lenguajes generados por gramáticas regulares
```

Por eso podemos pasar libremente entre **RegEx ⇄ autómata ⇄ gramática regular**
según convenga al problema.

## Autoevaluación del módulo

1. Describe por comprensión `L((a+b)* aa (a+b)*)`.
2. Construye el AFND-ε (Thompson) para `ab*`.
3. Escribe una RegEx para "palabras sobre `{0,1}` que terminan en `01`".
4. ¿Qué diferencia hay entre `r*` y `r⁺`?
