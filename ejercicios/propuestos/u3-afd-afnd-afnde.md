# Ejercicios propuestos oficiales — AFD, AFND y AFND-λ (Unidad 3)

> Transcripción de `Ejericios_AFD_AFND_AFNDe_1.docx`. ⚠️ Los ejercicios 1, 7 y
> 9–11 dependen de diagramas/tablas del documento original (se indican).
> Módulo de apoyo: `material-estudio/unidad-3-automatas/02-automatas-finitos.md`.

**1.** *(diagramas en el original)* Construye los **AFD** de los AFND dados.

**2.** *(tabla en el original)* Considera la función de transición δ para un
AFND: realiza el **diagrama de estados** y **analiza la cadena `01001`**
(análisis de hilos).

**3.** Construye un AFD que reconozca el lenguaje formado por las palabras
`ab`, `aba` y **las concatenaciones entre ellas**.
*Recomendación de la guía: hacer primero el AFND.*

**4.** Construye los AFD de los siguientes lenguajes:
a) `L = {w ∈ {a,b}* | w NO contiene la secuencia aa}`
b) `L = {w ∈ {0,1}* | w tiene tres 0 consecutivos}`

**5.** Construye el AFD que acepte `L = {0ʳ1ˢ2ᵗ | r, s, t ≥ 0}`.

**6.** Construye el AFD que acepte `L = {(abaⁿ)ᵐ | n, m ≥ 0}`.

**7.** *(figuras en el original)* Dados autómatas A1 y A2 que reconocen L1 y
L2, construye los autómatas que reconozcan:
a) `L1·L2` · b) `L2 ∪ L1` · c) `L1 ∪ (L1·L2)`
*(Técnica: conexiones ε entre autómatas — como en la guía resuelta de Turing,
ejercicio 1.)*

**8.** Construye el AFD que reconozca
`L = {w = dᵏ fⁿ gᵐ | k par, n impar, m par}`.
*(Pista: producto de tres condiciones de paridad, con fases estrictas d→f→g.)*

**9.** *(diagrama en el original)* Con el diagrama de estados dado, construye
las transiciones δ y el AFD equivalente; deduce el **lenguaje** que reconoce.

**10.** *(tabla en el original)* Dada la función de transición δ para un
AFND-λ, encuentra el **AFND** y el **AFD** equivalentes (ε-clausura +
subconjuntos).

**11.** Dado el AFND = `({a,b}, {p,q,r,s}, δ, p, {s})` con:

| δ | a | b | λ |
|---|---|---|---|
| → p | q, s | p | p, r |
| q | q, r | r | — |
| r | — | p, s | q |
| * s | s | — | q, r, s |

construye el **diagrama de estados** y los **AFND y AFD equivalentes**.

**12.** En algunos lenguajes de programación los comentarios van entre `/*` y
`*/`. Sea L el lenguaje de todas las cadenas de comentarios delimitados: todo
elemento **empieza por `/*`** y **acaba por `*/`**, sin ningún `*/`
intermedio. Alfabeto `{a, b, /, *}`. Indica el **AFD** que reconoce L.

---

### Material resuelto de referencia (enlaces de la guía original)

- AFD y AFND: <https://core.ac.uk/download/154797605.pdf>
- AFND-λ: <https://core.ac.uk/download/pdf/154797606.pdf>
