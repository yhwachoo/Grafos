# Grafos y Lenguajes Formales — Unidad 3: Teoría de Autómatas

Material de estudio, ejercitación y evaluación para la **Unidad 3** del ramo
*Grafos y Lenguajes Formales* (UTEM). El contenido está construido a partir de
las clases U3C1–U3C4, el apunte de Autómatas Finitos y el ejercicio AFD vs AFND.

## Contenidos de la unidad

1. Lenguajes formales y gramáticas (alfabetos, palabras, lenguajes, gramáticas
   regulares y regulares extendidas).
2. Autómatas finitos: AFD, AFND y AFND-ε, tablas de transición, equivalencia y
   minimización; autómatas modelo y traductores.
3. Gramáticas libres de contexto, autómatas apiladores y máquinas de Turing.
4. Expresiones regulares y su relación con los AFND-ε.

## Estructura del repositorio

```
material-estudio/
  00-guia-rapida.md          Resumen ejecutivo y formulario (cheat sheet)
  01-lenguajes-y-gramaticas.md
  02-automatas-finitos.md
  03-glc-apiladores-turing.md
  04-expresiones-regulares.md
ejercicios/
  ejercicios.md              Ejercicios por tipo, con pistas
  soluciones-ejercicios.md   Soluciones desarrolladas
control/
  control-formativo.md       Control por tipo de ejercicio (sin nota)
  pauta-control.md           Pauta de corrección
prueba/
  prueba.md                  Prueba sumativa (60 min, 60 pts)
  solucionario.md            Solucionario completo con puntajes
```

## Cómo usar este material

1. Lee la **guía rápida** para tener el mapa completo (jerarquía de Chomsky,
   notación y relaciones clave).
2. Estudia cada módulo del material de estudio.
3. Resuelve los **ejercicios** por tipo antes de mirar las soluciones.
4. Toma el **control formativo** cronometrado para autoevaluarte.
5. Rinde la **prueba** en 60 minutos y corrige con el solucionario.

## Diagramas

Los autómatas se ilustran con **diagramas Mermaid** (se renderizan automáticamente
en GitHub). Convención: los estados finales se dibujan con **doble círculo**
`(((qX)))` y el estado inicial se indica con una flecha desde el nodo `inicio`.

## Notación usada

- `Σ` alfabeto de entrada · `ω` palabra · `ε` palabra vacía · `Σ*` clausura de Kleene.
- Gramática: `G = (Σ, N, P, S)` con `N` no terminales, `P` producciones, `S` símbolo inicial.
- Autómata finito: `M = (Q, Σ, δ, q0, F)`.
- Autómata apilador: `M = (Q, Σ, Γ, δ, q0, Z, F)`.
