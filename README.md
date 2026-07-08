# Grafos y Lenguajes Formales (INFB 8061) — Material de estudio

Material de estudio, ejercitación y evaluación para el ramo *Grafos y
Lenguajes Formales* (UTEM), organizado por **unidades**. El contenido está
construido a partir de las clases oficiales (U1, U2 y U3), los apuntes, los
controles formativos y la pauta oficial de la Prueba 3.

## Unidades del ramo

| Unidad | Tema | Clases fuente |
|---|---|---|
| **1** | Ecuaciones de recurrencia (ELRO-1 y ELRO-2) | U1C1, U1C3 |
| **2** | Teoría de grafos (no ponderados y ponderados) | U2C1–U2C4 |
| **3** | Teoría de autómatas y lenguajes formales | U3C1–U3C4 + apunte AF |

## Sobre la Prueba 3 (formato oficial)

El temario informado es **AFD, AFND, AFND-ε, Autómatas de Pila y Máquinas de
Turing (1 cinta y multicinta)**. Sin embargo, la **pauta oficial** de la
Prueba 3 muestra que el formato real es de **4 preguntas grandes e
integradoras** (90 min, 120 pts, se contestan 100, exigencia 60%) donde
**gramáticas y expresiones regulares aparecen integradas** a los autómatas
(extraer la GR y la RegEx de un AFND-ε, construir el AFND-ε de una RegEx,
dar la GLC y el árbol de derivación junto al apilador, MT en notación JFLAP).
Ver `prueba/ensayo-formato-oficial.md`.

## Estructura del repositorio

```
material-estudio/
  unidad-1-recurrencias/
    01-elro-homogeneas.md              ELRO-1 y ELRO-2 homogéneas (Fibonacci, Binet)
    02-recurrencias-desde-algoritmos.md  Recurrencias desde código recursivo y enunciados
  unidad-2-grafos/
    01-conceptos-basicos.md            Definición, tipos, conexo/plano/euleriano/hamiltoniano
    02-valencias-formula-grafica.md    Fv y algoritmo de valencias (Havel-Hakimi)
    03-matriz-adyacencia-caminos.md    MA, potencias MAⁿ, enumeración de caminos
    04-grafos-ponderados.md            Dijkstra, Prim/Kruskal (AEM), Ford-Fulkerson
  unidad-3-automatas/
    00-guia-rapida.md                  Formulario / cheat sheet de la unidad
    01-lenguajes-y-gramaticas.md
    02-automatas-finitos.md            AFD, AFND, AFND-ε, subconjuntos, minimización
    03-glc-y-apiladores.md
    04-maquinas-de-turing.md           1 cinta y multicinta
    05-expresiones-regulares.md
ejercicios/
  ejercicios.md              Ejercicios por tipo (U3), con lectura de diagramas
  soluciones-ejercicios.md   Soluciones desarrolladas
control/
  control-formativo.md           Ensayo por tema (U3, 6 ítems)
  pauta-control.md               Pauta de corrección del anterior
  control-formativo-2-grafos.md  Control formativo oficial de la U2 (con pauta de Fv)
prueba/
  ensayo-formato-oficial.md               Ensayo con el FORMATO REAL de la prueba (4 preguntas, 120 pts)
  solucionario-ensayo-formato-oficial.md  Su solucionario con el desglose de puntaje oficial
  prueba.md                  Ensayo por tema (6 preguntas, 60 pts) — drill adicional
  solucionario.md            Solucionario del anterior
  solucionario.pdf           Mismo solucionario en PDF, con diagramas renderizados
  prueba-imprimible.html     Versión para imprimir y resolver a mano
  prueba-imprimible.pdf      Misma versión, ya en PDF (A4, lista para imprimir)
```

## Cómo usar este material

1. Ubica la **unidad** que vas a estudiar y lee sus módulos en orden.
2. Para la U3, parte por la **guía rápida** (mapa completo y formulario).
3. Resuelve los **ejercicios** por tipo antes de mirar las soluciones.
4. Toma los **controles formativos** cronometrados para autoevaluarte.
5. Rinde primero el **ensayo por tema** (`prueba.md`) y después el **ensayo con
   formato oficial** (`ensayo-formato-oficial.md`, 90 min eligiendo 100 pts).

## Diagramas

Los autómatas y grafos se ilustran con **diagramas Mermaid** (se renderizan
automáticamente en GitHub). Convención: los estados finales se dibujan con
**doble círculo** `(((qX)))` y el estado inicial se indica con una flecha desde
el nodo `inicio`.

## Notación usada

- `Σ` alfabeto de entrada · `ω` palabra · `ε`/`λ` palabra vacía · `Σ*` clausura de Kleene.
- Gramática: `G = (Σ, N, P, S)` con `N` no terminales, `P` producciones, `S` símbolo inicial.
- Autómata finito: `M = (Q, Σ, δ, q0, F)`.
- Autómata apilador: `M = (Q, Σ, Γ, δ, q0, Z, F)`.
- Máquina de Turing: `M = (Q, Σ, Γ, δ, q0, B, F)`.
- Grafo: `G = (V, E)`, orden `n = |V|`, tamaño `m = |E|`.
