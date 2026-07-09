# U2 · Módulo 2 — Valencias y fórmula de valencias

> Basado en la clase U2C2 (*Valencias de un grafo, teorema y algoritmo*).

## 2.1 Valencia y fórmula de valencias

- **Valencia** (o grado) de un vértice: número de **extremos de aristas** que
  coinciden en él.
- **Fórmula de valencias** `Fv`: la lista de las valencias de todos los
  vértices, ej. `Fv = 1:1:2:2:2:4`.

La `Fv` caracteriza parcialmente a un grafo, pero **no** recoge las conexiones
entre aristas (dos grafos distintos pueden compartir la `Fv`; para capturar la
estructura completa se usa la matriz de adyacencia, Módulo 3).

## 2.2 ¿Cuándo una Fv es "gráfica"?

Una secuencia de valencias es **gráfica** si existe un grafo simple (sin
aristas duplicadas ni lazos) que la realice.

**Teorema.** Una secuencia de `n` valencias `Fv = d₁:d₂:…:dₙ` (ordenada
descendentemente) es gráfica **sii**
`Fv' = d₂−1 : d₃−1 : … : d_{k+1}−1 : d_{k+2} : … : dₙ` (con `k = d₁`)
es gráfica.

Es decir: se quita la valencia mayor `d₁` y se **resta 1 a las siguientes `d₁`
valencias**; la secuencia original es gráfica si y solo si la reducida lo es.
(Es el teorema de Havel–Hakimi.)

## 2.3 Algoritmo (derivado del teorema)

```
1. Si existe d en Fv tal que d > n−1  →  parar: NO es gráfica
2. Si Fv = 0:0:…:0                    →  parar: SÍ es gráfica
3. Si hay un número negativo en Fv    →  parar: NO es gráfica
4. Ordenar Fv descendentemente
5. Eliminar la primera valencia d₁ y restar 1 a las siguientes d₁ valencias
6. Ir al paso 2
```

## 2.4 Ejemplo completo (de la clase)

¿Es gráfica `Fv = 2:2:3:4:3` (n = 5)?

```
Ningún dᵢ > 4 ✓ · no todo ceros · sin negativos → ordenar:
Fv = 4:3:3:2:2
   quitar 4, restar 1 a las 4 siguientes:  3−1 : 3−1 : 2−1 : 2−1
Fv = 2:2:1:1
   quitar 2, restar 1 a las 2 siguientes:  2−1 : 1−1 : 1
Fv = 1:0:1  → ordenar → 1:1:0
   quitar 1, restar 1 a la siguiente:      1−1 : 0
Fv = 0:0   →  ¡solo ceros!  →  SÍ es gráfica ✓
```

## 2.5 Casos que fallan (de la tarea de la clase)

**`Fv = 5:4:3:2:1:1`** (n=6):
```
5:4:3:2:1:1 → quitar 5, restar a las 5 → 3:2:1:0:0
3:2:1:0:0   → quitar 3, restar a las 3 → 1:0:−1:0   ← ¡negativo!  NO es gráfica
```

**`Fv = 1:3:5:7`** (n=4): ni siquiera hay que iterar — tiene un vértice de
valencia 7 con solo 4 vértices (máximo posible: n−1 = 3). **NO es gráfica**
(paso 1 del algoritmo).

**`Fv = 2:2:2:2:2:2`** (n=6): es gráfica, ¡y con **más de una** solución! (por
ejemplo, un ciclo de 6 vértices, o dos triángulos separados).

> Moraleja: una Fv gráfica puede corresponder a **varios grafos distintos** —
> otra razón por la que la Fv no caracteriza completamente al grafo.

## 2.6 Caminos entre vértices (introducción)

- **Camino:** secuencia de vértices visitados para ir de `vᵢ` a `vⱼ`.
- **Longitud** del camino: cantidad de **aristas** por las que se transita.

En una red pequeña se pueden enumerar a ojo (ej.: entre los equipos 1 y 5 de
una red: `1-2-3-4-5` (largo 4), `1-2-6-5` (largo 3), etc.), pero en redes
grandes **necesitamos una herramienta más potente que el ojo**: la **matriz de
adyacencia** y sus potencias (Módulo 3).

## Autoevaluación del módulo

1. Aplica el algoritmo a `Fv = 2:3:1:1:3:1`. *(Spoiler de la clase: no es gráfica.)*
2. ¿Por qué el paso 1 (`d > n−1`) descarta inmediatamente una Fv en un grafo simple?
3. Dibuja dos grafos **distintos** con `Fv = 2:2:2:2:2:2`.
4. Define longitud de un camino. ¿La longitud cuenta vértices o aristas?
