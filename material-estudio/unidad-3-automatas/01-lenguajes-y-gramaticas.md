# Módulo 1 — Lenguajes formales y gramáticas

> Basado en la clase U3C1 (*Teoría de Autómatas: conceptos básicos y gramáticas*).

## 1.1 Alfabeto, palabra y lenguaje

- **Alfabeto (Σ):** conjunto **finito** de símbolos con los que construimos
  palabras. Ej.: `Σ = {a, b}`.
- **Palabra (ω, por *word*):** combinación finita de símbolos de Σ,
  `ω ∈ Σ*`, a la que asignamos arbitrariamente un significado.
  Ej.: `a`, `ab`, `bab`, `abba`.
- **Lenguaje (L):** conjunto de palabras usadas para comunicar entidades,
  `L ⊆ Σ*`.

Con `Σ = {a, b}` podemos formar `a, ab, b, aaa, bab, bb, abba, …`

Un lenguaje puede definirse:

- **Por extensión** (listando): `L₁ = {a, b, ab, ba, bb, aa}`.
- **Por comprensión** (con una propiedad): `L₂ = {ω ∈ Σ* / ω no contiene a's}`
  o `L₂ = {ω ∈ Σ* / ω = bⁿ, n > 0}`.

### Nociones derivadas

- **Longitud** de una palabra: `|ω|` (cantidad de caracteres).
- **Potencia** de una palabra: `ωⁿ` es concatenar `ω` consigo misma `n` veces.
  Por convención `ω⁰ = ε` (palabra vacía).
- **Propiedad caracterizadora** `p_L(ω)`: predicado que cumplen exactamente las
  palabras del lenguaje. Ej.: `p_{L₁}(ω): 0 < |ω| ≤ 2`.

## 1.2 ¿Qué es una gramática?

Un lenguaje es **formal** si se define por un conjunto finito de reglas. Una
**gramática** es ese conjunto de reglas.

Definición de Chomsky (1956). Una gramática es un cuádruple:

```
G = (Σ, N, P, S)
```

- **Σ:** alfabeto de terminales (letras **minúsculas**).
- **N:** conjunto finito de **no terminales** o metasímbolos (**mayúsculas**);
  permiten *describir* palabras. `Σ ∩ N = ∅`.
- **P:** conjunto finito no vacío de **producciones** de la forma `X → Y`
  (se lee "X deriva/produce Y").
- **S:** símbolo inicial, `S ∈ N`.

Si una palabra contiene solo terminales está **terminada**; si contiene
no terminales es una **metapalabra**.

## 1.3 Derivaciones y árbol de derivación

Aplicando producciones de forma recursiva desde `S` se generan palabras. El
**árbol de derivación** muestra ese proceso.

**Ejemplo (G₁).**

```
G₁ = ({a,b}, {S,A}, {S → aA, A → bA, A → b}, S)
```

Derivación:
```
S → aA → abA → abbA → abbbA → … → abbⁿ
```
Lenguaje generado:
```
L(G₁) = {abⁿ / n > 0} = {ab, abb, abbb, …}
```
"Palabras que comienzan con `a` seguida de solo `b`'s (al menos una)".

**Ejemplo (G₂), lectura del patrón.**

```
G₂ = ({a,b}, {S,A}, {S → aS | aA | a, A → bS}, S)
```

Observaciones:
- La única forma de **terminar** una palabra es `S → a`.
- Toda derivación de `S` agrega una `a`.
- Las derivaciones de `A` agregan una `b` y luego vuelven a `S`.

Conclusión:
```
L(G₂) = {ω ∈ Σ* / ω comienza y termina en a, y no tiene dos b's consecutivas}
```

**Ejemplo (G₃), bombeo desde el centro.**

```
G₃ = ({a,b}, {S,A}, {S → aSa | bSb | aAb | bAa | ε, A → aSb | bSa}, S)
```

Como los no terminales quedan encerrados entre dos símbolos, las palabras son de
**largo par** y se construyen "desde el centro". La producción vacía `S → ε` es la
llave de salida, por lo que `ε ∈ L(G₃)`.
```
L(G₃) = {ω ∈ Σ* / ω tiene cantidad par de a's y par de b's}
```

## 1.4 Gramáticas regulares (GR)

Una gramática es **regular (por la derecha)** si **toda** producción tiene una de
las formas:

```
A → aB      (un terminal seguido de un no terminal)
A → a       (un terminal)
A → ε       (palabra vacía)
```

con `A, B ∈ N` y `a ∈ Σ`. El no terminal, si aparece, va siempre a la derecha del
terminal. Las GR generan exactamente los **lenguajes regulares** (tipo 3).

**No hay un formato único**, pero buscamos que sea regular. Para
`L = {ω = aⁿ, n par} = {ε, aa, aaaa, …}` hay varias soluciones:

```
P₁ = {S → aSa | ε}        (no regular: dos terminales rodean a S)
P₂ = {S → aaS | ε}        (no regular tal cual: aa son dos terminales)
P₄ = {S → aA | ε, A → aS} (REGULAR: cada producción es A → aB o A → ε)
```

`P₄` es la forma regular: introduce el auxiliar `A` para "contar de a dos".

## 1.5 Gramática regular extendida (GRE) y su transformación

Una **GRE** permite producciones `A → wB` o `A → w` con `w` una **palabra**
(varios terminales seguidos), por ejemplo `A → abcB`.

**Algoritmo de transformación GRE → GR.** Para cada producción con más de un
terminal a la izquierda, se introducen no terminales auxiliares que emiten un
terminal a la vez:

```
A → abcB     se reemplaza por     A → aX₁,  X₁ → bX₂,  X₂ → cB
```

Se repite hasta que toda producción quede en la forma `A → aB`, `A → a` o `A → ε`.
El lenguaje generado no cambia; solo se "descompone" cada palabra larga.

> Este algoritmo es exactamente lo que pide la **pregunta 1 del control formativo**:
> "Encuentre una GR equivalente para las GRE dadas, aplicando el algoritmo visto en
> clases".

## 1.6 Relación lenguajes ⇄ gramáticas ⇄ autómatas

- Lenguaje **regular** ⇔ generado por una **GR** ⇔ aceptado por un **AF** ⇔
  descrito por una **RegEx** (Teorema de Kleene).
- Lenguaje **libre de contexto** ⇔ generado por una **GLC** ⇔ aceptado por un
  **autómata apilador**.

De una GR se obtiene directamente un AFND: cada no terminal es un estado, cada
producción `A → aB` es una transición `δ(A, a) = B`, y `A → a` lleva a un estado
final. Este puente se profundiza en el Módulo 2.

## Autoevaluación del módulo

1. Da tres palabras de `L = {ω / ω = aⁿbᵐ, n>0, m≥0}` y descríbelo por comprensión.
2. Escribe una GR para `L = {ω ∈ {a,b}* / ω = abⁿa, n ≥ 0}`.
3. Transforma la GRE `A → abA | ba | ε` a una GR equivalente.
4. ¿Por qué `S → aSa | ε` no es una gramática regular?
