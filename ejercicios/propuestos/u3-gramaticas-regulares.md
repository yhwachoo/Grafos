# Ejercicios propuestos oficiales — Gramáticas Regulares (Unidad 3)

> Transcripción de `Ejercicios_Gramaticas_Regulares.docx`. Estos ejercicios
> entrenan exactamente el puente **autómata ⇄ gramática regular** que la
> Prueba 3 real evalúa integrado (ver `prueba/ensayo-formato-oficial.md`, P1).
> Módulos de apoyo: `01-lenguajes-y-gramaticas.md` y `02-automatas-finitos.md`
> de la U3.

## A. Autómata → Gramática Regular

**A1.** *(diagramas en el original)* Construye las gramáticas regulares que
generan los lenguajes aceptados por los autómatas dados.

**A2.** *(diagrama en el original)* Construye la GR que genera el lenguaje
aceptado por el AFND dado; luego **convierte el AFND a AFD** y repite el
proceso. ¿Las gramáticas generadas son **equivalentes**?

## B. Gramática Regular → Autómata

Construye un autómata que reconozca el lenguaje generado por cada gramática:

**G1** `= ({0,1}, {S,A}, S, P)` · `P = {S → 1A | 0 | λ,  A → 0A | 1A | 1}`

**G2** `= ({0,1}, {S,A,B}, S, P)` · `P = {S → 1A | 0,  A → 1B | 1A | 1,  B → 0A | 1B | 0}`

**G3** `= ({a,b}, {S,A,B}, S, P)` · `P = {S → aA | λ | bS,  A → aB | bA,  B → aS | bB}`

**G4** `= ({a,b,c}, {S,A,B,C}, S, P)` ·
`P = {S → aA | bC,  A → aA | bB | λ,  B → bB | b | λ,  C → cB | cC | λ}`

**G5** `= ({a,b,c}, {S,A,B,C}, S, P)` ·
`P = {S → aA | bC,  A → aA | aS,  B → b,  C → cB | cS}`

**G6** `= ({a,b}, {S,A}, S, P)` · `P = {S → aA | bS,  A → λ}`

**G7** `= ({a}, {S}, S, P)` · `P = {S → λ}`

*(Recuerda la correspondencia: cada no terminal = un estado; `A → aB` =
transición δ(A,a)=B; `A → a` = transición a un estado final; `A → λ` = A es
estado final.)*

## C. Gramática Regular Extendida → Gramática Regular

Para las gramáticas **G3, G4, G5 y G6** del punto anterior, realiza la
transformación de **GRE a GR** y construye el autómata correspondiente a la GR.
*(Algoritmo: módulo `01-lenguajes-y-gramaticas.md`, sección 1.5.)*
