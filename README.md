# Grafos y Lenguajes Formales — Unidad 3: Teoría de Autómatas

Material de estudio, ejercitación y evaluación para la **Unidad 3** del ramo
*Grafos y Lenguajes Formales* (UTEM). El contenido está construido a partir de
las clases U3C1–U3C4, el apunte de Autómatas Finitos y el ejercicio AFD vs AFND.

## Alcance de la Prueba 3

Según lo informado por el profesor, la 3ª prueba cubre **todo lo visto entre la
2ª prueba y el fin del semestre**: **AFD, AFND, AFND-ε, Autómatas de Pila,
Máquinas de Turing (1 cinta) y Máquinas de Turing (multicinta)**. La `prueba/`,
el `control/` y los ejercicios Tipo C–J están alineados exactamente con estos 6
temas. Los Módulos 1 (gramáticas) y 5 (expresiones regulares) del material de
estudio, y los ejercicios Tipo A, B e I, son **complementarios y no entran en
la Prueba 3**, pero se conservan como contenido de la unidad.

## Contenidos de la unidad

1. *(complementario)* Lenguajes formales y gramáticas (alfabetos, palabras,
   lenguajes, gramáticas regulares y regulares extendidas).
2. **AFD, AFND y AFND-ε** — tablas de transición, equivalencia (construcción de
   subconjuntos, ε-clausura) y minimización; autómatas modelo y traductores.
3. **Gramáticas libres de contexto y Autómatas de Pila.**
4. **Máquinas de Turing** — 1 cinta y multicinta.
5. *(complementario)* Expresiones regulares y su relación con los AFND-ε.

## Estructura del repositorio

```
material-estudio/
  00-guia-rapida.md          Resumen ejecutivo y formulario (cheat sheet)
  01-lenguajes-y-gramaticas.md
  02-automatas-finitos.md
  03-glc-y-apiladores.md
  04-maquinas-de-turing.md
  05-expresiones-regulares.md
ejercicios/
  ejercicios.md              Ejercicios por tipo (Tipos C-J = alcance Prueba 3)
  soluciones-ejercicios.md   Soluciones desarrolladas
control/
  control-formativo.md       Control con 6 ítems, uno por tema de la Prueba 3
  pauta-control.md           Pauta de corrección
prueba/
  prueba.md                  Prueba sumativa 3 (60 min, 60 pts, 6 preguntas)
  solucionario.md            Solucionario completo con puntajes
  prueba-imprimible.html     Versión para imprimir y resolver a mano
  prueba-imprimible.pdf      Misma versión, ya en PDF (A4, lista para imprimir)
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
